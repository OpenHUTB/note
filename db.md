

# 教学


# mysql

索引：FULLTEXT（分词）、HASH、BTREE、RTREE

myISAM：
.frm表定义
.MYD(MYData)
.MYI(MyIndex)

direct IO应用场景：
不使用操作系统缓冲，使得磁盘IO（或者DMA）直接将数据存入-用户空间-的buffer。避免内核缓冲的内存消耗与CPU拷贝（数据从内核空间到用户空间的拷贝）的消耗
使用dma直接由dma控制从内存输入到用户空间的buffer中不经过cpu做mov操作，不消耗cpu
1. 大文件
2. 只使用一次

## 绿色版安装
[安装教程](https://blog.csdn.net/cweqin/article/details/112859446) ，
修改`my.ini`设置无密码直接登陆
```text
skip-grant-tables
```
设置安装目录和数据存放目录
```text
basedir="D:\matlab\software\db\mysql-5.7.36-winx64"
datadir="D:\mysql\data"
```

```text
:: 安装数据库（需要管理员权限）
:: 可能出现问题：The service already exists
:: 是由于之前已经安装过mysql并且没有删除干净
:: 查询mysql服务：sc query mysql
:: 删除mysql服务：sc delete mysql
mysqld --install

:: 启动服务
:: 可能报错：发生系统错误 2。系统找不到指定的文件。
:: 解决：打开注册表：HKEY_LOCAL_MACHINE -> SYSTEM -> CurrentControlSet -> Services -> MySQL 里 ImagePath 的值设置为 %MYSQL_HOME% 的路径，然后再尝试 net start mysql
:: https://blog.csdn.net/u014163312/article/details/116035272
:: 出现：error 2 has occurred.  The system cannot find the file specified.
:: mysqld --remove
:: https://blog.csdn.net/weixin_45051095/article/details/121187433
net start mysql
```
