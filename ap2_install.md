 
data_web
http://10.19.19.23:8200/web/html-data/data_list.html
替换/logic/data/*、/model/data/*、/lib/comm/tools.php
404: 修改/web/js/util/nav_data.js, 修改 var dataurl = '/web/html-data/'，或者强制刷新
var userurl = '/html-user/'
var programurl = '/html-program/'

安装postman: http://jingyan.baidu.com/article/a17d528513abe28099c8f274.html

后台常驻任务：
原始数据上传
/home/wanghaidong/AP2/softwares/php-5.6.30/bin/php /home/wanghaidong/AP2/server/www/datasys/daemon/data/rawupload.php &
ps aux | grep rawupload.php
更新资源表
/home/wanghaidong/AP2/softwares/php-5.6.30/bin/php /home/wanghaidong/AP2/server/www/datasys/daemon/user/resource.php &


gcc:
(wget http://ftp.gnu.org/gnu/gcc/gcc-4.8.5/gcc-4.8.5.tar.gz)
Cannot find appropriate C++ compiler on this system.  
Please specify one using environment variable CXX.  
--yum install gcc-c++

安装mysql出现Could NOT find Curses (missing CURSES_LIBRARY CURSES_INCLUDE_PATH)
yum install ncurses-devel

命令行登录mysql报Segmentation fault
vi ./cmd-line-utils/libedit/terminal.c
把terminal_set方法中的 char buf[TC_BUFSIZE]; 这一行注释,再把 area = buf;改为 area = NULL;

Navicate连接失败：
（1）永久关闭SELinux（否则samba可能不能访问）
修改配置文件
# vi /etc/selinux/config
将SELINUX=enforcing改为SELINUX=disabled
需要重启机器生效！！
（2）关闭防火墙
开启： chkconfig iptables on
关闭： chkconfig iptables off

**************************************************************************************
**************************************************************************************
cmake:
wget https://cmake.org/files/v3.3/cmake-3.3.2.tar.gz
./bootstrap
./configure --prefix=/home/wanghaidong/AP2/softwares/cmake-3.3.2
make
make install
vi ~/.bashrc
export PATH=$PATH:/home/wanghaidong/AP2/softwares/cmake-3.3.2/bin
source ~/.bashrc
echo $PATH

**************************************************************************************
Mysql: https://www.chenyudong.com/archives/building-mysql-5-6-from-source.html
**************************************************************************************
sudo apt-get install libncurses5-dev (设置光标的位置和终端屏幕上显示的字符样式)
在源码包里,编辑文件 cmd-line-utils/libedit/terminal.c
把terminal_set方法中的 char buf[TC_BUFSIZE]; 这一行注释,再把 area = buf;改为 area = NULL;

wget http://dev.mysql.com/get/Downloads/MySQL-5.6/mysql-5.6.16.tar.gz
tar zxvf mysql-5.6.16.tar.gz
cd mysql-5.6.16/

cmake \
-DCMAKE_INSTALL_PREFIX=/home/ubuntu/software/mysql-5.6.16 \
-DMYSQL_DATADIR=/home/ubuntu/software/mysql-5.6.16/data \
-DSYSCONFDIR=/home/ubuntu/software/mysql-5.6.16/sysconf \
-DWITH_MYISAM_STORAGE_ENGINE=1 \
-DWITH_INNOBASE_STORAGE_ENGINE=1 \
-DWITH_MEMORY_STORAGE_ENGINE=1 \
-DWITH_READLINE=1 \
-DMYSQL_UNIX_ADDR=/home/ubuntu/software/mysql-5.6.16/mysql.sock \
-DMYSQL_TCP_PORT=3306 \
-DENABLED_LOCAL_INFILE=1 \
-DWITH_PARTITION_STORAGE_ENGINE=1 \
-DEXTRA_CHARSETS=all \
-DDEFAULT_CHARSET=utf8 \
-DDEFAULT_COLLATION=utf8_general_ci

make j8 && make install

./scripts/mysql_install_db --user=wanghaidong --ldata=/home/wanghaidong/ap2/software/mysql-5.6.16/data

启动Mysql:
netstat -lntp | grep 3306
vi ./my.cnf
port = 3319
./bin/mysqld --defaults-file=./my.cnf
ps aux | grep mysql  (netstat -tnlp | grep 3319)

设置超时：show variables like '%timeout%'; (看不到更新)
vi my.cnf
| wait_timeout                | 28800    |
interactive_timeout=2880000
wait_timeout=2880000
./bin/mysqld restart --defaults-file=./my.cnf
set global interactive_timeout=2880000;
show variables like '%timeout%';

修改root密码
mysql -u root
UPDATE user SET Password = PASSWORD('ubuntu') WHERE user = 'root';
FLUSH PRIVILEGES;

mysql -uroot -p -h10.19.19.23 -P3319        密码：a5300066
use mysql;
desc user;
GRANT ALL PRIVILEGES ON *.* TO root@"%" IDENTIFIED BY "ubuntu";　　//为root添加远程连接的能力。(后面必须是root的密码）
update user set Password = password('a5300066') where User='root';
select Host,User,Password  from user where User='root';
flush privileges;
mysql -uroot -pa5300066 -h10.19.19.23 -P3319        使用密码登录mysql:a5300066

导入.sql数据：
mysql -uroot -p -h10.19.19.23 -P3319
create database data_sys;
use data_sys;
source /home/wanghaidong/AP2/server/tools/data/data_sys.sql     (Failed to open file '*.sql': *.sql所在的文件系统必须是登录mysql前所在的文件系统）

重建数据库：
drop database data_sys;
create database data_sys;
use data_sys;
source /home/wanghaidong/AP2/install/sql/data_sys.sql
source /home/wanghaidong/AP2/install/sql/user_rbac.sql
source /home/wanghaidong/AP2/install/sql/user_rbac_data_test.sql

path长度需要改成255
data_down_list需要增加comment属性

mysql-workbench: sudo apt-get install mysql-workbench

启动方式不对，需要用脚本启动后台进程
/bin/sh ./bin/mysqld_safe --defaults-file=./my.cnf
（后台出现：/home/wanghaidong/AP2/softwares/mysql-5.6.16/bin/mysqld --defaults-file=./my.cnf --basedir=/home/wanghaidong/AP2/softwares/mysql-5.6.16 --datadir=/home/wanghaidong/AP2/softwares/mysql-5.6.16/data --plugin-dir=/home/wanghaidong/AP2/softwares/mysql-5.6.16/lib/plugin --log-error=/home/wanghaidong/AP2/softwares/mysql-5.6.16/data/dl023.hobot.cc.err --pid-file=/home/wanghaidong/AP2/softwares/mysql-5.6.16/data/dl023.hobot.cc.pid --port=3319）


navicate:
出现：access violation at address in module 'vavicate.exe'
解决：属性界面，选择左侧边栏的“高级系统设置”;“高级”选项卡下的“性能”中的“设置”按钮。
在性能选项中，勾选“为除下列程序之外的所有程序和服务启用DEP”，如果不需要设置不启用DEP的应用程序或服务的话，直接点击“确定”按钮即可。如果需要设置，点击“添加”按钮按照第①②步中找到的路径添加不需要启用DEP的应用程序。


**************************************************************************************
PHP (tar zxvf php-5.6.30.tar.gz)
configure: error: xml2-config not found.
yum install libxml2
yum install libxml2* -y

configure: error: Cannot find OpenSSL's <evp.h>
yum install openssl openssl-devel
ln -s /usr/lib64/libssl.so /usr/lib/

checking for cURL in default path... not found
wget  http://curl.haxx.se/download/curl-7.38.0.tar.gz
tar -xzvf curl-7.38.0.tar.gz
cd curl-7.38.0
./configure
make
make install

configure: error: jpeglib.h not found.
yum install  libjpeg-devel

configure: error: png.h not found
yum install libpng-devel

configure: error: freetype-config not found.
yum -y install gcc gcc-c++  make cmake automake autoconf kernel-devel ncurses-devel libxml2-devel openssl-devel curl-devel libjpeg-devel libpng-devel  pcre-devel libtool-libs freetype-devel gd zlib-devel file bison patch mlocate flex diffutils   readline-devel glibc-devel glib2-devel bzip2-devel gettext-devel libcap-devel libmcrypt-devel openldap openldap-devellibxslt-devel

/lib64/libc.so.6: version `GLIBC_2.14' not found 
strings /lib64/libc.so.6 | grep GLIBC
http://mirrors.ustc.edu.cn/gnu/libc/
wget http://mirrors.ustc.edu.cn/gnu/libc/glibc-2.14.tar.gz
../configure --prefix=/usr/local/glibc-2.14
make -j2
make install
cd /usr/local/glibc-2.14/lib
cp libc-2.16.so /lib64/
cd /lib64
rm -rf libc.so.6
/sbin/sln libc-2.14.so /lib64/libc.so.6
strings /lib64/libc.so.6 |grep GLIBC
**************************************************************************************
ubuntu
sudo apt-get install libxml2-dev
sudo apt-get install openssl
sudo apt-get install libcurl3-openssl-dev
sudo apt-get install libssl-dev (evp.h)
sudo apt-get -y install libfreetype6-dev
**************************************************************************************
wget http://cn2.php.net/distributions/php-5.6.30.tar.gz
(./configure --prefix=/home/wanghaidong/AP2/softwares/php-5.6.30 --enable-fpm --with-fpm-user=www --with-fpm-group=www --with-mysql=mysqlnd --with-mysqli=mysqlnd --with-pdo-mysql=mysqlnd --with-iconv-dir --with-freetype-dir --with-jpeg-dir --with-png-dir --with-zlib --with-libxml-dir --enable-xml --disable-rpath --enable-bcmath --enable-shmop --enable-sysvsem --enable-inline-optimization --with-curl --enable-mbregex --enable-mbstring --with-gd --enable-gd-native-ttf --with-openssl --with-mhash --enable-pcntl --enable-sockets --with-xmlrpc --enable-zip --enable-soap --without-pear)
./configure --prefix=/home/wanghaidong/ap2/software/php-5.6.30 --enable-fpm --with-fpm-user=www --with-fpm-group=www --with-mysql=mysqlnd --with-mysqli=mysqlnd --with-pdo-mysql=mysqlnd --with-iconv-dir --with-freetype-dir --with-jpeg-dir --with-png-dir --with-zlib --with-libxml-dir --enable-xml --disable-rpath --enable-bcmath --enable-shmop --enable-sysvsem --enable-inline-optimization --with-curl --enable-mbregex --enable-mbstring --with-gd --enable-gd-native-ttf --with-openssl --with-mhash --enable-pcntl --enable-sockets --with-xmlrpc --enable-zip --enable-soap --without-pear --enable-maintainer-zts --enable-roxen-zts
(ZTS (Zend Threaded System) 

make -j8 && make install

cp ./etc/php-fpm.conf.default ./etc/php-fpm.conf

vi ./etc/php-fpm.conf
listen = 127.0.0.1:9013  （改为9014，默认为9000）

更改时区：修改php.ini，在php.ini中找到data.timezone =去掉它前面的;号，然后设置data.timezone = “Asia/Shanghai”; 

/home/wanghaidong/AP2/softwares/php-5.6.30/sbin/php-fpm (必须启动)

netstat -apn | grep 9013
ps aux | grep php-fpm

重启PHP-fpm:
杀掉master进程，还需杀掉子进程
ps aux | grep php-fpm | grep wanghai | awk '{print $2}' | xargs kill -s 9
/home/wanghaidong/AP2/softwares/php-5.6.30/sbin/php-fpm

phpMyAdmin登录超时：
vi /home/wanghaidong/AP2/softwares/php-5.6.30/lib/php.ini
session.gc_maxlifetime = 36000
/home/wanghaidong/AP2/softwares/phpMyAdmin-4.6.6-all-languages/libraries/config.default.php
$cfg['LoginCookieValidity'] = 36000;


mcrypt扩展安装



**************************************************************************************
nginx
wget ftp://ftp.csx.cam.ac.uk/pub/software/programming/pcre/pcre-8.41.tar.gz
yum clean all
(ubuntu) 
sudo apt-get install libpcre3 libpcre3-dev
sudo apt-get install zlib1g-dev
**************************************************************************************
wget http://nginx.org/download/nginx-1.7.9.tar.gz
./configure --prefix=/home/wanghaidong/ap2/software/nginx-1.7.9
make -j8 && make install
Q: error: this statement may fall through [-Werror=implicit-fallthrough=]
A: (make CFLAGS='-Wno-implicit-fallthrough')


cp -r phpMyAdmin-4.6.6-all-languages/ /home/wanghaidong/AP2/softwares
vi ./libraries/config.default.php
$cfg['Servers'][$i]['port'] = '3319';

netstat -apn | grep 8013
vi ./conf/nginx.conf
listen       8013;
location ~ \.php$ {
    root           /home/wanghaidong/AP2/softwares/phpMyAdmin-4.6.6-all-languages;
    fastcgi_pass   127.0.0.1:9013;
    fastcgi_index  index.php;
    fastcgi_param  SCRIPT_FILENAME  $document_root$fastcgi_script_name;
    include        fastcgi_params;
}

启动服务： ./sbin/nginx
重启nginx: /home/wanghaidong/AP2/softwares/nginx-1.7.9/sbin/nginx -s reload
/home/wanghaidong/AP2/softwares/nginx-1.7.9/sbin/nginx -s stop

http://10.19.19.23:8200/softwares/admin/db_structure.php?server=1&db=data_sys&token=f770035b82d521066ff244e5075e8ca9
http://10.19.19.23:8200/index.php
http://192.168.249.128:8200/index.php
用户名：root    密码：a530006

vi config.inc.php (config.sample.inc.php)    vi ./libraries/config.default.php
localhost -> 127.0.0.1
$cfg['blowfish_secret'] = 'a5300066';

图片不显示错误：
修改nginx/conf/nginx.conf:
location / {
    root   /home/wanghaidong/AP2/softwares/admin;
    index  index.html index.htm;
}

************************************************************************************
wget http://download.redis.io/releases/redis-4.0.9.tar.gz
************************************************************************************
Redis(http://www.cnblogs.com/it-cen/p/4295984.html):
make
cd src
make install PREFIX=/home/wanghaidong/ap2/software/redis-3.2.8
cp ./redis.conf /home/wanghaidong/ap2/software/redis-3.2.8/bin
vi ./redis.conf
port 6392
daemonize yes       ->>后端运行
启动redis服务：./redis-server ./redis.conf
停止redis服务：./redis-cli -p 6392 shutdown

命令行进入： /home/wanghaidong/AP2/softwares/redis-3.2.8/bin/redis-cli -h 10.19.19.23 -p 6392
 
#bind 127.0.0.1 绑定特定IP
关闭保护模式：protected-mode no

获取数据： ./redis-cli -p 6392 get test
keys *
del stat_log_detail
get stat_log_summary
flushall

************************************************************************************
************************************************************************************
安装PHP redis扩展：
https://github.com/nicolasff/phpredis/archive/2.2.4.tar.gz
Redis 目录下执行：/home/wanghaidong/ap2/software/php-5.6.30/bin/phpize
./configure --with-php-config=/home/wanghaidong/ap2/software/php-5.6.30/bin/php-config
make && make install

../bin/php --ini
Configuration File (php.ini) Path: /home/wanghaidong/AP2/softwares/php-5.6.30/lib
拷贝安装目录下的php.ini.development到lib目录下

在重启PHP
查看PHP已有哪些扩展:
/home/wanghaidong/AP2/softwares/php-5.6.30/bin/php -m


Q: perl: warning: Setting locale failed.
vi ~/.bashrc
export LC_ALL=C


************************************************************************************
改Nginx转发：
<?php
define('DATASYS_ENV', 'tc');

location /datasys/ {
            root           /data/sdc/dongmin/app/datasystem-server/www;
            fastcgi_pass   127.0.0.1:9007;
            fastcgi_index  index.php;
            fastcgi_param  SCRIPT_FILENAME  $document_root$fastcgi_script_name;
            include        fastcgi_params;
            rewrite        ^/datasys/(.*)/(.*)/(.*)/$  /datasys/index.php?m=$1&c=$2&a=$3 break; 
        }

访问页面显示：
Deprecated: mysql_select_db(): The mysql extension is deprecated and will be removed in the future: use mysqli or PDO instead in
禁止php报错
display_errors = On 改为 display_errors = Off

http://10.19.19.23:8200/datasys/data/tag/create/?firm=1&category=%E6%95%B0%E6%8D%AE%E7%B1%BB%E5%9E%8B&detail=tessttt
select * from data_tag_list


selenium.common.exceptions.WebDriverException: Message: 'geckodriver' executable needs to be in PATH. 
sudo mv geckodriver /usr/local/bin/



******************************************
FTP
查看本地用户：lcd
必须从23上登录ftp才能上传到23的FTP服务器
Entering Passive Mode       （主动）服务器从20端口向客户端的***X端口发送连接请求，建立一条数据链路来传送数据。  
ftp> passive        关闭客户端的PASV方式，强制其用PORT方式访问服务器，登录FTP服务器后用passive命令关闭客户端的PASV方式
put /home/wanghaidong/AP2/data/carline/20161031_175042.pack 20161031_175042.pack
尝试下载：wget ftp://wanghaidong:888@10.19.19.23/20160604_150130.pack

put /home/wanghaidong/AP2/data/carline/20160604_150130.pack AP2/data/tmp/20160604_150130.pack
wget ftp://wanghaidong:888@10.19.19.23/AP2/data/tmp/20160604_150130.pack


****************************************************************************************
用户权限模块：
替换代码，保留conf文件夹
rewrite ^/(.*)/(.*)/?$ /index.php?c=$1&a=$2 last;       nginx配置，这个规则加原来那个下面



打开路由权限：
vi lib/logic.php
public function checkAccess() {
// return true; // 注释掉



Debug修改数据管理模块源代码：
/home/wanghaidong/AP2/server/www/datasys/model/data/rawlist.php
/home/wanghaidong/AP2/server/www/datasys/logic/data/raw.php


点击两次上传原始数据：
error end of file



**************************************************************************************
统计模块：
改下本地host：/etc/hosts; 10.19.19.23 dpxtest
http://dpxtest:8091/web/index.php       point  888
http://10.19.19.23/dpx/web/index.php
日志log配置在conf/stat.php
鹏翔：每执行一次下一批就在log目录下生成.data日志: /home/wanghaidong/AP2/server/www/datasys/daemon/stat/process.php
nohup /home/wanghaidong/AP2/softwares/php-5.6.30/bin/php /home/wanghaidong/AP2/server/www/datasys/daemon/stat/process.php >/dev/null 2>&1 & 流程是 1.0代码生成日志

测试使用：日志从/home/wanghaidong/AP2/log/statlog/label_log导入redis，redis中生成stat_log_detail
/home/wanghaidong/AP2/softwares/php-5.6.30/bin/php /home/wanghaidong/AP2/server/www/datasys/daemon/stat/dumps.php

redis数据导入mysql表中
nohup /home/wanghaidong/AP2/softwares/php-5.6.30/bin/php /home/wanghaidong/AP2/server/www/datasys/daemon/stat/statLog.php>/dev/null 2>&1 &
标准错误输出到output文件: nohup /home/wanghaidong/AP2/softwares/php-5.6.30/bin/php /home/wanghaidong/AP2/server/www/datasys/daemon/stat/statLog.php>/dev/null 2>error.log &
mysql数据库中生成stat_log_detail_26_1100_2017_0表，stat_log_catlog表中插入一条记录；redis中stat_log_detail变为stat_log_summary
ps aux | grep statLog.php
kill -s 9 27259
vim /home/wanghaidong/AP2/server/www/datasys/daemon/stat/statLog.php
/home/wanghaidong/AP2/softwares/php-5.6.30/bin/php /home/wanghaidong/AP2/server/www/datasys/daemon/stat/statReport.php  前一天的数据形成报表入库
/home/wanghaidong/AP2/softwares/php-5.6.30/bin/php /home/wanghaidong/ap2/datasystem-server/www/datasys/daemon/stat/statReport.php

代码更新 vi /home/wanghaidong/AP2/server/www/datasys/daemon/stat/dumps.php

stat_report_detail和detail_log_detail不一致，修改：/home/wanghaidong/AP2/server/www/datasys/model/stat/queue.php :  $this->detail = 'stat_report_detail';

**************************************************************************************
统计分离：
建立：data_sys_stat数据库：
字符集：utf8 -- UTF-8 Unicode
排序规则：utf8_general_ci

***********************************************************************************************
项目管理：
source /home/wanghaidong/AP2/install/serverSrc/label/tools/pro/pro.sql
pro_firm_list：业务项目组列表
pro_project_list：项目列表
pro_project_data：项目
pro_project_proc：项目-项目组
pro_project_sec：项目-乙方






**************************************************************************************
第三方库
ImageMagick:
git clone https://github.com/ImageMagick/ImageMagick.git
./configure --prefix=/home/ubuntu/git/DFS/third/ImageMagick
make -j && make install
http://blog.csdn.net/wdjhzw/article/details/43031449

libpng
wget http://prdownloads.sourceforge.net/libpng/libpng-1.5.4.tar.gz
./configure --prefix=/home/ubuntu/git/DFS/third/libpng
make -j8 & make install


**************************************************************************************
代码更新：
/home/wanghaidong/AP2/server/www/datasys/conf 目录下全部保留  chmod -R 444 *.php
chmod 444 /home/wanghaidong/AP2/server/www/datasys/lib/conf.php
cp -r datasys/ /home/wanghaidong/AP2/server/www  显示权限不够就对了
git clone http://phint.horizon-robotics.com/diffusion/LABEL/label.git

redis连接异常导致整个系统崩溃

update rbac_group_role set status=0;
update rbac_group set status=0;
update data_ver_list set is_del=0;

http://10.19.19.23:8200/datasys/data/res/delete/?lists=[51]

http://10.19.19.23:8200/web/html-user/users_list.html
用户组列表第一页和第二页返回的结果是一样的

创建用户组没有权限，显示500


代码更新：
./lib/conf.php改为只读权限


PHPstorm
注册（PhpStorm-2017.1.4.exe）：
打开：http://idea.lanyus.com/
为避免phpstorm联网时注册失效，请将“0.0.0.0 account.jetbrains.com”添加到hosts文件中：C:\Windows\System32\drivers\etc     hosts
注册码获取（http://idea.lanyus.com/）：
BIG3CLIK6F-eyJsaWNlbnNlSWQiOiJCSUczQ0xJSzZGIiwibGljZW5zZWVOYW1lIjoibGFuIHl1IiwiYXNzaWduZWVOYW1lIjoiIiwiYXNzaWduZWVFbWFpbCI6IiIsImxpY2Vuc2VSZXN0cmljdGlvbiI6IkZvciBlZHVjYXRpb25hbCB1c2Ugb25seSIsImNoZWNrQ29uY3VycmVudFVzZSI6ZmFsc2UsInByb2R1Y3RzIjpbeyJjb2RlIjoiQUMiLCJwYWlkVXBUbyI6IjIwMTctMTEtMjMifSx7ImNvZGUiOiJETSIsInBhaWRVcFRvIjoiMjAxNy0xMS0yMyJ9LHsiY29kZSI6IklJIiwicGFpZFVwVG8iOiIyMDE3LTExLTIzIn0seyJjb2RlIjoiUlMwIiwicGFpZFVwVG8iOiIyMDE3LTExLTIzIn0seyJjb2RlIjoiV1MiLCJwYWlkVXBUbyI6IjIwMTctMTEtMjMifSx7ImNvZGUiOiJEUE4iLCJwYWlkVXBUbyI6IjIwMTctMTEtMjMifSx7ImNvZGUiOiJSQyIsInBhaWRVcFRvIjoiMjAxNy0xMS0yMyJ9LHsiY29kZSI6IlBTIiwicGFpZFVwVG8iOiIyMDE3LTExLTIzIn0seyJjb2RlIjoiREMiLCJwYWlkVXBUbyI6IjIwMTctMTEtMjMifSx7ImNvZGUiOiJEQiIsInBhaWRVcFRvIjoiMjAxNy0xMS0yMyJ9LHsiY29kZSI6IlJNIiwicGFpZFVwVG8iOiIyMDE3LTExLTIzIn0seyJjb2RlIjoiUEMiLCJwYWlkVXBUbyI6IjIwMTctMTEtMjMifSx7ImNvZGUiOiJDTCIsInBhaWRVcFRvIjoiMjAxNy0xMS0yMyJ9XSwiaGFzaCI6IjQ3NzU1MTcvMCIsImdyYWNlUGVyaW9kRGF5cyI6MCwiYXV0b1Byb2xvbmdhdGVkIjpmYWxzZSwiaXNBdXRvUHJvbG9uZ2F0ZWQiOmZhbHNlfQ==-iygsIMXTVeSyYkUxAqpHmymrgwN5InkOfeRhhPIPa88FO9FRuZosIBTY18tflChACznk3qferT7iMGKm7pumDTR4FbVVlK/3n1ER0eMKu2NcaXb7m10xT6kLW1Xb3LtuZEnuis5pYuEwT1zR7GskeNWdYZ0dAJpNDLFrqPyAPo5s1KLDHKpw+VfVd4uf7RMjOIzuJhAAYAG+amyivQt61I9aYiwpHQvUphvTwi0X0qL/oDJHAQbIv4Qwscyo4aYZJBKutYioZH9rgOP6Yw/sCltpoPWlJtDOcw/iEWYiCVG1pH9AWjCYXZ9AbbEBOWV71IQr5VWrsqFZ7cg7hLEJ3A==-MIIEPjCCAiagAwIBAgIBBTANBgkqhkiG9w0BAQsFADAYMRYwFAYDVQQDDA1KZXRQcm9maWxlIENBMB4XDTE1MTEwMjA4MjE0OFoXDTE4MTEwMTA4MjE0OFowETEPMA0GA1UEAwwGcHJvZDN5MIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEAxcQkq+zdxlR2mmRYBPzGbUNdMN6OaXiXzxIWtMEkrJMO/5oUfQJbLLuMSMK0QHFmaI37WShyxZcfRCidwXjot4zmNBKnlyHodDij/78TmVqFl8nOeD5+07B8VEaIu7c3E1N+e1doC6wht4I4+IEmtsPAdoaj5WCQVQbrI8KeT8M9VcBIWX7fD0fhexfg3ZRt0xqwMcXGNp3DdJHiO0rCdU+Itv7EmtnSVq9jBG1usMSFvMowR25mju2JcPFp1+I4ZI+FqgR8gyG8oiNDyNEoAbsR3lOpI7grUYSvkB/xVy/VoklPCK2h0f0GJxFjnye8NT1PAywoyl7RmiAVRE/EKwIDAQABo4GZMIGWMAkGA1UdEwQCMAAwHQYDVR0OBBYEFGEpG9oZGcfLMGNBkY7SgHiMGgTcMEgGA1UdIwRBMD+AFKOetkhnQhI2Qb1t4Lm0oFKLl/GzoRykGjAYMRYwFAYDVQQDDA1KZXRQcm9maWxlIENBggkA0myxg7KDeeEwEwYDVR0lBAwwCgYIKwYBBQUHAwEwCwYDVR0PBAQDAgWgMA0GCSqGSIb3DQEBCwUAA4ICAQC9WZuYgQedSuOc5TOUSrRigMw4/+wuC5EtZBfvdl4HT/8vzMW/oUlIP4YCvA0XKyBaCJ2iX+ZCDKoPfiYXiaSiH+HxAPV6J79vvouxKrWg2XV6ShFtPLP+0gPdGq3x9R3+kJbmAm8w+FOdlWqAfJrLvpzMGNeDU14YGXiZ9bVzmIQbwrBA+c/F4tlK/DV07dsNExihqFoibnqDiVNTGombaU2dDup2gwKdL81ua8EIcGNExHe82kjF4zwfadHk3bQVvbfdAwxcDy4xBjs3L4raPLU3yenSzr/OEur1+jfOxnQSmEcMXKXgrAQ9U55gwjcOFKrgOxEdek/Sk1VfOjvS+nuM4eyEruFMfaZHzoQiuw4IqgGc45ohFH0UUyjYcuFxxDSU9lMCv8qdHKm+wnPRb0l9l5vXsCBDuhAGYD6ss+Ga+aDY6f/qXZuUCEUOH3QUNbbCUlviSz6+GiRnt1kA9N2Qachl+2yBfaqUqr8h7Z2gsx5LcIf5kYNsqJ0GavXTVyWh7PYiKX4bs354ZQLUwwa/cG++2+wNWP+HtBhVxMRNTdVhSm38AknZlD+PTAsWGu9GyLmhti2EnVwGybSD2Dxmhxk3IPCkhKAK+pl0eWYGZWG3tJ9mZ7SowcXLWDFAk0lRJnKGFMTggrWjV8GYpw5bq23VmIqqDLgkNzuoog==


安装PHP扩展Imagick
class not exists:Imagick
/home/wanghaidong/AP2/softwares/extension
安装jpeg8
wget http://www.ijg.org/files/jpegsrc.v8d.tar.gz
./configure --prefix=/home/wanghaidong/AP2/softwares/extension/jpeg-8d/jpeg-8d
make -j && make install
安装ImageMagick
wget http://www.imagemagick.org/download/ImageMagick.tar.gz
./configure --prefix=/home/wanghaidong/AP2/softwares/extension/ImageMagick-7.0.6-4/ImageMagick-7.0.6-4  --x-includes=/home/wanghaidong/AP2/softwares/extension/jpeg-8d/jpeg-8d/include --x-libraries=/home/wanghaidong/AP2/softwares/extension/jpeg-8d/jpeg-8d/lib
make -j && make install
安装imagick-3.4.3
wget http://pecl.php.net/get/imagick-3.4.3.tgz
/home/wanghaidong/AP2/softwares/php-5.6.30/bin/phpize
./configure  --with-php-config=/home/wanghaidong/AP2/softwares/php-5.6.30/bin/php-config --with-imagick=/home/wanghaidong/AP2/softwares/extension/ImageMagick-7.0.6-4/ImageMagick-7.0.6-4/include
error: ‘struct _php_core_globals’ has no member named ‘safe_mode’（imagick-3.1.0b1改用imagick-3.4.3解决）
make && make install
PHP加入扩展
vi /home/wanghaidong/AP2/softwares/php-5.6.30/lib/php.ini
extension=imagick.so


发邮件
Q: invalid SSL_version specified at /usr/share/perl5/vendor_perl/IO/Socket/SSL.pm line 415.
A: just changed sendEmail line 1 from #!/usr/bin/perl -w to #!/usr/bin/perl5.12 -w
#!/usr/bin/perl -w
#!/home/fastdb/softwares/perl-5.10.0/perl-5.10.0/bin/perl -w





安装jpeg9
wget http://www.ijg.org/files/jpegsrc.v9b.tar.gz
./configure --prefix=/home/wanghaidong/AP2/softwares/extension2/jpeg-9b/jpeg-9d
make -j && make install
安装ImageMagick
wget https://www.imagemagick.org/download/ImageMagick.tar.gz
./configure --prefix=/home/wanghaidong/AP2/softwares/extension2/ImageMagick-7.0.6-6/ImageMagick-7.0.6-6  --x-includes=/home/wanghaidong/AP2/softwares/extension2/jpeg-9b/jpeg-9d/include --x-libraries=/home/wanghaidong/AP2/softwares/extension2/jpeg-9b/jpeg-9d/lib
make -j && make install
安装imagick-3.4.3
wget https://pecl.php.net/get/imagick-3.4.3.tgz
/home/wanghaidong/AP2/softwares/php-5.6.30/bin/phpize
./configure  --with-php-config=/home/wanghaidong/AP2/softwares/php-5.6.30/bin/php-config --with-imagick=/home/wanghaidong/AP2/softwares/extension2/ImageMagick-7.0.6-6/ImageMagick-7.0.6-6/include
error: ‘struct _php_core_globals’ has no member named ‘safe_mode’（imagick-3.1.0b1改用imagick-3.4.3解决）
make && make install
PHP加入扩展
vi /home/wanghaidong/AP2/softwares/php-5.6.30/lib/php.ini
extension=imagick.so

PHP Warning:  PHP Startup: Unable to load dynamic library '/home/wanghaidong/AP2/softwares/php-5.6.30/lib/php/extensions/no-debug-non-zts-20131226/imagick.so' - /lib64/libjpeg.so.62: version `LIBJPEG_6.2' not found (required by /lib64/libtiff.so.5) in Unknown on line 0

通过查看libjpeg.so.62，发现其链接指向libjpeg.so.62.1.0，初步怀疑是小版本的问题。
通过将其它服务器上的libjpeg.so.62.0.0拷贝到本机/usr/lib64，并重新做链接，问题得以解决。






拷贝data_sys数据库
mysql -uroot -pa5300066 -h10.19.19.23 -P3319
CREATE DATABASE 'data_sys_master' DEFAULT CHARACTER SET UTF8 COLLATE UTF8_GENERAL_CI;
`要用键盘Esc下的那个，而不是单引号，否则出错；
DEFAULT CHARACTER SET utf8：数据库字符集。设置数据库的默认编码为utf8，这里utf8中间不要"-"；
COLLATE utf8_general_ci:数据库校对规则，ci是case insensitive的缩写，意思是大小写不敏感；相对的是cs，即case sensitive，大小写敏感；还有一种是utf8_bin，是将字符串中的每一个字符用二进制数据存储，区分大小写。
整理如下：
    utf8_bin：区分大小写；
    utf8_general_cs：大小写敏感；
    utf8_general_ci：大小写不敏感。
mysqldump data_sys -u root -pa5300066 --add-drop-table | mysql data_sys_master -u root -pa5300066;  是操作系统下命令，不是在 mysql 命令行中使用的。

导出数据库：
$conf = array(
    'default' => array(
        'DB_HOSTS' => '10.19.19.23:8798',
        'DB_USERNAME' => 'dongmin',
        'DB_PWD' => '1234',
        'DB_DATABASE' => 'data_sys',
    ),
);
mysqldump -u 用户名 -p 数据库名 > 导出的文件名
mysqldump -udongmin -p1234 -h10.19.19.23:8798 > backup.sql


redis_6393.conf
port 6393



fastdfs-php client
wget https://github.com/happyfish100/fastdfs/archive/master.zip
unzip master.zip
/home/wanghaidong/AP2/softwares/php-5.6.30/bin/phpize
./configure --with-php-config=/home/wanghaidong/AP2/softwares/php-5.6.30/bin/php-config

extension=fastdfs_client.so
fastdfs_client.base_path = /home/wanghaidong/AP2/log/fastdfs
fastdfs_client.connect_timeout = 2
fastdfs_client.network_timeout = 60
fastdfs_client.log_level = info
fastdfs_client.log_filename =
fastdfs_client.http.anti_steal_secret_key =
fastdfs_client.tracker_group_count = 1
fastdfs_client.tracker_group0 = /etc/fdfs/client.conf
fastdfs_client.use_connection_pool = false
fastdfs_client.connection_pool_max_idle_time = 3600


***************
环境变量配置
**********************
压缩文件存放位置（提供给Nginx向外提供文件下载服务）：resdown.php:15:    'tmppath' => '/home/wanghaidong/AP2/tmp'



下载没有成功，也没有日志，cmd执行没有任何反应
原因是配置了log目录 /home/yaorui/yali/log/rawlog/
但是没有新建rawlog目录 只到/home/yaorui/yali/log

Q：数据下发只下发一张图片
A：上传的原始数据每一个文件夹一张图片作为一批

Q：新建项目绑定数据，结果数据状态一直为0
A：没有同步lib/comm/procprocess.php
结果数据状态由0变为2是由script/proc/gendata.php完成


