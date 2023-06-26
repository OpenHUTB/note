

数据平台在Hbase上数据的操作
业务需求 
1.       通过row_key可以对完整Json文件和img文件夹进行下载（90%的情况）
2.       通过row_key和版本号对该版本的Json数据和对应的图片进行下载（10%的情况）
3.       Json数据的插入，插入到指定行的Json列簇下面，并标记版本号。
4.       海量文件的上传，Json文件和img文件夹中的图片的上传。
算法策略与代码
海量文件上传（包括json文件和img文件夹）
算法思想：将数据上传至Hbase的表中，由于表的结构为一张img对应着一条json数据，为了将时间复杂度降低至O（n），我们先对json文件中的数据进行排序与每一张img对应，在读取的时候可以直接根据json数据定位到对应的img。在这了我们采用的排序算法是快速排序，调用的Hbase API为Put。
代码如下：（json文件的排序）
 
package operation;
 
import java.io.BufferedReader;
import java.io.FileReader;
import java.io.IOException;
import java.util.ArrayList;
import org.json.JSONObject;
 
 
public class Json_sort {
 
 public static String img_id = null; 
 public static JSONObject data_json = null;
 public static String path = null;
 public static String num_index;
 
 public Json_sort(String path){
  Json_sort.path = path;
 }
 
 
 /**
  * @param args
  * @throws IOException 
  */
 public ArrayList<String> get_sort_json() throws IOException {
  // TODO Auto-generated method stub
  ArrayList<String> json_arr = new ArrayList<String>();
  BufferedReader br = new BufferedReader(new FileReader(path));
  String s = null;
  int count = 0;
  while((s = br.readLine()) != null){
   json_arr.add(s);
   count++;
  }
  quickSort(json_arr,0,count-1);
  return json_arr;
 
 
 }
 
 private static void quickSort(ArrayList<String> json_arr, int low, int high) {
  // TODO Auto-generated method stub
  if(low>=high){
   return;
  }
  int index = partition(json_arr,low,high);
  quickSort(json_arr,low,index-1);
  quickSort(json_arr,index+1,high);
 }
 
 
 public static int partition(ArrayList<String> json_arr, int low, int high){
  JSONObject data = new JSONObject(json_arr.get(low));
  String data_index = json_arr.get(low);
  String img = data.getString("image_key");
  String[] arr = img.split("\\.");
  String num = arr[0];
  while(low < high){
   data_json = new JSONObject(json_arr.get(high));
   img_id = data_json.getString("image_key");
   String[] arr1 = img_id.split("\\.");
   num_index = arr1[0];
   while(num_index.compareTo(num)>=0 && high > low){
    high--;
    data_json = new JSONObject(json_arr.get(high));
    img_id = data_json.getString("image_key");
    String[] arr2 = img_id.split("\\.");
    num_index = arr2[0];
   }
   json_arr.set(low, json_arr.get(high));
   data_json = new JSONObject(json_arr.get(low));
   img_id = data_json.getString("image_key");
   String[] arr2 = img_id.split("\\.");
   num_index = arr2[0];
   while(num_index.compareTo(num)<0 && high > low){
    low++;
    data_json = new JSONObject(json_arr.get(low));
    img_id = data_json.getString("image_key");
    String[] arr3 = img_id.split("\\.");
    num_index = arr3[0];
   }
   json_arr.set(high, json_arr.get(low));
  }
  json_arr.set(high,data_index);
  return high; 
 }
}
 
img文件的排序：
 
package operation;
 
 
public class Img_sort {
 
 public static String s_index = null;
 public static String num_index;
 
 public void img_sort(String[] file){
  int len = file.length;
  quickSort(file, 0, len-1);
 }
 
 
 private static void quickSort(String[] file, int low, int high) {
  // TODO Auto-generated method stub
  if(low>=high){
   return;
  }
  int index = partition(file,low,high);
  quickSort(file,low,index-1);
  quickSort(file,index+1,high);
 }
 
 
 public static int partition(String[] file, int low, int high){
  String s = file[low];
  String[] arr = s.split("\\.");
  String num = arr[0];
  while(low < high){
      s_index = file[high];
   String[] arr1 = s_index.split("\\.");
      num_index = arr1[0];
   while(num_index.compareTo(num)>=0 && high > low){
    high--;
    s_index = file[high];
    String[] arr2 = s_index.split("\\.");
       num_index = arr2[0];
   }
   file[low] = file[high];
   s_index = file[low];
   String[] arr2 = s_index.split("\\.");
   String num_index = arr2[0];
   while(num_index.compareTo(num)< 0 && high > low){
    low++;
    s_index = file[low];
    String[] arr3 = s_index.split("\\.");
       num_index = arr3[0];
   }
   file[high] = file[low];
  }
  file[high] = s;
  return high; 
 }
}
 
海量数据上传：
 
package operation;
 
 
import java.io.File;
import java.io.FileInputStream;
import java.io.IOException;
import java.io.InputStream;
import java.util.ArrayList;
 
 
import org.apache.hadoop.hbase.TableName;
import org.apache.hadoop.hbase.client.Put;
import org.apache.hadoop.hbase.client.Table;
import org.apache.hadoop.hbase.util.Bytes;
 
 
public class Put_rows {
 
 
 /**
  * @param args
  * @throws IOException 
  */
 public static void main(String[] args) throws IOException{
  // TODO Auto-generated method stub
  int len = args.length;
  if(len != 5)
   print();
  else
   put_rows(args[0],args[1],args[2],args[3],args[4]);
        
 }
 
 
 public static void put_rows(String table, String json_path, String img_path, String row, String version) throws IOException{
  Init in = new Init();
  in.init();
  Table t = in.connection.getTable(TableName.valueOf(table));
  Json_sort json_file = new Json_sort(json_path);
  ArrayList<String> json_data = json_file.get_sort_json();
  File file = new File(img_path);
  String[] filelist = file.list();
  Img_sort file_sort = new Img_sort();
  file_sort.img_sort(filelist);
  int i = 0;
  int j = 0;
  while(j < json_data.size() && i < filelist.length){
   System.out.println(json_data.get(j));
   System.out.println(filelist[i]);
   File picture = new File(img_path+"/"+filelist[i]);
   String[] arr = filelist[i].split("\\.");
   String row_img = arr[0];
   String row_key = row + "+" + row_img;
   System.out.println(row_key);
   int num = (int) picture.length();
   byte[] img = new byte[num];
   InputStream a = null;
   a = new FileInputStream(picture);
   a.read(img);
   Put put = new Put(Bytes.toBytes(row_key));
   put.addColumn(Bytes.toBytes("info"), Bytes.toBytes(version), Bytes.toBytes(json_data.get(j)));
   put.addColumn(Bytes.toBytes("img"), null, img);
   t.put(put);
   i++;
   j++;
   System.out.println("done put rows");
  }
  System.out.println("number count:"+i);
  t.close();
 }
 
 private static void print() {
  // TODO Auto-generated method stub
  System.out.println("--------------------------------------");
  System.out.println("Some of the necessary parameters:");
  System.out.println("table(*):the table name that you operate");
  System.out.println("json_path(*):the path of json file ");
  System.out.println("img_path(*):the path of image file");
  System.out.println("row(*):the row_key of a row");
  System.out.println("version(*):the version of json data");
  System.out.println("--------------------------------------");
 }
 
 
}


RegionServer
http://hdfsvm005.hogpu.cc:16030

HBase Master
hdfsvm001.hogpu.cc:16010

Hbase调用JavaAPI实现批量导入操作
http://787141854-qq-com.iteye.com/blog/2067818

HBase Java客户端编程 http://www.cnblogs.com/panfeng412/archive/2011/08/14/2137984.html

/etc/hbase/conf/hbase-site.xml 

hostname -i
10.10.10.184


