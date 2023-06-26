


部署：

缓冲区，日志格式
PHP线上参数

https://ftp.pcre.org/pub/pcre/
--with-  指的是源代码目录
./configure --prefix=/home/haidong.wang/software/nginx --with-pcre=/home/haidong.wang/install/pcre-8.35 --with-zlib=/home/haidong.wang/install/zlib-1.2.8
configure: error: You need a C++ compiler for C++ support.
yum install -y gcc gcc-c++







+远程SSH登录
多线程

接口
写入状态信息文件（upload.list，或者download.list）：
每一行第一个字符串：0成功，1失败
一行的后续内容：文件链接，或错误信息
1. 上传文件夹下所有文件（或单个文件），返回HDFS路径
hadoop jar ./HDFS.jar 1 /home/haidong.wang/data/data_tmp
返回：hdfs://10.10.10.34:8020/user/wanghaidong/AP2/bc7c2f64-342e-491b-8567-60dcaccbd0b5.seq
上传单个文件
hadoop jar ./HDFS.jar 1 /home/haidong.wang/data/data_tmp/53ac2be3debeb950084f79b3fe7a5905.jpg
11. 上传文件（不存在就新建），返回状态信息：0成功，1失败
hadoop jar ./HDFS.jar 11 /home/haidong.wang/data/data_1038_hand_v2/data_000001.json 
得到：hdfs://10.10.10.34:8020/user/wanghaidong/AP2/8af465af-7855-4331-99db-aa8cbaa5582b
12. 追加文件，返回状态信息：0成功，1失败
hadoop jar ./HDFS.jar 12 /home/haidong.wang/data/data_1038_hand_v2/data_000001.json hdfs://10.10.10.34:8020/user/wanghaidong/AP2/8af465af-7855-4331-99db-aa8cbaa5582b
13. 上传整个文件夹到HDFS，压缩成MapFile格式
hadoop jar ./HDFS.jar 13 /home/haidong.wang/data/data_tmp
返回：hdfs://10.10.10.34:8020/user/wanghaidong/AP2/e5097f33-b4b8-45bd-a9f4-a1f4c80d9952.map    
上传单个文件，压缩成MapFile格式
hadoop jar ./HDFS.jar 13 /home/haidong.wang/data/data_tmp/53ac2be3debeb950084f79b3fe7a5905.jpg
返回：hdfs://10.10.10.34:8020/user/wanghaidong/AP2/53ac2be3debeb950084f79b3fe7a5905.jpg.map

2. 下载指定路径下的文件，返回HTTP文件目录（/home/haidong.wang/download/（文件时间超过2天就进行清理），下载完成打印出HTTP文件链接）
hadoop jar ./HDFS.jar 2 hdfs://10.10.10.34:8020/user/wanghaidong/AP2/efb57648-9bf4-4567-bfcc-da9186b587d0.seq 
hadoop jar ./HDFS.jar 2 hdfs://10.10.10.34:8020/user/wanghaidong/AP2/53ac2be3debeb950084f79b3fe7a5905.jpg.seq
21. 下载单个文件（下载到download目录下，返回HTTP文件夹的链接，文件夹置于文件夹之内）
hadoop jar ./HDFS.jar 21 hdfs://10.10.10.34:8020/user/wanghaidong/AP2/bc7c2f64-342e-491b-8567-60dcaccbd0b5.seq
返回：http://10.10.10.184:8080/download/7413c1aa-6bdb-437f-9f21-c5ed7c473ef3/
下载整个mapfile文件夹（不进行解压），返回的HTTP文件夹的链接
hadoop jar ./HDFS.jar 21 hdfs://10.10.10.34:8020/user/wanghaidong/AP2/e5097f33-b4b8-45bd-a9f4-a1f4c80d9952.map
返回：http://10.10.10.184:8080/download/f2eab020-e5e6-4254-9058-78f2a052174c/
22. 下载MapFile，解压成文件夹
hadoop jar ./HDFS.jar 22 hdfs://10.10.10.34:8020/user/wanghaidong/AP2/e5097f33-b4b8-45bd-a9f4-a1f4c80d9952.map
返回：http://10.10.10.184:8080/download/a402bf83-55fc-4d67-bb83-c135773c636d/
解压成单个文件
hadoop jar ./HDFS.jar 22 hdfs://10.10.10.34:8020/user/wanghaidong/AP2/53ac2be3debeb950084f79b3fe7a5905.jpg.map
返回：http://10.10.10.184:8080/download/5c346622-1140-418c-b1c4-8c47afee88ac/
23. 并发下载文件夹列表里的文件
hadoop jar ./HDFS.jar 23 3 hdfs://10.10.10.34:8020/user/wanghaidong/AP2/e5097f33-b4b8-45bd-a9f4-a1f4c80d9952.map hdfs://10.10.10.34:8020/user/wanghaidong/AP2/1565068d-5e72-43f6-8c58-d1fca272b5f5.map hdfs://10.10.10.34:8020/user/wanghaidong/AP2/eef9a95b-fc5e-4723-b2b7-91ee753a775c.map

3. 删除指定HDFS路径下的文件，返回状态信息：0成功，1失败
hadoop jar ./HDFS.jar 3 hdfs://10.10.10.34:8020/user/wanghaidong/AP2/9319f828-a936-4147-8c65-850f73020665.seq

4. 下载指定文件名的文件
hadoop jar ./HDFS.jar 4 1 hdfs://10.10.10.34:8020/user/wanghaidong/AP2/d55fa0b4-51e7-416e-9302-5fc60aafb450 2 53ac2be3debeb950084f79b3fe7a5905.jpg fffca4c3f11c380072409b19b2f01e81.jpg

hdfs://10.10.10.34:8020/user/wanghaidong/AP2/5d5fd378-d1a3-47d5-82db-cc0f82897d00.map



客户端解压：
hadoop jar ./HDFS.jar 21 hdfs://10.10.10.34:8020/user/wanghaidong/AP2/e5097f33-b4b8-45bd-a9f4-a1f4c80d9952.map
http://10.10.10.184:8080/download/6d1bd59b-20c7-48bb-85ec-172fd5886baf/
ll ./download/6d1bd59b-20c7-48bb-85ec-172fd5886baf/
解压MapFile（参数为一个文件夹，里面包含data文件和index文件）
hadoop jar ./client.jar ./download/6d1bd59b-20c7-48bb-85ec-172fd5886baf/
解压SequenceFile（参数为一个文件）
hadoop jar ./client.jar ./download/73af9aed-cf7d-40f9-a524-6013d6302223/bc7c2f64-342e-491b-8567-60dcaccbd0b5.seq


性能测试
hadoop fs -ls hdfs://10.10.10.34:8020/user/wanghaidong/AP2/
数据准备（/home/haidong.wang/uploadData.sh）：
上传50个文件夹（1.9G，2w个文件）

**********************************************
time hadoop jar ./HDFS.jar 13 /home/haidong.wang/data/data_000001
返回：hdfs://10.10.10.34:8020/user/wanghaidong/AP2/ae057ca0-e0ed-42ad-8c63-33d51dcdf699.map
时间：2m6.023s

************************************************
time hadoop jar ./HDFS.jar 23 1 hdfs://10.10.10.34:8020/user/wanghaidong/AP2/ae057ca0-e0ed-42ad-8c63-33d51dcdf699.map
返回：http://10.10.10.184:8080/download/a1a70cf1-93ea-4360-9754-faeb92da23df/
时间：0m26.655s（7.22倍）
*************************************************
time hadoop jar ./HDFS.jar 23 3 hdfs://10.10.10.34:8020/user/wanghaidong/AP2/ae057ca0-e0ed-42ad-8c63-33d51dcdf699.map hdfs://10.10.10.34:8020/user/wanghaidong/AP2/3ce349d8-66ce-4c00-bfbe-c7c10d2519ce.map hdfs://10.10.10.34:8020/user/wanghaidong/AP2/93ababbd-1cce-4dc2-a4a6-e058640b44f5.map

返回：
http://10.10.10.184:8080/download/08f45c5b-f6ad-4e7a-aa89-27be61570651/
http://10.10.10.184:8080/download/a03d65e5-eec5-45e3-be0d-4650e1b96223/
http://10.10.10.184:8080/download/1c114712-386a-4bfd-9e94-fd183b53a4ef/
时间：0m50.520s（4.67倍）

******************************2w*5=10w（5线程）
time hadoop jar ./HDFS.jar 23 5 hdfs://10.10.10.34:8020/user/wanghaidong/AP2/ae057ca0-e0ed-42ad-8c63-33d51dcdf699.map hdfs://10.10.10.34:8020/user/wanghaidong/AP2/3ce349d8-66ce-4c00-bfbe-c7c10d2519ce.map hdfs://10.10.10.34:8020/user/wanghaidong/AP2/93ababbd-1cce-4dc2-a4a6-e058640b44f5.map hdfs://10.10.10.34:8020/user/wanghaidong/AP2/25fb808c-5ebf-4bac-9c00-86b310fb36c2.map hdfs://10.10.10.34:8020/user/wanghaidong/AP2/7454727d-ae3a-4252-ba56-fbb45d79da2c.map
返回：
http://10.10.10.184:8080/download/49dab42c-efff-4724-8305-a95045a566b2/
http://10.10.10.184:8080/download/7332c69f-1087-4501-b36e-3f0051ea672b/
http://10.10.10.184:8080/download/e4e55003-5589-4be8-ab4c-007f39bdc897/
http://10.10.10.184:8080/download/618aad63-3bdd-4a25-bdaf-2a84952e6820/
http://10.10.10.184:8080/download/4f9292f3-2e5e-42b8-a5c5-7a5762a066c9/
时间：1m21.744（2.25倍）

******************************2w*10=20w（10线程）
time hadoop jar ./HDFS.jar 23 10 hdfs://10.10.10.34:8020/user/wanghaidong/AP2/ae057ca0-e0ed-42ad-8c63-33d51dcdf699.map hdfs://10.10.10.34:8020/user/wanghaidong/AP2/3ce349d8-66ce-4c00-bfbe-c7c10d2519ce.map hdfs://10.10.10.34:8020/user/wanghaidong/AP2/93ababbd-1cce-4dc2-a4a6-e058640b44f5.map hdfs://10.10.10.34:8020/user/wanghaidong/AP2/25fb808c-5ebf-4bac-9c00-86b310fb36c2.map hdfs://10.10.10.34:8020/user/wanghaidong/AP2/7454727d-ae3a-4252-ba56-fbb45d79da2c.map hdfs://10.10.10.34:8020/user/wanghaidong/AP2/8f667baa-fd25-4160-963e-bc32ae23211f.map hdfs://10.10.10.34:8020/user/wanghaidong/AP2/8096de4c-1389-4130-886c-8f7b240831c6.map hdfs://10.10.10.34:8020/user/wanghaidong/AP2/fa4851d7-d712-4c1c-bd57-78dbd49f911a.map hdfs://10.10.10.34:8020/user/wanghaidong/AP2/54cf6670-713c-4b09-a2b2-73fc85748c9d.map hdfs://10.10.10.34:8020/user/wanghaidong/AP2/5d99fc69-53ca-49ca-8e5e-f5acee199fb7.map
返回：
http://10.10.10.184:8080/download/b29f306e-f7b7-44fd-ac50-7c85504c1444/
http://10.10.10.184:8080/download/ca1af2dd-60d2-4d93-b364-eea961ee9ea7/
http://10.10.10.184:8080/download/096b6b46-8420-4c0d-85ad-ef045df05b0a/
http://10.10.10.184:8080/download/9565705d-420b-422e-b70b-29d36f612857/
http://10.10.10.184:8080/download/e8fe5ceb-34bb-4573-ae63-b9d6bb3aec31/
http://10.10.10.184:8080/download/d6c9b246-ef86-4c47-a5a7-54bf1d7e286c/
http://10.10.10.184:8080/download/74a934f9-7844-492d-8584-cbccc4170ee0/
http://10.10.10.184:8080/download/c2c5a276-7d8b-4833-ad98-5340f53f596e/
http://10.10.10.184:8080/download/9be430bf-c9b2-4e84-b662-f8ce7125130d/
http://10.10.10.184:8080/download/2f58501c-d995-4eac-85c6-860896f95109/
时间：2m51.905s（2.375倍）

******************************2w*20=40w（20线程）
time hadoop jar ./HDFS.jar 23 20 hdfs://10.10.10.34:8020/user/wanghaidong/AP2/ae057ca0-e0ed-42ad-8c63-33d51dcdf699.map hdfs://10.10.10.34:8020/user/wanghaidong/AP2/3ce349d8-66ce-4c00-bfbe-c7c10d2519ce.map hdfs://10.10.10.34:8020/user/wanghaidong/AP2/93ababbd-1cce-4dc2-a4a6-e058640b44f5.map hdfs://10.10.10.34:8020/user/wanghaidong/AP2/25fb808c-5ebf-4bac-9c00-86b310fb36c2.map hdfs://10.10.10.34:8020/user/wanghaidong/AP2/7454727d-ae3a-4252-ba56-fbb45d79da2c.map hdfs://10.10.10.34:8020/user/wanghaidong/AP2/8f667baa-fd25-4160-963e-bc32ae23211f.map hdfs://10.10.10.34:8020/user/wanghaidong/AP2/8096de4c-1389-4130-886c-8f7b240831c6.map hdfs://10.10.10.34:8020/user/wanghaidong/AP2/fa4851d7-d712-4c1c-bd57-78dbd49f911a.map hdfs://10.10.10.34:8020/user/wanghaidong/AP2/54cf6670-713c-4b09-a2b2-73fc85748c9d.map hdfs://10.10.10.34:8020/user/wanghaidong/AP2/5d99fc69-53ca-49ca-8e5e-f5acee199fb7.map hdfs://10.10.10.34:8020/user/wanghaidong/AP2/ae057ca0-e0ed-42ad-8c63-33d51dcdf699.map hdfs://10.10.10.34:8020/user/wanghaidong/AP2/3ce349d8-66ce-4c00-bfbe-c7c10d2519ce.map hdfs://10.10.10.34:8020/user/wanghaidong/AP2/93ababbd-1cce-4dc2-a4a6-e058640b44f5.map hdfs://10.10.10.34:8020/user/wanghaidong/AP2/25fb808c-5ebf-4bac-9c00-86b310fb36c2.map hdfs://10.10.10.34:8020/user/wanghaidong/AP2/7454727d-ae3a-4252-ba56-fbb45d79da2c.map hdfs://10.10.10.34:8020/user/wanghaidong/AP2/8f667baa-fd25-4160-963e-bc32ae23211f.map hdfs://10.10.10.34:8020/user/wanghaidong/AP2/8096de4c-1389-4130-886c-8f7b240831c6.map hdfs://10.10.10.34:8020/user/wanghaidong/AP2/fa4851d7-d712-4c1c-bd57-78dbd49f911a.map hdfs://10.10.10.34:8020/user/wanghaidong/AP2/54cf6670-713c-4b09-a2b2-73fc85748c9d.map hdfs://10.10.10.34:8020/user/wanghaidong/AP2/5d99fc69-53ca-49ca-8e5e-f5acee199fb7.map
返回：
时间：5m47.699s（2.40倍）

客户端解压
time hadoop jar ./client.jar ./download/0e079a54-773b-46fc-8366-7623938616ef.seq
real    0m0.800s 

搭建tomcat文件服务器
部署在：fastdb@10.19.19.23:/home/fastdb/ap2/hdfs上
（http://blog.csdn.net/yu452148611/article/details/46324891）
http://10.10.10.184:8080/
端口改为：12346
apache-tomcat-9.0对应的JAVA必须为JAVA8
打开tomcat conf 目录下的server.xml，在最底下找到</Host>
vi /home/haidong.wang/install/apache-tomcat-9.0.0.M21/conf/web.xml，在该行上面添加<Context docBase="/home/fastdb/ap2/hdfs/download" path="/download" reloadable="true"/>
修改tomcat conf目录下的web.xml文件，找listings：
    <servlet>
        <servlet-name>default</servlet-name>
        <servlet-class>org.apache.catalina.servlets.DefaultServlet</servlet-class>
        <init-param>
            <param-name>debug</param-name>
            <param-value>0</param-value>
        </init-param>
        <init-param>
            <param-name>listings</param-name>
            <param-value>true</param-value>
        </init-param>
        <load-on-startup>1</load-on-startup>
    </servlet>
http://10.10.10.184:8080/download/
http://10.10.10.184:8080/download/1d955f16-b89a-4077-8e5a-99ea1f205ae4/

定时清理下载缓冲
find /home/haidong.wang/download/ -mtime +1 -name "*.seq" -exec rm -rf {} \;
vi /home/haidong.wang/auto-del-1-days-ago-download.sh
chmod +x /home/haidong.wang/auto-del-1-days-ago-download.sh
crontab -e
10 0 * * * /home/haidong.wang/auto-del-1-days-ago-download.sh >/dev/null 2>&1
crontab -l
crontab -r
 

MR
https://www.codeproject.com/Articles/887028/Implementing-Joins-in-Hadoop-Map-Reduce-using-MapF
 

是否可以远程提交任务(http://www.huqiwen.com/2013/07/18/hdfs-permission-denied/)
export HADOOP_USER_NAME=wanghaidong
hadoop jar ./Test.jar 1 /home/wanghaidong/hdfs/server/data_tmp/  hdfs://yz-gpu034.hogpu.cc:8020/user/test/local2hdfs.seq
hadoop fs -ls hdfs://yz-gpu034.hogpu.cc:8020/user/test/local2hdfs.seq
8020是hadoop的namenode的RPC调用端口（core-site.xml）

按照接口修改之前
hadoop jar ./Test.jar 1 /home/haidong.wang/data/data_tmp /user/data/test1/local2hdfs.seq
hadoop jar ./Test.jar 2 /user/data/test1/local2hdfs.seq /home/haidong.wang/data/data_tmpSave
hadoop jar ./Test.jar 3 /user/data/test1/data_000001.seq,/user/data/test1/data_000002.seq 53ac2be3debeb950084f79b3fe7a5905.jpg,00e810517a53d7134a6cf471
5e67f7a7.jpg

用scp传输文件到HDFS本地文件
time scp -r data_1038_hand_v2/ haidong.wang@hdfsvm005.hogpu.cc:/home/haidong.wang/data
real    11m21.867s
user    1m7.764s
sys 0m45.221s

上传到HDFS的SequenceFile
 time hadoop jar ./Test.jar 1 /home/haidong.wang/data/data_1038_hand_v2/data_000001/ /user/data/test1/data_000001.seq                       
real 3m7.299s
user 1m59.691s
sys  0m7.801s
1942267494

拉取文件到本地：
time hadoop jar ./Test.jar 2 /user/data/test1/data_000001.seq /home/haidong.wang/data/data_tmpSave
real 0m22.576s
user 0m18.302s
sys  0m6.164s

需要查找的图片列表做成一个HashTable，遍历SequenceFile的key


MR测试
hadoop jar ./Test.jar /user/haidong.wang/class6/input/dept /user/haidong.wang/class6/input/emp /user/haidong.wang/class6/out1
hadoop fs -cat /user/haidong.wang/class6/out1/part-r-00000
ACCOUNTING      8750
RESEARCH 6775
SALES  9400



hadoop jar ./Test.jar /user/data/test1/job.properties
hadoop jar ./Test.jar ./local2hdfs.txt /user/data/test1/local2hdfs.txt
hadoop fs -cat /user/data/test1/local2hdfs.txt

hadoop jar ./Test.jar /user/haidong.wang/seq/input /user/haidong.wang/seq/output




ssh haidong.wang@hdfsvm005.hogpu.cc
aA5300066
10.10.10.184
登陆上  用 yarn 命令提交

ssh 
ssh laipeng.han@hdfsvm001.hogpu.cc
strong2017


查看库中数据【无需权限】
查看库中所有的项目
python bin/run.py -l project
查看库中项目id为17的所有数据
python bin/run.py -l datalist -i 17
查看库中数据id为198的所有版本
python bin/run.py -l data -i 198
下载数据【需要数据所在项目的下载权限】
下载数据id为198的最新版本的标注结果，无图片
python bin/run.py -d -i 198
下载数据id为198的最新版本的标注结果，加图片
python bin/run.py -d -i 198 -n
下载数据id为198，版本号为3的标注结果
python bin/run.py -d -i 198 -v 3
下载数据id为198，标注内容为lane,face,person的最新版本数据
python bin/run.py -d -i 198 -c "lane,face,person"
批量下载数据id为463，版本为1，数据id为514，版本为1的数据
python bin/run.py -d -i 463#1,514#1（可选-o参数，加上会下载数据到本地文件夹，不加只会告诉对应多个任务的task_id）
下载标注任务id为836的数据。标注任务还在进行中时，也可以下载到已经标注的结果。
python bin/run.py -d -r 836
上传标注结果【需要数据所在项目的上传权限】
上传数据id为198的标注结果，本地文件为file_name
python bin/run.py -a -i 198 -f file_name -m data_describe
查询上传、下载任务的状态【创建者可以查询】
python bin/run.py -s -i 59584
返回结果：[Status] 59584 `s status is 下载数据完成. json={"code":0,"URL":"http:\/\/10.19.19.21\/output_dir\/59584\/datasystem_output_2016-08-18-14-03-10_926828.tar"}
帮助
python bin/run.py -h
下载SDK

wget http://10.19.19.21/output_dir/HDS_TOOLS.tar
联系liaojie，开通帐号，权限http://10.19.19.21/basic/web/index.php
下载与上传文件的数据格式为： datasystem_output_{random_num}.tar









http://blog.csdn.net/u010619243/article/details/54633140

ssh wanghaidong@10.19.19.23
888

hdfs  dfs -ls hdfs://yz-gpu034.hogpu.cc:8020/user/test/

hadoop version
/usr/hdp/2.4.2.0-258/hadoop/hadoop-common-2.7.1.2.4.2.0-258.jar


SequenceFile文件是Hadoop用来存储二进制形式的key-value对而设计的一种平面文件(Flat File)。目前，也有不少人在该文件的基础之上提出了一些HDFS中小文件存储的解决方案，他们的基本思路就是将小文件进行合并成一个大文件，同时对这些小文件的位置信息构建索引。不过，这类解决方案还涉及到hadoop的另一种文件格式——MapFile文件。SequenceFile文件并不保证其存储的key-value数据是按照key的某个顺序存储的，同时不支持append操作。

支持文件分割
本地切分
压缩
http://www.aboutyun.com/thread-4893-1-1.html

/home/wanghaidong/install/python27/bin/python 

测试Hbase上传的数据：
ssh test@10.19.19.23    horizon123
数据目录（文件个数116768）：/home/test/platform/dongmin/HDS_TOOLS/data_1038_hand_v2
scp -r test@10.19.19.23:/home/test/platform/dongmin/HDS_TOOLS/data_1038_hand_v2 .
 
Hbase账户
haidong.wang@hdfsvm005.hogpu.cc haidong2017

HDFS集群
yz-gpu034 - yz-gpu036 3台机器
hdfs://yz-gpu034.hogpu.cc:8020      10.10.10.34
hdfs dfs -ls  hdfs://yz-gpu034.hogpu.cc:8020/user/wanghaidong
hdfs  dfs -ls hdfs://yz-gpu034.hogpu.cc:8020/user/test/
time hdfs  dfs -put ./data_1038_hand_v2 hdfs://yz-gpu034.hogpu.cc:8020/user/test/
查看文件夹大小
time hdfs  dfs -count -q hdfs://yz-gpu034.hogpu.cc:8020/user/test/data_1038_hand_v2
上传11GB数据（只上传了10.7G）
real    60m11.039s
user    5m31.852s
sys 3m7.588s

下载：10.7 G
hadoop fs -du -s -h hdfs://yz-gpu034.hogpu.cc:8020/user/test/
time hdfs  dfs -get ./data_1038_hand_v2 hdfs://yz-gpu034.hogpu.cc:8020/user/test/ .
只下载了2.4G，24781（141个文件/s，1000w个文件19小时，7毫秒/文件）
real    2m55.147s（175s）
user    0m57.693s
sys 0m20.759s





需求
FastDFS图片服务器
动态扩容
根据fileID

压力测试Nginx报告
运维：半小时解决
监控

HDFS
压力性能、功能测试

《程序员修炼之道》
暴露问题


MyEclipse

http://intern-whdl.hobot.cc:8080/AP2/verify?userName=haidong.wang&password=aA5300066

Eclipse部署：
Terminal:
D:\DFS>scp -r HDFS.jar haidong.wang@10.10.10.184:/home/haidong.wang
[haidong.wang@hdfsvm005 ~]$ hadoop jar ./HDFS.jar 1 ./download/6d1bd59b-20c7-48bb-85ec-172fd5886baf/


