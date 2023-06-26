# Endnote 文献库介绍
[参考](https://liwt31.github.io/2020/05/19/endnote/) 

在Data文件夹下有若干子文件夹。如果在EndNote中保存了pdf则有pdf文件夹。
除此之外还有rdb和tdb两个文件夹。rdb和tdb中的文件后缀名均为*.frm、*.MYI和*.MYD。而这些文件后缀正是MySQL的数据文件。因此不难推断EndNote将所有后台数据保存为MySQL数据库格式，对这些数据库进行增删改查即可突破EndNote本身的接口限制访问EndNote文献库。
tdb里文件体积都较小而rdb中文件体积都较大。据一些简单测试貌似rdb中是主要数据而tdb中是回收站数据。
rdb（代表了一个MySQL数据库）中含有若干个MySQL数据表，其中与参考文献基本信息相关的是refs.*文件。[利用恢复数据库的方法，将这些文件恢复成MySQL数据库](https://stackoverflow.com/questions/879176/how-to-recover-mysql-database-from-myd-myi-frm-files) ：


# 问题
[修改作者名全是大写](https://blog.csdn.net/weixin_44029689/article/details/114580335)

[调整参考文献编号与参考文献间距](https://blog.csdn.net/sunflower02/article/details/109100392)
