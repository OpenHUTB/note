


file_put_contents("/home/wanghaidong/ap2/log/run/hello", $cmd);  // FILE_APPEND

1版本
2版本 
原图是跳的

下载版本数据没有走hadoop分支
需要追加文件 写成一个文件，实际可能有多个.json文件分散开来，只要image_key对应上就行
20000张图片一个文件夹，不是一定data_000001   -- 解压还需要还原？

git revert 463fa3bd379cb212fe91b9474e63be4ee2f9f07b
463fa3bd379cb212fe91b9474e63be4ee2f9f07b

git reset --hard 463fa3bd379cb212fe91b9474e63be4ee2f9f07b

/home/wanghaidong/AP2/server/www/datasys

一、上传原始数据
  1. 上传(-b)FTP目录(-t)下的原始图片，对应的业务项目组(-j)为13，切分方式(-g)为1，返回任务id（用于上传原始数据进度查询）
python run.py -b -t ftp://dongmin:888@10.19.19.23/ftp/predict/img -j 3 -g 1 -u system001 -p 111111
python run.py -b -t ftp://yaorui:888@10.19.19.23/img/pic1 -j 3 -g 1 -u system001 -p 111111

python run.py -b -t ftp://dongmin:888@10.19.19.23/ftp/predict/img -j 3 -g 1 -z wanghaidong -u system001 -p 111111
-z (***) 插入异常，为func_pycurl.py
python run.py -b -t ftp://yaorui:888@10.19.19.23/img/pic1 -j 3 -g 1 -u system001 -p 111111
http://10.19.19.23:8200/datasys/devops/info/api/?action=rawUpload&firm=3&split=1&path=ftp://yaorui:888@10.19.19.23/img/pic1&username=system001&passwd=111111
http://10.19.19.23:8200/datasys/devops/info/api/?action=rawUpload&firm=3&split=1&comment=***&&username=system001&passwd=111111&path=ftp://yaorui:888@10.19.19.23/img/pic1
  1. 原始数据上传状态查询，-i为上传返回的任务id
python run.py -x -i 2310 -u system001 -p 111111
 
 
二、上传结果数据
  1. 上传(-a)FTP地址的结果数据，结果数据所对应的原始数据id(-w)为297
python run.py -a -t ftp://dongmin:888@10.19.19.23/ftp/predict/result/data_000001.json -w 2310 -u system001 -p 111111
  1. 上传(-a)HTTP地址的结果数据，结果数据所对应的原始数据id(-w)为197，返回上传任务id（用于上传结果数据进度查询）
python run.py -a -t http://10.19.19.23:8200/tmp/data_000001.json -w 197 -u system001 -p 111111

http://10.19.19.23:8200/datasys/devops/info/api/?action=resUpload&username=system001&passwd=111111&raw=371&path=ftp://dongmin:888@10.19.19.23/ftp/predict/result/data_000001.json&comment=donghaiwang
python run.py -a -t ftp://dongmin:888@10.19.19.23/ftp/predict/result/data_000001.json -z donghaiwang -w 2310 -u system001 -p 111111
  1. 上传进度查询
python run.py -y -i 58223 -u system001 -p 111111
 
 
三、下载数据【需要数据的下载权限】
  1. 下载数据id为297，版本号为1的标注结果，无图片（返回用于下载进度查询的任务id）
python run.py -d -i 2310#1 -u system001 -p 111111
  1. 下载数据id为198，版本号为3的标注结果，加图片（增加-n）
python run.py -dn -i 198#3 -u system001 -p 111111
  1. 下载数据id为198，版本号为3的标注结果，加图片，并下载解压到本地的./data/目录下（增加-o）
python run.py -dno -i 198#3 -u system001 -p 111111
  1. 下载状态查询
python run.py -s -i 129 -u system001 -p 111111




python run.py -b -t ftp://yaorui:888@10.19.19.23/img/pic1 -j 13 -g 1 -u system001 -p 111111
python run.py -dn -i 2296#0 -u 标注员yr -p 123654


wanghaidong:
python run.py -b -t ftp://yaorui:888@10.19.19.23/img/pic1 -j 13 -g 1  -u system001 -p 111111
python run.py -dn -i 312#0 -u 标注员yr -p 123654
file_put_contents("/home/wanghaidong/AP2/server/www/datasys/hello.txt", "haha", FILE_APPEND);  // FILE_APPEND
python run.py -b -t ftp://yaorui:888@10.19.19.23/img/pic1 -j 13 -g 1 -u 甲方管理员 -p 123654
// python run.py -x -i 311  -u 甲方管理员 -p 123654
python run.py -dn -i 311#0 -u 标注员yr -p 123654


alter table data_down_list add img int


python run.py -dn -i 2272#0 -u 甲方管理员 -p 123654
python run.py -dn -i 2275#0 -u 甲方管理员 -p 123654
python run.py -dn -i 2278#0 -u 标注员yr -p 123654
python run.py -dn -i 2279#0 -u 标注员yr -p 123654

python run.py -b -t ftp://yaorui:888@10.19.19.23/img/pic1 -j 13 -g 1 -u 甲方管理员 -p 123654

python run.py -b -t ftp://yaorui:888@10.19.19.23/img/pic1 -j 13 -g 1 -u system001 -p 111111

大图上传原始数据
python run.py -b -t ftp://dongmin:888@10.19.19.23/ftp/predict/img -j 3 -g 1 -u system001 -p 111111
结果数据
python run.py -a -t ftp://dongmin:888@10.19.19.23/ftp/predict/result/data_000001.json -w 2233 -u system001 -p 111111

file_put_contents("/home/yaorui/software/nginx-1.7.9/html/datasystem-server/www/datasys/hello.txt", $cmd, FILE_APPEND);
file_put_contents("/home/yaorui/software/nginx-1.7.9/html/datasystem-server/www/datasys/hello.txt", $var_export($cmd,true), FILE_APPEND);

-b -t ftp://yaorui:888@10.19.19.23/img/pic1 -j 3 -g 1 -u system001 -p 111111

/home/yaorui/software/nginx-1.7.9/html/datasystem-server/www/datasys/
export HADOOP_USER_NAME=wanghaidong








vi lib/comm/resprocess.php
$conf = self::completeConf($conf);
修改conf/resup.php成相对路径

data_ver_list: backup (长度改为255)

更新./model/data/verlist.php
./model/data/dowlist.php
scripts/result/result_download.php


/home/yaorui/software/php-5.6.30/bin/php /home/yaorui/yali/datasystem-server/www/datasys/daemon/data/rawupload.php


上传原始数据
http://10.19.19.23:8616/datasys/devops/info/api/?action=rawUpload&username=system001&passwd=111111&firm=13&split=1&path=ftp://dongmin:888@10.19.19.23/ftp/predict/img

http://10.19.19.23:8616/datasys/devops/info/api/?action=rawUploadStatus&username=system001&passwd=111111&task=2185

上传结果数据
http://10.19.19.23:8616/datasys/devops/info/api/?action=resUpload&username=system001&passwd=111111&raw=2185&path=ftp://dongmin:888@10.19.19.23/ftp/predict/result/data_000001.json

http://10.19.19.23:8616/datasys/devops/info/api/?action=resUploadStatus&username=system001&passwd=111111&task=58073

结果数据下载
http://10.19.19.23:8616/datasys/devops/info/api/?action=download&username=system001&passwd=111111&data=2185&version=7&img=1

http://10.19.19.23:8616/datasys/devops/info/api/?action=status&username=system001&passwd=111111&task=24




git ignore 
web conf

上午，需要和前端原来接口没有保持一致，需要进行修改
风险点：项目详情页增加标注进度列（周四）

目标和预期产出


api() info()只会给SDK调用，
需要和前端原来的调用保持一致，并且原来不在HDFS的数据（即在本地的数据（是一个本地的地址，而不是FTP地址）也需要上传到HDFS上去，再进行下载）

改造上传下载脚本

和原来web前端出现不兼容
扩展，notify去除文件监控，ssh2免登录



http://10.19.19.23:8616/datasys/devops/info/api/?action=status&username=system001&passwd=111111&task=12

http://10.19.19.23:8100/datasys/devops/info/api/?action=download&username=system001&passwd=111111&data=36&version=0&img=1

 

http://10.19.19.23:8616/tmp/tmpfile/120_12_1501136351_899687.tar.gz

http://10.19.19.23:8616/datasys/devops/info/api/?action=status&username=system001&passwd=111111&task=12

{"error":0,"msg":"ok","data":{"status":"3","tip":"http:\/\/10.19.19.23:8616\/tmp\/tmpfile\/120_12_1501136351_899687.tar.gz"}}




这周完成下载功能

用户名和密码做用户控制，加上down_list做下载权限控制，上传和浏览等使用系统权限控制
上传和hdfs
上传数据你需要改造我原有的脚本, 看看我的代码，在devops里面做开发
上传数据是一个单独的权限，你去看看上传数据的controller里面就知道了
sdk基于我的devops改造实现

下载后的目录配置
Mysql密码
lib/rbac/user.php login($username, $passwd, $remember=false)

策略
下载判断权限，缓存，还有指定用户名和密码下载
logical/data/download验证权限  Model_user_permission   __construct：cache
验证登录/logic/rbac/user.php -> info()  $user=...  是否登录

接口实验没问题后，使用sdk再跑一遍

sdk就是一个client，接口是实际执行命令的程序，你下载带图片的数据到sdk不是还要sdk解压么



LibLogic
请求来源，from来自SDK， 公用
原始数据ID

id version
检查 下载一次， 别人调用 ，检查是否是1，2个小时，
id 返回给前端 状态时间更新

再来任务id是否下载玩
主线程返回id, url

res中合体 raw+ver

Ph: wanghaidong wanghaidong
git remote set-url origin http://wanghaidong@ph.horizon-robotics.com/diffusion/DATASYSTEMIISERVER/datasystem-server.git
git config --global user.name "haidong.wang"
git config --global user.email "haidong.wang@hobot.cc"

git init
git remote add origin http://ph.horizon-robotics.com/diffusion/DATASYSTEMIISERVER/datasystem-server.git

wanghaidong
wanghaidong

git clone http://haidong.wang:aA5300066@ph.horizon-robotics.com/diffusion/DATASYSTEMIISERVER/datasystem-server.git

测试链接：http://10.19.19.23:8200/datasys/data/raw/view/

开发接口：
预测数据上传（OK）
http://10.19.19.23:8200/datasys/sdk/data/upload/?path=ftp://dongmin:888@10.19.19.23/ftp/car/result/data_000001.json&raw=78

原始数据上传（更新file_num, pic_num字段； 新建表data_raw_127) 需不需要建立data_raw_127
http://10.19.19.23:8200/datasys/sdk/data/rawupload/?firm=1&split=4&path=/home/wanghaidong/AP2/server/www/datasys/logic/sdk/data/data_tmp/

http://10.19.19.23:8200/datasys/sdk/data/rawupload/?firm=1&split=4&path=ftp://wanghaidong:aA5300066@10.19.19.23/AP2/data/tmp/data_000001

下载（下载数据记录为data_down_list中任务状态为1的任务，即已审批通过））：
http://10.19.19.23:8200/datasys/sdk/data/download/?list=[{"raw":50,"version":0},{"raw":50,"version":1}]&image=1
http://10.19.19.23:8200/datasys/sdk/data/download/?list=[{"raw":50,"version":0}]&image=1&username=system001&password=111111


update data_down_list set 'url'='http://10.10.10.184:8080/download/128c00d9-1229-4e54-91b2-75f545f0523c/'
 where id = 6

hdfs://10.10.10.34:8020/user/wanghaidong/AP2/8af465af-7855-4331-99db-aa8cbaa5582b
hdfs://10.10.10.34:8020/user/wanghaidong/AP2/65cde214-9ddb-40f7-84d6-6574cc074af4


ftp://wanghaidong:aA5300066@10.19.19.23/AP2/data/tmp/data_000001.json


http://10.19.19.23:8200/datasys/sdk/data/upload/?path=/home/wanghaidong/AP2/data/data_000002.json&id=123&attch={"step":"20","split":[]}&&comment="test"

上传FTP地址上的文件；下载ssh登录


增加                  ./logic/sdk/data.php
// ./lib/comm/resprocess.php增加函数：upload2HDFS
./lib/conf.php增加    const SDK_CONF           = 'sdk';    // sdk conf for HDFS and FastDFS



框架规则（index.php中进行初始化）：
类Model_data_sdkuploadlist位于./model/data/sdkuploadlist.php中


Q:
需要进行登录，不然this->uid为空
http://10.19.19.23:8200/datasys/rbac/home/login/?name=system001&password=111111
http://10.10.10.184:8080/download/data_000001.json

./conf/resup.php 中'dir' => '/home/wanghaidong/AP2/server/www/datasys/scripts/result' 应该为全路径

增加上传原始路径的长度
alter table data_raw_list modify backup varchar(512);
alter table data_ver_list modify backup varchar(512);
ALTER TABLE data_down_list MODIFY url VARCHAR(512);

 error occur when flush relation record
Remote file no newer than local file 'AP2/data/tmp/data_000001.json' -- not retrieving.
远程文件不比本地文件“%s”新 -- 不取回。n"
FINISHED --2017-07-22 10:19:18--
Total wall clock time: 0.04s
Downloaded: 1 files, 273 in 0s (40.6 MB/s)
download error,error code -1
ambiguous redirect
phpinfo()


$cmd = "cd /home/wanghaidong/AP2/tmp/res/155;wget -nH -m ftp://wanghaidong:aA5300066@10.19.19.23/AP2/data/tmp/data_000001.json";

http://blog.sina.com.cn/s/blog_6e99ef350102vgmv.html
验证PHP ssh2扩展是否安装：php -i | grep ssh
libssh
/home/wanghaidong/AP2/softwares/php-5.6.30/bin/php -i | grep ssh2
./configure --prefix=/home/wanghaidong/AP2/softwares/libssh2-1.4.3
make && make install
ssh2(依赖libssh)
/home/wanghaidong/AP2/softwares/php-5.6.30/bin/phpize(根据该php的配置情况生成对应的configure文件)
./configure --with-php-config=/home/wanghaidong/AP2/softwares/php-5.6.30/bin/php-config --with-ssh2=/home/wanghaidong/AP2/softwares/libssh2-1.4.3 (运行./configure --prefix, 只需要--with-php-config)
make && make install
vi /home/wanghaidong/AP2/softwares/php-5.6.30/lib/php.ini
extension_dir = "/home/wanghaidong/AP2/softwares/php-5.6.30/lib/php/extensions/no-debug-non-zts-20131226/"
extension=ssh2.so
/home/wanghaidong/AP2/softwares/php-5.6.30/bin/php -c /home/wanghaidong/AP2/softwares/php-5.6.30/lib/php.ini
/home/wanghaidong/AP2/softwares/php-5.6.30/bin/php -m (出现ssh2)
重启php-fpm: ps aux | grep php-fpm | grep wanghai | awk '{print $2}' | xargs kill -s 9
/home/wanghaidong/AP2/softwares/php-5.6.30/sbin/php-fpm

wget http://libssh2.org/download/libssh2-1.8.0.tar.gz

inotify
inotify-0.1.6.tgz
tar zxf inotify-0.1.6.tgz
/home/wanghaidong/AP2/softwares/php-5.6.30/bin/phpize
./configure
make -j
cp ./modules/inotify.so /home/wanghaidong/AP2/softwares/php-5.6.30/lib/php/extensions/no-debug-non-zts-20131226/



ls -l /proc/sys/fs/inotify/
http://pecl.php.net/package/inotify


业务项目组 Id
预测数据json
Fast  token  fileid



<?php 

class Logic_sdk_data extends Lib_Logic {
    public function upload(){
        $data = $this->param();
        
        $must = array('path', 'id');
        $option = array('attrs', 'comment');  
        $params = Lib_Comm_Tools::checkParam($data, $must, $option);    
        if(!$params || !Lib_Comm_Tools::checkJson($params, array('attrs'))) {
            $this->error(1, 'param error');
        }
        
        $path = $params['path'];
        unset($params['path']);
        Lib_Comm_Tools::getAddCommonInfo($params, $this->uid);
        $verList = new Model_data_verlist();
        $verId = $verList->add($params);
        
        if($verId){
            Lib_Comm_Resprocess::upload2HDFS($path);
            $this->output('data', array());
        } else {
            $this->error(5, 'sys error, mysql error');
        }
    }
    
}

?>



Python 客户端
-d -i 50#0,50#1 -n -u test -p aA5300066
-d -i 50#0,50#1 -n -p aA5300066 -o
-d -i 50#0 -n -p aA5300066 -o
增加输出目录
-d -i 50#0 -n -p aA5300066 -o -t F:/tmp/

need_image: yes, no



http://10.19.19.23:8616/datasys/devops/info/api/?action=status&username=system001&passwd=111111&task=12

http://10.19.19.23:8100/datasys/devops/info/api/?action=download&username=system001&passwd=111111&data=36&version=0&img=1

0版本数据verlist ver=0 backup地址
下载  检查下backup字段  上传到HDFS 
下载的时候的 判断  并上传

数据库中
重要：上传预测数据
上传HDFS 是原始图片



连接Ubuntu的mysql
<?php
$conf = array(
    'default' => array(
        'DB_HOSTS' => '127.0.0.1:3306',
        'DB_USERNAME' => 'root',
        'DB_PWD' => 'aA5300066',
        'DB_DATABASE' => 'data_sys',
    ),
);
$tc = array(
    'default' => array(
        'DB_HOSTS' => '127.0.0.1:3306',
    ),
);
$nj = array(
    'default' => array(
        'DB_HOSTS' => '127.0.0.1:3306',
    ),
);
$gz = array(
    'default' => array(
        'DB_HOSTS' => '127.0.0.1:3306',
    ),
);


<?php
$conf = array(
    'default' => array(
        'DB_HOSTS' => '10.19.19.23:8798',
        'DB_USERNAME' => 'dongmin',
        'DB_PWD' => '1234',
        'DB_DATABASE' => 'data_sys',
    ),
);
$tc = array(
    'default' => array(
        'DB_HOSTS' => '10.19.19.23:8798',
    ),
);
$nj = array(
    'default' => array(
        'DB_HOSTS' => '10.19.19.23:8798',
    ),
);
$gz = array(
    'default' => array(
        'DB_HOSTS' => '10.19.19.23:8798',
    ),
);

<?php
$conf = array(
    'default' => array(
        'DB_HOSTS' => '10.19.19.23:3319',
        'DB_USERNAME' => 'root',
        'DB_PWD' => 'a5300066',
        'DB_DATABASE' => 'data_sys',
    ),
);
$tc = array(
    'default' => array(
        'DB_HOSTS' => '10.19.19.23:3319',
    ),
);
$nj = array(
    'default' => array(
        'DB_HOSTS' => '10.19.19.23:3319',
    ),
);
$gz = array(
    'default' => array(
        'DB_HOSTS' => '10.19.19.23:3319',
    ),
);





http://10.64.39.222:8200/datasys/devops/info/api/?action=download&username=system001&passwd=111111&data=36&version=0&img=1
{"error":0,"msg":"ok","data":{"task":"59"}}

http://10.64.39.222:8200/datasys/devops/info/api/?action=status&username=system001&passwd=111111&task=59

wget ftp://dongmin:888@10.19.19.23/ftp/tmp/data_1543_person_v1/result/data_000001.json


原始数据上传
http://10.64.39.222:8200/datasys/devops/info/api/?action=rawUpload&username=system001&passwd=111111&firm=13&split=1&path=ftp://dongmin:888@10.19.19.23/ftp/tmp/data_1543_person_v1/result/data_000001.json


http://10.1919:8200/datasys/devops/info/api/?action=rawUpload&username=system001&passwd=111111&firm=13&split=1&path=ftp://dongmin:888@10.19.19.23/ftp/tmp/data_1543_person_v1/result/data_000001.json


开发接口：
预测数据上传（OK）
http://10.19.19.23:8200/datasys/devops/info/api/?action=rawUpload&username=system001&passwd=111111&firm=13&split=1&path=ftp://dongmin:888@10.19.19.23/ftp/tmp/data_1543_person_v1/result/data_000001.json




http://10.19.19.23:8200/datasys/sdk/data/upload/?path=ftp://dongmin:888@10.19.19.23/ftp/car/result/data_000001.json&raw=78

原始数据上传（更新file_num, pic_num字段； 新建表data_raw_127) 需不需要建立data_raw_127
http://10.19.19.23:8200/datasys/sdk/data/rawupload/?firm=1&split=4&path=/home/wanghaidong/AP2/server/www/datasys/logic/sdk/data/data_tmp/

http://10.19.19.23:8200/datasys/sdk/data/rawupload/?firm=1&split=4&path=ftp://wanghaidong:aA5300066@10.19.19.23/AP2/data/tmp/data_000001

下载（下载数据记录为data_down_list中任务状态为1的任务，即已审批通过））：
http://10.19.19.23:8200/datasys/sdk/data/download/?list=[{"raw":50,"version":0},{"raw":50,"version":1}]&image=1
http://10.19.19.23:8200/datasys/sdk/data/download/?list=[{"raw":50,"version":0}]&image=1&username=system001&password=111111


修改
./conf/pass.php
$conf = array(
    //'prefix' => 'ftp://upload:99754106633f94d35@10.19.19.25/',
    'prefix' => '',
);

./lib/comm/resprocess.php
resUpload()  --> $cmd = "cd {$conf['dir']};
//$conf = self::completeConf($conf);
$ret = Lib_Comm_Resprocess::upload($infos); $ret=1; 

增加上传原始路径的长度
alter table data_raw_list modify backup varchar(256);
alter table data_ver_list modify backup varchar(256);
ALTER TABLE data_down_list MODIFY url VARCHAR(256);


SELECT id,res,image_key,vindex,pindex,width,height,token,result FROM data_result_191 WHERE `res`='224' ORDER BY vindex,pindex LIMIT 0,1000
data_result_191中表res=230改为224
update data_result_191 set res='224';


224_11_1502095659_300506.t


原始数据上传
http://10.19.19.23:8200/datasys/devops/info/api/?action=rawUpload&username=system001&passwd=111111&firm=13&split=1&path=ftp://dongmin:888@10.19.19.23/ftp/predict/img
/home/wanghaidong/AP2/softwares/php-5.6.30/bin/php /home/wanghaidong/AP2/server/www/datasys/daemon/data/rawupload.php &

http://10.19.19.23:8200/datasys/devops/info/api/?action=rawUpload&username=system001&passwd=111111&firm=13&split=1&path=ftp://dongmin:888@10.19.19.23/ftp/tmp/data_1543_person_v1/data_000001

http://10.19.19.23:8200/datasys/devops/info/api/?action=rawUpload&username=system001&passwd=111111&firm=1&split=1&path=ftp://dongmin:888@10.19.19.23/ftp/predict/img

http://10.19.19.23:8200/datasys/data/raw/upload/?process={"step":"","split":[]}&firm=10&path=ftp://dongmin:888@10.19.19.23/ftp/tmp/data_1543_person_v1/data_000001&split=1&comment=test&attch=&compress=0&secret=0
结果数据上传
http://10.19.19.23:8200/datasys/devops/info/api/?action=resUpload&username=system001&passwd=111111&raw=191&path=ftp://dongmin:888@10.19.19.23/ftp/predict/result/data_000001.json

http://10.19.19.23:8200/datasys/devops/info/api/?action=resUpload&username=system001&passwd=111111&raw=189&path=ftp://dongmin:888@10.19.19.23/ftp/tmp/data_1543_person_v1/result/data_000001.json
下载
http://10.19.19.23:8200/datasys/devops/info/api/?action=download&username=system001&passwd=111111&data=191&version=1&img=1

http://10.19.19.23:8200/datasys/devops/info/api/?action=download&username=system001&passwd=111111&data=197&version=2&img=1
结果数据id=235

http://10.19.19.23:8200/datasys/devops/info/api/?action=download&username=system001&passwd=111111&data=196&version=0&img=1
结果数据id=232

http://10.19.19.23:8200/datasys/devops/info/api/?action=status&username=system001&passwd=111111&task=11

data_ver_list: id=224
data_down_list: id=11
{"error":0,"msg":"ok","data":{"task":"11"}}

data_ver_list, id=224, backup=hdfs://10.10.10.34:8020/user/wanghaidong/AP2/9212a833-17c4-4274-a26e-92aa1e89fc73

查询状态
http://10.19.19.23:8200/datasys/devops/info/api/?action=status&username=system001&passwd=111111&task=11
{"error":0,"msg":"ok","data":{"status":"0","tip":"no permission"}}
将data_down_list的状态改为1，{"error":0,"msg":"ok","data":{"status":"2","tip":"please waiting for download"}}

查看状态
http://10.19.19.23:8200/datasys/devops/info/api/?action=status&username=system001&passwd=111111&task=12

浏览器实际参数
http://10.19.19.23:8100/datasys/data/raw/upload/
process={"step":"","split":[]}&firm=10&path=ftp://dongmin:888@10.19.19.23/ftp/tmp/data_1543_person_v1/data_000001&split=1&comment=test test test&attch=&compress=0&secret=0

原始数据上传查询
http://10.19.19.23:8200/datasys/devops/info/api/?action=rawUploadStatus&username=system001&passwd=111111&task=201
http://10.19.19.23:8200/datasys/devops/info/api/?action=rawUpload&username=system001&passwd=111111&firm=13&split=1&path=ftp://dongmin:888@10.19.19.23/ftp/predict/img
返回：{"error":0,"msg":"ok","data":{"task":201}}

结果数据上传查询
http://10.19.19.23:8200/datasys/devops/info/api/?action=resUpload&username=system001&passwd=111111&raw=191&path=ftp://dongmin:888@10.19.19.23/ftp/predict/result/data_000001.json
http://10.19.19.23:8200/datasys/devops/info/api/?action=resUploadStatus&username=system001&passwd=111111&task=250

权限理解
http://10.19.19.23:8200/datasys/devops/info/api/?action=download&username=system001&passwd=111111&data=197&version=0&img=1
raw=197 version=0  -> data_verlist 版本数据id=233

pro_firm_list记录业务项目组的信息 13  parsing项目  区域
user_auth_permission 记录用户授权信息(./model/user/resource.php)
value:13 业务项目组资源ID
$this->firmlevel = array(
            'plantform' => 1,   // 平台
            'firm' => 2,        // 业务项目组
            'project' => 3, // 项目
            'data' => 4,        // 数据
        );
$this->restype = array(     // 资源类型
            'plantform' => 1,
            'firm' => 2,
            'project' =>3,
            'raw' => 4,
            'res' => 5,
            'zero' => 6,
        );
$this->authstatus = array(      // 授权值，可以进行累加63
            'upload' => 1,
            'create' => 2,
            'retrieve' => 4,
            'update' => 8,
            'delete' => 16,
            'grant' => 32,
        );
uid,level, type, act 某个用户对某一层级的资源的操作类型
INSERT INTO user_auth_permission (field, level, value, type, uid, auth, update_time, update_user, create_time, create_user, is_del) VALUES (1, 4, 3, 4, 1, 63, 1496833017, 2, 1496833017, 2, 0);





