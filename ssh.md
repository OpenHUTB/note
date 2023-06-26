

MobaXterm_Personal_10.2
vi /etc/ssh/sshd_config
 X11Forwarding yes   \\确定no改写成yes
service sshd restart
运行eclipse

在Windows的命令提示符cmd中使用ssh工具--OpenSSH for Windows
http://sourceforge.NET/projects/opensshwindows/
添加PATH
就可以在cmd中直接使用ssh/ls/mv/scp等命令了
ssh fastdb@10.19.19.23


无密码登录:
ssh-keygen -t rsa -P ''
-t  Specifies the type of key to create
/home/chenlb下生成.ssh目录，.ssh下有id_rsa和id_rsa.pub。

scp .ssh/id_rsa.pub wanghaidong@10.19.19.23:/home/wanghaidong/id_rsa.pub

cat id_rsa.pub >> .ssh/authorized_keys

chmod 600 .ssh/authorized_keys