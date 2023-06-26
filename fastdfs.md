
降低最大连接数目报错：
[2017-10-12 17:03:11] ERROR - file: tracker_nio.c, line: 140, malloc task buff failed, you should increase the parameter: max_connections

达到系统的最大连接数目：
ERROR - file: connection_pool.c, line: 130, connect to 10.19.19.22:23000 fail, errno: 99, error info: Cannot assign requested address

[2017-10-12 13:56:52] ERROR - file: tracker_service.c, line: 2452, cmd=102, client ip: 10.19.19.24, package size 16 is not correct, expect length > 38
如果storage server是最新版本了，貌似tracker server不是最新版。
总之，应该是storage和tracker的版本不匹配导致的问题。


tracker.conf
max_connections=4096
accept_threads=64
work_threads=512
(
max_buff_size = 1024KB
thread_stack_size = 256KB
)

use_connection_pool = true


storage.conf
max_connections=2048
(buff_size = 1024KB)
accept_threads=16
work_threads=64
disk_reader_threads = 16
disk_writer_threads = 16
(thread_stack_size=4096KB)

use_connection_pool = true




故障预警（http://www.heminjie.com/system/linux/1923.html）：
notification_email()
{
    emailuser='nongfugengxia@163.com'
    emailpasswd='donghaiwang.1'
    emailsmtp='smtp.163.com'
    sendto='haidong.wang@hobot.cc'
    title='Disk Space Alarm'
    /data/sdb/git/monitor/sendEmail-v1.56/sendEmail -f $emailuser -t $sendto -s $emailsmtp -u $title -xu $emailuser -xp $emailpasswd
}

while :
do
        stillRunning=$(ps -ef |grep "serverMain" |grep -v "grep")
        if [ "$stillRunning" ] ; then
                echo "service was already started"
        else
                echo "service was not started"
                echo -e "test" | notification_email
                sleep 3600
        fi
        sleep 10
done

******************************************************************************************************************
#!/bin/sh 
# 实现服务崩溃后自动重启
# 后台启动脚本命令：nohup  ./start.sh > server.out 2>&1 &
#=====================
# haidong.wang 
#===================== 
while :  
do 
    echo "Current DIR is " $PWD 
    stillRunning=$(ps -ef |grep "$PWD/serverMain" |grep -v "grep") 
    if [ "$stillRunning" ] ; then 
        echo "TWS service was already started by another way" 
        echo "Kill it and then startup by this shell, other wise this shell will loop out this message annoyingly" 
        kill -9 $pidof $PWD/serverMain 
    else 
        echo "TWS service was not started" 
    echo "Starting service ..." 
    $PWD/serverMain 
    echo "TWS service was exited!" 
    fi 
    sleep 1 
done 



需求：
group中的一个storage不可恢复的挂了，原来访问这个IP地址的数据访问不到。
重新搭建一个相同IP地址的storage并同步数据。

数据迁移：
http://10.19.19.23:18093/

/data/sdb/release/softwares/nginx-1.7.9/logs
[2017-06-24 17:25:42] ERROR - file: ../storage/trunk_mgr/trunk_shared.c, line: 177, "No such file or directory" can't be accessed, error info: /data/sdb/release/softwares/nginx-1.7.9_2/logs

test1/M00/00/00/ChMTF1lOMXGAQJZxAAca_JuuunI6395913***haidong.wang***59748A23C0109D11387CAF69C8255B4A

cp fastdfs-nginx-module/src/mod_fastdfs.conf fastdfs-5.05/conf/
vi fastdfs-5.05/conf/mod_fastdfs.conf 

./configure --prefix=/data/sdk/testEnv/softwares/nginx-1.7.9_1 --add-module=/data/sdk/testEnv/install/softwares/fastdfs-nginx-module/src/


configure: error: xml2-config not found. Please check your libxml2 installation.
--with-xml-dir=/usr/lib/

PHP (tar zxvf php-5.6.30.tar.gz)
**************************************************************************************
./configure --prefix=/data/sdb/release/softwares/release/php-5.6.30 --enable-fpm --with-fpm-user=www --with-fpm-group=www --with-mysql=mysqlnd --with-mysqli=mysqlnd --with-pdo-mysql=mysqlnd --with-iconv-dir --with-freetype-dir --with-jpeg-dir --with-png-dir --with-zlib --disable-rpath --enable-bcmath --enable-shmop --enable-sysvsem --enable-inline-optimization --with-curl --enable-mbregex --enable-mbstring --with-gd --enable-gd-native-ttf --with-openssl --with-mhash --enable-pcntl --enable-sockets --enable-zip --enable-soap --without-pear

make -j8 && make install

cp ./etc/php-fpm.conf.default ./etc/php-fpm.conf

vi ./etc/php-fpm.conf
listen = 127.0.0.1:9013  （改为9014）

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




系统驱动：
读取系统配置文件 DFS.conf

读取FastDFS客户端的配置文件 client.conf
提前为下载所需要的buffer申请内存
内存池开源：
https://github.com/dcshi/ncx_mempool
(https://github.com/imiskolee/mempool)



encrypt
http://www.cnblogs.com/sunxuchu/p/5483956.html


linux中无 conio.h的解决方法
http://www.myexception.cn/linux-unix/1728305.html
system("stty -echo");
c=getchar();
system("stty echo");

在线格式转换：http://pic.55.la/




Client
报错 linux-x86-64......
因为删除了fdfsClient中的main函数，所以Makefile.in中的ALL_PRGS也需要删除fdfsClient

调用另一个.c文件中的函数（调用上传函数）：
1. 将int main(int argc, char *argv[])转换成uploadMain(int argc, char *argv[])
2. 增加fdfs_upload_file.h, int uploadMain(int argc, char *argv[]);
3. fdfs_upload_file.c中增加#include "fdfs_upload_file.h"
4. 在使用的地方增加头文件 #include "fdfs_upload_file.h"
5. Makefile.in中增加：FDFS_HEADER_FILES:    fdfs_upload_file.h
                    FDFS_STATIC_OBJS:   fdfs_upload_file.o
                    ALL_PRGS:           fdfsClient(fdfs_upload), 还需要删除fdfs_download_file（不然会出现undefined reference to `main'）

git init
git add .
git commit -m 'first commit'
git remote add master http://phint.horizon-robotics.com/diffusion/DB/distributeddb.git
git push master master



download file fail, error no: 22, error info: Invalid argument
下载: group1/M00/0F/A8/ChMTF1hmD8yAL1TAAAOqFUHPy20457.jpg......, result: 1


FastDFS的API使用解读
http://www.oschina.net/question/234345_50735
StorageClient中是将File ID用Group Name和File Name两部分来表示的，而StorageClient1中是将Group Name和File Name统一起来处理的。其实通过分析FastDFS Java Client的源码可以发现，StorageClient1是StorageClient的一个子类


将文件读取转化为内存数据的传递
编写测试用例，调用.so
测试业务层和存储层（加公共模块）的功能

部署到服务器上
编写Socket程序提供服务，进行Socket连接进行测试



占用内存空间较大的局部数组声明的前面加static将其从堆栈数据段挪到全局数据段
堆栈大小默认1MB
可以在链接选项中改大。
申请内存数量的值保存在内存块首地址前0x10的位置，即首地址前第16个字节的位置



C语言
decryptedFileID = strtok( decryptedFileID, delims );    // 解密后真正的fileID
char * decryptedUserName = strtok(NULL, delims);        // 解密后真正的userName
在第一次调用时，strtok()必需给予参数s 字符串，往后的调用则将参数s 设置成NULL。每次调用成功则返回下一个分割后的字符串指针
printf("%s ", strtok(s, delim));
while((p = strtok(NULL, delim)))
    printf("%s ", p);
    printf("\n");
    
  
int main()  
{  
    char str[]="ab,cd,ef";  
    char *ptr;  
    printf("before strtok:  str=%s\n",str);  
    printf("begin:\n");  
    ptr = strtok(str, ",");  
    while(ptr != NULL){  
        printf("str=%s\n",str);  
        printf("ptr=%s\n",ptr);  
        ptr = strtok(NULL, ",");  
    }  
    system("pause");  
    return 0;  
}  




Nginx增加请求时间日志： 
log_format  main  '$remote_addr - $remote_user [$time_local] "$request" '
                      '$status $body_bytes_sent "$http_referer" '
                      '"$http_user_agent" "$http_x_forwarded_for" "$request_time" ';

    access_log  logs/access.log  main;

10.98.35.191 - - [22/Jun/2017:09:54:15 +0800] "GET /action.php?fileID=GQwRCw5PUTNOTVFGR1FPTVE9FjMqOBISNTJJMT8sSwYTPz8YOgg6PxNMDQlPR05HTUtM&dueTime=T0pHRk5HSUZNSw==?1498096437482 HTTP/1.1" 200 508994 "http://10.19.19.24/web/tools/dist/point/index.html?



cd php-7.0.4/
ls
vim etc/php-fpm.d/www.conf
ps aux | grep php-fpm | grep fast
kill -USR2 15473
ps aux | grep php-fpm | grep fast
history 30

; The number of child processes to be created when pm is set to 'static' and the
; maximum number of child processes when pm is set to 'dynamic' or 'ondemand'.
; This value sets the limit on the number of simultaneous requests that will be
; served. Equivalent to the ApacheMaxClients directive with mpm_prefork.
; Equivalent to the PHP_FCGI_CHILDREN environment variable in the original PHP
; CGI. The below defaults are based on a server without much resources. Don't
; forget to tweak pm.* to fit your needs.
; Note: Used when pm is set to 'static', 'dynamic' or 'ondemand'
; Note: This value is mandatory.
pm.max_children = 100

; The number of child processes created on startup.
; Note: Used only when pm is set to 'dynamic'
; Default Value: min_spare_servers + (max_spare_servers - min_spare_servers) / 2
pm.start_servers = 30

; The desired minimum number of idle server processes.
; Note: Used only when pm is set to 'dynamic'
; Note: Mandatory when pm is set to 'dynamic'
pm.min_spare_servers = 30

; The desired maximum number of idle server processes.
; Note: Used only when pm is set to 'dynamic'
; Note: Mandatory when pm is set to 'dynamic'
pm.max_spare_servers = 100



重启tracker 
脚本参数1 脚本参数2 
/usr/local/bin/.restart.sh /usr/local/bin/fdfs_trackerd /etc/fdfs/tracker.conf

重启storage 
脚本参数1 脚本参数2 
/usr/local/bin/.restart.sh /usr/local/bin/fdfs_storaged /etc/fdfs/storage.conf