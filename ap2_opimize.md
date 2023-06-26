

请求响应慢排查
Mysql，可以开启慢查询
http://10.19.19.23:8200/web/html-program/program_list_platform.html
http://10.19.19.23:8200/datasys/pro/project/masterview/?offset=0

http://blog.csdn.net/joeyon1985/article/details/50036095
nginx
$upstream_response_time < request_time, 两者相近表示主要是后端PHP处理时间，比如：7.512 7.512
$request_time: nginx处理请求的时间，指的就是从接受用户请求数据到发送完回复数据的时间
upstream_response_time: 是从Nginx向后端建立连接开始，到接受完数据然后关闭连接为止的时间。因为会有重试，它可能有多个时间段
$request_time时间比$upstream_response_time长，这有可能是因为web页面通过post上传较大的数据，nginx一直在接收数据

php-fpm提供了慢执行日志
script_filename = /home/wanghaidong/ap2/datasystem-server/www/datasys/index.php
[0x00007f71eef87808] mysqli_query() /home/wanghaidong/ap2/datasystem-server/www/datasys/lib/comm/mysql.php:101
[0x00007f71eef87568] query() /home/wanghaidong/ap2/datasystem-server/www/datasys/lib/comm/mysql.php:158
[0x00007f71eef87310] fetchAll() /home/wanghaidong/ap2/datasystem-server/www/datasys/model/data/rawlist.php:91
[0x00007f71eef86c60] view() /home/wanghaidong/ap2/datasystem-server/www/datasys/model/user/resource.php:510
[0x00007f71eef84f78] detail() /home/wanghaidong/ap2/datasystem-server/www/datasys/model/user/permission.php:376
[0x00007f71eef841e8] detail() /home/wanghaidong/ap2/datasystem-server/www/datasys/model/user/permission.php:507
[0x00007f71eef83c68] recurList() /home/wanghaidong/ap2/datasystem-server/www/datasys/model/user/permission.php:509
[0x00007f71eef836f8] recurList() /home/wanghaidong/ap2/datasystem-server/www/datasys/model/user/permission.php:488
[0x00007f71eef831f0] traverse() /home/wanghaidong/ap2/datasystem-server/www/datasys/model/user/permission.php:526
[0x00007f71eef82950] retrieve() /home/wanghaidong/ap2/datasystem-server/www/datasys/lib/comm/tools.php:666
[0x00007f71eef82418] retrive() /home/wanghaidong/ap2/datasystem-server/www/datasys/logic/pro/project.php:289
[0x00007f71eef80018] masterview() /home/wanghaidong/ap2/datasystem-server/www/datasys/lib/init.php:64
[0x00007f71eef7f8e0] run() /home/wanghaidong/ap2/datasystem-server/www/datasys/index.php:7




故障排查：
点击标注；XHR
XHR类型即通过XMLHttpRequest方法发送的请求

