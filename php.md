

phpadmin: 搜索，全选，导出指定条件的sql

date('w')==0  周日
定期进行optimize
optimize table ad_visit_history;
当你删除数据时，mysql并不会回收，被已删除数据的占据的存储空间，以及索引位。而是空在那里，而是等待新的数据来弥补这个空缺，这样就有一个缺少，如果一时半会，没有数据来填补这个空缺，那这样就太浪费资源了。

flock()
LOCK_SH 共享锁（读取）
LOCK_EX 排它锁（写入）exclusive
LOCK_UN 释放锁定
LOCK_NB 在flock()锁定时不阻塞


phpdoc (https://github.com/phpDocumentor/phpDocumentor2)
wget http://pear.php.net/go-pear.phar
pear channel-discover pear.phpdoc.org
pear install phpdoc/phpDocumentor

phpdoc run -d /home/wanghaidong/ap2/datasystem-server/www/datasys/logic/third -t /home/wanghaidong/ap2/tmp/phpdoc
http://10.19.19.23:8200/tmp/phpdoc/index.html
http://10.19.19.23:8200/tmp/phpdoc/classes/Logic_third_task.html

phpdoc -h
phpdoc template:list

win10安装：https://www.cnblogs.com/ryanlamp/p/4769471.html
phpdoc run -d F:\git\datasystem-server\www\datasys\logic\third -t F:\tmp1\phpdoc

PHP Fatal error:  Class 'DOMDocument' not found
yum install php-xml


LNMP(Linux,Niginx, Mysql, PHP) + fastdfs,HDFS
前端看懂、redis
Linux C/C++
Python DL (自然语言处理、图像）
表达

Lib_Comm_Log::write('MONITOR','todolist_err_back_secondary',[var_export($record, true),var_export($backSeqRecord, true)]);
var_export第二个参数为TRUE时，有返回值

轮询：
//        $verList = new Model_data_verlist();
//        $ret = $verList->view(array('raw' => intval($rawId)));      // 查找ver_list中对应raw的所有记录
//        while ($ret[0]['id'] == NULL) {
//            $ret = $verList->view(array('raw' => intval($rawId)));
//            sleep(1);       // 上传队列uploadQueue压入redis队列，等待其处理完
//        }
//        $verList->update(array('id' => intval($ret[0]['id']), 'hdfs' => $backupItem));


配置文件少了","逗号，require失败报错。

array_map和array_walk的使用对比
map    主要是为了得到你的回调函数处理后的新数组，要的是结果。
walk   主要是对每个参数都使用一次你的回调函数，要的是处理的过程。
walk   可以认为提供额外参数给回调函数，map不可以

walk   主要是要对数组内的每个值进行操作，操作结果影响原来的数组
map    主要是对数组中的值进行操作后返回数组，以得到一个新数组
walk   可以没有返回值 map要有，因为要填充数组
 
 

PDO(PHP Data Object) 

lt = Less Than = 小于 
gt = Great Than = 大于



Debug session was finished without being paused
        It may be caused by path mappings misconfiguration or not synchronized local and remote projects.
        To figure out the problem check path mappings configuration for 'localhost' server at PHP|Servers or enable Break at first line in PHP scripts option (from Run menu).
        Do not show again
运行没有停止，调试会话就停止了，可能是没有设置断点。


开始：
$stime=microtime(true);
结束：
$etime=microtime(true);//获取程序执行结束的时间
$total=$etime-$stime;  //计算差值
echo "<br />当前页面执行时间为：{$total} 秒";exit;

执行效率log记录
$t1 = microtime(true);
$t2 = microtime(true);
file_put_contents("/home/yaorui/yali/datasystem-server/www/datasys/logic/data/log", ($t2-$t1) . PHP_EOL, FILE_APPEND);

ab -n 1000 -c 100 http://10.19.19.23:8200/datasys/pro/project/slaveview/


XDebug远程调试（http://www.51testing.com/html/18/170218-3538738.html）
wget https://xdebug.org/files/xdebug-2.3.2.tgz
/home/wanghaidong/AP2/softwares/php-5.6.30/bin/phpize
./configure --enable-xdebug --with-php-config=/home/wanghaidong/AP2/softwares/php-5.6.30/bin/php-config
make & make install

vi /home/wanghaidong/AP2/softwares/php-5.6.30/lib/php.ini
zend_extension="/home/wanghaidong/AP2/softwares/php-5.6.30/lib/php/extensions/no-debug-non-zts-20131226/xdebug.so"
[xdebug]
xdebug.idekey=PHPSTORM
xdebug.remote_connect_back = 1
xdebug.remote_host=10.129.157.29
xdebug.remote_enable=on
xdebug.remote_port = 9001
xdebug.remote_handler = dbgp
xdebug.auto_trace = 1
xdebug.collect_includes = 1
xdebug.collect_params = 1
xdebug.collect_return = 1
xdebug.default_enable = 1
xdebug.collect_assignments = 1
xdebug.collect_vars = 1
xdebug.remote_autostart = 1
xdebug.show_local_vars = 1
xdebug.show_exception_trace = 0
注意：不需要重启php-fpm就php -m里就有xdebug，但是仍需要冲洗php-fpm才会生效。

远程调试接口特别卡
;xdebug.remote_connect_back = 1
设置了这个参数之后，xdebug返回数据时就不会只返回给xdebug.remote_host参数设置的IP了，任何ip请求都会返回数据，这样就可以多人共享这台服务器的php xdebug环境了
vi lib/php.ini
xdebug.remote_host=10.64.39.68  (设置成ipconfig中WLAN的ipv4地址)10.19.19.23能够ping通10.64.39.68


重启php-fpm
ps aux | grep php-fpm | grep wanghai | awk '{print $2}' | xargs kill -s 9
/home/wanghaidong/AP2/softwares/php-5.6.30/sbin/php-fpm

激活PHPstorm:http://idea.lanyus.com/

配置PhpStorm中的 XDebug
File -> Settings -> Languages&Frameworks -> PHP -> Debug -> Debug port:9001

配置PhpStorm中的 Server
File -> Settings -> Languages&Frameworks -> PHP -> Servers -> 向右箭头(Import From Deployment Configuration) 
    -> Deployment:wanghaidong; Host:10.19.19.23; Port:8200; Use path mappings; 
    
设置调试项
Run -> Edit Configurations -> 单击左上角"+"按钮 -> PHP Web Application; Server:wanghaidong; Start URL:http://10.19.19.23:8200/datasys/data/res/retrive/?limit=0&raw=508

开始调试: Alt+Shift+D
F5：Step Into
F6：Step Over
F7：Step Out

打开指定文件：Ctrl+Shift+R


工程后面增加自动保存同步功能：
1. 添加一个FTP服务器：Tools -> Deployment -> Configuration
2. 打开设置界面，设置为Always或On explicit save action，最后OK即可

参考：
http://www.cnblogs.com/52php/p/5677839.html
http://www.51testing.com/html/18/170218-3538738.html

1. 增加git, 使用local的git，先保证能git clone ssh://
ssh-keygen -t rsa -b 4096 -C "1402499358@qq.com"
ssh-keygen -t rsa -b 4096 -C "haidong.wang@hobot.cc
ssh-keygen -t rsa -f ~/.ssh/id_rsa.github -C "1402499358@qq.com"
PhpStorm:
ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAACAQCw31YvL1PfkTwChzwJ4wCFhvDbG+hZ5V7UBon2dTlw4CQPN+Yo6cuVDu9HknXnn2rYwNAXWYYtQJbsqaQAlonvOQvOT0FYKX/eHzzDdkiB0hGf2zKgUm8LDuBAh+6cPX7p99LoeJUqqa3Q/M7UroH5fcnpH6y94rx47phK54+WUipG5SyvGGXaTPxRdiqGhuFrkatWq2xV1jvf2nX8HPMj5ctEm1kG+/erd16iedQK3ddPA5GFW5muyV+Gu9VYgKfNy1xM2ASrh8zUmAt3EM3wMiFtSZmm1LDbl6DtoMsLA1JQNllF51tw6wucjqON09U3hrWO63SONR/N4IjQNZNovzEypxBGF9fRMvkouT1caf7hBMc4WHWJ/7StD09tnY4FX63C1W0hwF5U3GIqOsO5qh6/Hh4XGUku/Svog8ZdPG3NKK+6lTRvZ63zUfUwDvPG3UkLX4XVWXiIfcguqXM9mN+l5lLll8Ksw/GCCPZEe4ehRW+dRQkx2FxaI4KYU2Woct60vxiua17ZWXN45Nfc3KO5zPp5n4vDzKd02wmTkxeFP5BwBoLqdbtbuyBxfV4wGYYsU70Pz0n0CMaBhM1jVuNRJ4TNiR7+NaOchdYrEWACGVdTQsmtoIaNnQ5wwYo3EjOivpiqEynrlFinToNfXpwgUy4l9gjLu87rxQpDfw== haidong.wang@hobot.cc
原来win10:
ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDIas9NkgM2+n6l49eIiGagvZMHYcKkv6p8RIUk7/0cJRaGbSJvxB9HzeLUD2W2KYocCLZrNUaCrlg+N0Np4qnx8lq+N70HOia49OaF3ZUyVuU3A284aywpbZJN/LE8eGMJvKdiop115TSb7SLn2USesrYIW7ySJd4NJszmI2txYk3LsRcYI4XB+VdqTbqzWd2XvrgAxgQHX49WeYaGq56r87Py64NhJgiO7euLGvrrhnQdri8HlS9GwzWcnfWVFz92BVjJbHZy+mQ14wHLRPHsWgAoXymTTou6xneNwDKpCKoRmKbS3I58HCv3Sb6KtGcsuiwvQlTKlQvPvaS2JMxb haidong.wang@hobot.cc

新建~/.ssh/config并按以下格式配置
Host ph.hobot.cc
    IdentityFile ~/.ssh/id_rsa.ph
    User wanghaidong

Host github.com
    IdentityFile ~/.ssh/id_rsa.github
    User donghaiwang

ssh -T git@github.com
ssh -T git@ph.hobot.cc

出现：phabricator-ssh-exec: Invalid command. fatal: Could not read from remote repository.
重新安装ph解决

2. 本地与远程进行同步, ctrl+s


清空当前缓冲区的数据: ob_clean();
flush();exit;
conf/redis.php末尾有空格


浏览器强制刷新：Ctrl+Shift+R
更新了前端代码，浏览器缓存了旧的JS。


lib/rbac/user.php
$this->session = \DTS::$app->session;
    $dbconf = \Lib_Comm_Conf::get(\Lib_Conf::REDIS_CONF);
$this->userObj = \datasys\model\Model_User::getInstance();




Chrome添加Edit This Cookie插件
增加cookie调试（不影响线上环境）
if ($_COOKIE['PHPSESSID'] == 'debug') {
    echo "debug";exit();
}


require 生成一个致命错误（E_COMPILE_ERROR），在错误发生后脚本会停止执行。
include 生成一个警告（E_WARNING），在错误发生后脚本会继续执行。


PHP_EOL: End Of Line
Leap year:闰年


PHPStorm:
远程开发
http://annn.me/webstorm-phpstorm-remote-host/
注意：Project name为主机名（执行hostname）；
server Name 为主机名
指定远程主机的根目录，需要点击Project Root才能下一步；
Q: HEAD method failed for
A: Try to check "Don't check http connection".

显示方法列表：鼠标移到最左下角的正方形，选structure就有了

设置快捷键：File -> Settings -> Apperance -> System Settings -> Keymap -> 选择“Eclipse” -> 然后“Copy”一份 -> 再个性化设置

ctrl+shift+alt+n, 查找函数
右键点击方法名 选择finder useage(Ctrl+G)



Git
"clone failed. Could not read from remote repository".
ssh://git@ph.hobot.cc/diffusion/DATASYSTEMIISERVER/datasystem-server.git





http://127.0.0.2:8080/action.php?fileID=BkdcRUABGXtRBhwBMB82ck52W31kdgdfUGVgAnFSZlI3dHJTUW90AydmQzAHBQICVQwD&dueTime=UAELCAYBDwJZAg==

SDK: 
输入：group1/M03/10/6D/ChMTF1i1PS2AbPdVAAca_B5FSp07544490***haidong.wang***59748A23C0109D11387CAF69C8255B4A、30
输出：http://127.0.0.2:8080/action.php?fileID=group1/M03/10/6D/ChMTF1i1PS2AbPdVAAca_B5FSp07544490&deadLine=2488510148（加密）


PHP(Nginx)：
以post的方式提交至：http://10.19.19.23:8080/action.php
POST内容：（解密）http://10.19.19.23:8080/group1/M03/10/6D/ChMTF1i1PS2AbPdVAAca_B5FSp07544490***2488510148
返回图片： echo file_get_contents($imagesURL);


测试nginx响应时间：
netstat -apn | grep 8080
http://10.19.19.23:8080/group1/M03/10/6D/ChMTF1i1PS2AbPdVAAca_B5FSp07544490
注意：必须停止服务再改动配置文件，不然停止服务会失败。
23服务停止，会自动切换到22上去访问文件。


<pre>
file ID： <?php echo $_POST["fileID"]; ?>!<br>
limited time： <?php echo $_POST["limitedTime"]; ?> second.。

Warning: Cannot modify header information - headers already sent by (output started at
修改：只echo一个


建议使用php扩展，不要使用纯PHP版本的客户端API。


**************************************************************************************
Mysql :
mysql -u root -pubuntu

phpmyadmin密码：ubuntu

Redis:
sudo apt-get install redis-server
ps -aux|grep redis
netstat -nlt | grep 6379
sudo /etc/init.d/redis-server status
redis-cli
set key1 "hello"
get key1

**************************************************************************************
PHP:
23: /data/sdj/group1_2/php-7.0.4/sbin

需要到服务器上重新编译PHP
./configure --prefix=/home/ubuntu/nginx/php-7.0.4/php-7.0.4
--enable-fpm 
--with-fpm-user=www --with-fpm-group=www

make -j8
make install

php-fpm (必须启动)

netstat -apn | grep 9000
ps aux | grep php-fpm

ERROR: failed to open configuration file '/data/sdj/group1_2/php-7.0.4/etc/php-fpm.conf': No such file or directory (2)
cp php-fpm.conf.default php-fpm.conf

ERROR:. No pool defined at least one pool section must be specified in config file 
ERROR: failed to post process the configuration 
solution:   cp www.conf.default www.conf

ERROR: unable to bind listening socket for address '127.0.0.1:9000': Address already in use (98)
solution:   vi www.conf
listen = 127.0.0.1:9009

http://10.19.19.23:8080/action.php?fileID=BkdcRUABGXtRBhwBMB82ck52W31kdgdfUGVgAnFSZlI3dHJTUW90AydmQzAHBQICVQwD&dueTime=UAELCAkBNgFXAw==

**************************************************************************************


nginx
./configure --prefix=
make -j8
make install
启动服务： ./sbin/nginx

location ~ \.php$ {
    root           /home/ubuntu/nginx/php-7.0.4/demo;
    fastcgi_pass   127.0.0.1:9000;
    fastcgi_index  index.php;
   # fastcgi_param  SCRIPT_FILENAME  /scripts$fastcgi_script_name;
    fastcgi_param  SCRIPT_FILENAME  $document_root$fastcgi_script_name;
    include        fastcgi_params;
}

并修改PHP action.php中IP地址从自己获取



*****************************************************
http://blog.csdn.net/ssoul_liu/article/details/51059139
安装完libcommon,fastdfs
fastdfs/php_client/# phpize
./configure --with-php-config=/usr/bin/php-config
make
make install
安装信息：
libtool: install: cp ./.libs/fastdfs_client.so /home/ubuntu/nginx/fastdfs-5.05/php_client/modules/fastdfs_client.so
libtool: install: cp ./.libs/fastdfs_client.lai /home/ubuntu/nginx/fastdfs-5.05/php_client/modules/fastdfs_client.la
libtool: finish: PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/sbin" ldconfig -n /home/ubuntu/nginx/fastdfs-5.05/php_client/modules
----------------------------------------------------------------------
Libraries have been installed in:
   /home/ubuntu/nginx/fastdfs-5.05/php_client/modules

If you ever happen to want to link against installed libraries
in a given directory, LIBDIR, you must either use libtool, and
specify the full pathname of the library, or use the `-LLIBDIR'
flag during linking and do at least one of the following:
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable
     during execution
   - add LIBDIR to the `LD_RUN_PATH' environment variable
     during linking
   - use the `-Wl,-rpath -Wl,LIBDIR' linker flag
   - have your system administrator add LIBDIR to `/etc/ld.so.conf'

See any operating system documentation about shared libraries for
more information, such as the ld(1) and ld.so(8) manual pages.
----------------------------------------------------------------------
Installing shared extensions:     /usr/lib/php5/20121212/


cat fastdfs_client.ini >> /etc/php5/fpm/php.ini


/etc/php5/fpm/php-  .conf

12002
fastcgi_pass   localhost:9000; 指定FastCGI服务器监听端口与地址

NOTICE: PHP message: PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20121212/fastdfs_client.so' - libfdfsclient.so: cannot open shared object file: No such file or directory in Unknown on line 0
[02-Mar-2017 17:10:27] ERROR: An another FPM instance seems to already listen on /var/run/php5-fpm.sock
[02-Mar-2017 17:10:27] ERROR: FPM initialization failed


netstat -an未发现监听9000端口。
查看/var/log/php5-fpm.log一切正常。
随后查看/etc/php5/fpm/pool.d/www.conf，发现listen = /var/run/php5-fpm.sock。
将listen设置为9000,即改成listen=9000
重启php5-fpm与nginx后，恢复。

启动fpm:  /usr/sbin/php5-fpm







gzip -cd php-5.2.17-fpm-0.5.14.diff.gz | patch -d php-5.2.17 -p1
./configure --prefix=/home/ubuntu/nginx/php-5.2.17/php-5.2.17 --enable-fpm
make && make install

编译php5.2.17报错： dereferencing pointer to incomplete type ret = buf->buffer->use;
curl -o php-5.x.x.patch https://mail.gnome.org/archives/xml/2012-August/txtbgxGXAvz4N.txt
patch -p0 -b < ./php-5.x.x.patch

编译安装fastdfs_php_client
../../php-5.2.17/php-5.2.17/bin/phpize
fastdfs-5.05/php_client$ ./configure --with-php-config=/home/ubuntu/nginx/php-5.2.17/php-5.2.17/bin/php-config
make
make install
Installing shared extensions:     /home/ubuntu/nginx/php-5.2.17/php-5.2.17/lib/php/extensions/no-debug-non-zts-20060613/


wapm64
安装完，需要启动wampapache64,wampmysql64服务
<Directory />
    AllowOverride none
    Require all denied
</Directory>






// &&与运算,同真时结果为真,再执行赋值语句$b = $c.否则结果为假
$a = 1;$b = 2;$c = 3;
$a && $b = $c;
echo "a:$a" . PHP_EOL;
echo "b:$b" . PHP_EOL;
echo "c:$c" . PHP_EOL . PHP_EOL;


