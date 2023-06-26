




IP(独立IP)： 即Internet Protocol, 指独立IP数。00:00-24:00内相同IP地址之被计算一次。
　　PV(访问量)： 即Page View,  即页面浏览量或点击量，用户每次刷新即被计算一次。
　　UV(独立访客)：即Unique Visitor, 访问您网站的一台电脑客户端为一个访客。00:00-24:00内 相同的客户端只被计算一次。

统一资源标识符（英语：Uniform Resource Identifier，或URI)是一个用于标识某一互联网资源名称的字符串。



http://10.19.19.23:8100/datasys/data/tag/create/?firm=1&category=数据类型&detail=tessttt
http://10.19.19.23:8100/datasys/data/tag/delete/?lists=[1,5]
http://10.19.19.23:8100/datasys/data/tag/edit/?id=5&category=数据类型&detail=录制
http://10.19.19.23:8100/datasys/data/tag/view/?id=5&category=数据类型&detail=录制&firm=1

http://10.19.19.23:8100/datasys/data/down/view/?raw=1&firm=1

http://10.19.19.23:8100/datasys/data/down/edit/?id=1&comment=tesssst
http://10.19.19.23:8100/datasys/data/down/delete/?lists=[1,2]
http://10.19.19.23:8100/datasys/data/down/apply/?res=5&comment=test
http://10.19.19.23:8100/datasys/data/down/download/?id=3
http://10.19.19.23:8100/datasys/data/down/progress/?id=3

http://10.19.19.23:8100/datasys/data/raw/upload/?firm=1&split=4&tags=[1,3]&comment=test&path=ftp://username:password@10.19.19.23/ftp/&process={%22step%22:20,%22split%22:[{%22name%22:%2220160604_150130.pack%22,%22seg%22:%220%20100%20500%20800%22,%22step%22:15}]}
http://10.19.19.23:8100/datasys/data/raw/progress/?id=5
http://10.19.19.23:8100/datasys/data/raw/view/?comment=tes&tags=[2,4]
http://10.19.19.23:8100/datasys/data/raw/edit/?id=1&tags=[2,3,4]&comment=ttttttst
http://10.19.19.23:8100/datasys/data/raw/delete/?lists=[1,2]

http://10.19.19.23:8100/datasys/data/res/upload/?raw=1&path=ftp://username:password@10.19.19.23/ftp/tmp
http://10.19.19.23:8100/datasys/data/res/progress/?id=13
http://10.19.19.23:8100/datasys/data/res/retrive/?tags=[2,3]&firm=1
http://10.19.19.23:8100/datasys/data/res/view/?res=13
http://10.19.19.23:8100/datasys/data/res/chart/?res=13


error 5
cd /home/wanghaidong/AP2/server/www/datasys/lib/comm
vi vi mysql.php


Mysql: https://www.chenyudong.com/archives/building-mysql-5-6-from-source.html

https://dev.mysql.com/doc/refman/5.6/en/source-configuration-options.html
 -DMYSQL_UNIX_ADDR=file_name   设置监听套接字路径
The Unix socket file path on which the server listens for socket connections. This must be an absolute path name. The default is /tmp/mysql.sock.
This value can be set at server startup with the --socket option.

-DDEFAULT_CHARSET=utf8
缺省情况下，MySQL使用latin1的（CP1252西欧）字符集。cmake/character_sets.cmake文件包含允许的字符集名称列表。


my.cnf的配置文件的默认读取顺序为
File Name（上面的优先）    Purpose
/etc/my.cnf             Global options
/etc/mysql/my.cnf       Global options
SYSCONFDIR/my.cnf       Global options
$MYSQL_HOME/my.cnf      Server-specific options *******
defaults-extra-file     The file specified with --defaults-extra-file=path, if any
~/.my.cnf               User-specific options
~/.mylogin.cnf          Login path options

my.cnf是mysql启动时要读取的配置文件

WARNING: Default config file /etc/my.cnf exists on the system
This file will be read by default by the MySQL server
If you do not want to use this, either remove it, or use the
--defaults-file argument to mysqld_safe when starting the server
启动Mysql server时，可指定--default-file=/path/my.cnf参数来启动mysql服务。



测试转开发技术可能会有些跟不上，如果技术跟上了，测试转开发挺好，写代码考虑的条件会比较细一些，考虑问题的角度也会有很大的不同。
开发转测试，思维很难转换，经常会漏Bug