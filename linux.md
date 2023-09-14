


# 软件
## acroread: error while loading shared libraries: libxml2.so.2: wrong ELF class: ELFCLASS64
软件是32位的，需要32位的 ×.so.×动态链接库，而系统是64位的所提供的该 动态链接库×.so.×是64位的，所以不能用。

# 硬盘
显示为0表示不是转动的有硬盘（固态硬盘）
```
lsblk -d -o name,rota
-d, --nodeps         don't print slaves or holders
-o, --output <list>  output columns
```


# shell
查看系统可以用的shell类型
```shell script
cat /etc/shells
```
## sh
/bin/sh 相当于 /bin/bash --posix。
sh就是开启了POSIX标准的bash 。

## dash
于 bash 过于复杂，有人把 bash 从 NetBSD 移植到 Linux(Ubuntu) 并更名为 dash（Debian Almquist Shell），并以获得更快的脚本执行速度。Debian Almquist shell，缩写为dash，一种 Unix shell。它比 Bash 小，只需要较少的磁盘空间，但是它的对话性功能也较少。

# 系统管理
## 使用sudo命令不用输入密码
* 输入su root进入root模式
* 输入vi /etc/sudoers (chmod u+w /etc/sudoers)
* 找到 %sudo ALL=(ALL:ALL) ALL这一行修改为 %sudo ALL=(ALL:ALL) NOPASSWD:ALL
* chmod u-w /etc/sudoers


# 其他
指定进程进行磁盘使用情况监控（[参考](https://blog.csdn.net/qq_34672033/article/details/89736473)）
```
sudo iotop -p 19744
```
指定用户进行磁盘监控
```buildoutcfg
sudo iotop -u d
```

# 问题
apt-get install安装依赖错误。
perl-base : 破坏: perl (< 5.30.0~) but 5.26.1-6ubuntu0.5 is to be installed
```commandline
apt install -f perl-base=5.26.1-6
apt-get install perl
apt-get install liberror-perl
apt-get install git
```



# 进程
使用top -c命令过滤基于进程名称列出的进程
top -bc | grep name_of_process



sudo echo "又一行信息" >> test.asc
权限不够。这是因为重定向符号 “>” 和 ">>" 也是 bash 的命令。
使用 sudo 只是让 echo 命令具有了 root 权限，但是没有让 “>” 和 ">>" 命令也具有 root 权限。
解决办法1： sudo sh -c 'echo "又一行信息" >> test.asc'
解决办法2： echo "第三条信息" | sudo tee -a test.asc


压力测试工具：
sudo apt-get install stress

CPU：4个调用sqrt函数的进程：
stress -c 4

内存：
stress --vm 2 --vm-bytes 3000M --vm-keep

ref: https://www.cnblogs.com/jiftle/p/12904248.html



cgroups子系统(control group)
/sys/fs/cgroup/*
1. cpu子系统，主要用于限制进程的cpu使用率
4. memory子系统，可以限制进程的内容使用量
ref:
https://segmentfault.com/a/1190000008323952
https://www.cnblogs.com/menkeyi/p/10941843.html




1. 查看是否开启自动休眠
```shell
sudo systemctl status sleep.target
```
2. 关闭自动休眠
```shell
sudo systemctl mask sleep.target suspend.target hibernate.target hybrid-sleep.target
```
3. 查看自动休眠是否关闭
```shell
systemctl status sleep.target
```




wget ftp://ftp.mrc-cbu.cam.ac.uk/ -r

sudo lshw -class network #查看本机网卡信息


列出当前使用的运行等级
systemctl get-default
启动系统救援模式
```
systemctl rescue
```
进入紧急模式
systemctl emergency
置多用户模式或图形模式为默认运行等级
# systemctl set-default runlevel3.target
# systemctl set-default runlevel5.target
Runlevel 0 : 关闭系统
Runlevel 1 : 救援？维护模式
Runlevel 3 : 多用户，无图形系统(这个)
Runlevel 4 : 多用户，无图形系统
Runlevel 5 : 多用户，图形化系统
Runlevel 6 : 关闭并重启机器


jbd2/sda2-8 导致 mount: /dev/sda is already mounted or /mnt/tmp busy

查看.tar.gz一级目录
tar tzvf ./crack.tgz | grep ^d  | awk -F/  '{if(NF<4) print }'
grep ^d  以表示目录的d开头，文件以-开头
awk -F fs :  --field-separator
awk 中的 NF 是由'/' 分割后的 字段个数！ 而不是 '/' 的个数(The variable NF is set to the total number of fields in the input record)
而且，行尾的'/' 后面，即使没有字符了，其后也被计算入一个 字段
drwxr-xr-x d/d               0 2020-03-26 23:45 crack_linux/        就是3个字段

解压压缩文件中的制定目录R2020a_1/到制定文件夹
tar -zxf ./crack.tgz R2020a_1/ -C /data2/install/matlab/2020a/tmp


批量重命名：
统一将 以.mp41结尾的文件 重命名为.mp4
rename 's/.mp41$/.mp4/' *


进入第三个文件夹
cd `ls | awk 'NR==3'`

epoll
基于事件的 轮询
epoll将“维护监视队列”和“进程阻塞”分离
就绪列表、epoll使用了红黑树作为索引结构
事件通知方式，每当fd就绪，系统注册的回调函数就会被调用，将就绪fd放到readyList里面，时间复杂度O(1)

边压缩边传输边解压(c: create; x: extract;)
z: Filter the archive through gzip
f: Use archive file or device ARCHIVE
短横线(-)可以表示输出流（产生输出流、接受输出流）
-C: Change to DIR before performing any operations
tar zcf - city2 | ssh lmy@115.157.195.198 tar zxf - -C /data2/lmy/data

unrar x -o- -y  *.rar
x  用绝对路径解压文件
o- 不覆盖已存在文件
y  假设对全部询问都回答是

文件恢复（参考：https://cloud.tencent.com/developer/article/1684479）：
先看内存中是否还存在
lsof | grep test_remove.py
cp /proc/9913/fd/1 /tmp/test_remove.py
没有就用ext4magic进行恢复
You must install the develop packages "ext2fs , blkid , e2p , uuid" to build ext4magic
sudo apt-get install libblkid-dev
libex2fs-dev

.tar.gz ->  tar zxf
.tar.bz2 -> tar jxf


根据文件名找文件的路径
locate libcanberra-gtk-module.so

set default zoom of firefox:
about:config
layout.css.devPixelsPerPx
value: 1.2

fdisk -l
lsblk

Make it run, then make it right, then make it fast.


宏内核通过函数调用访问特定的逻辑和数据。
微内核通过IPC(进程间通信)访问特定的逻辑和数据。（对于微内核而言，只需要send，receive两个系统调用就够了）

-generic、-lowlatency
延迟指的是多任务调度的延迟，延迟低指的是切换频繁，是频繁，不是快，所以在需要实时性的系统里，就可以更快响应。
是低延迟，还是高吞吐。

-preempt 降低延时，但是没有牺牲节能特性
-lowlatency
-rt
-realtime

RT-Preempt patch 是在Linux社区kernel的基础上，加上相关的补丁，以使得Linux满足实时性的需求。

查看内核版本：cat /etc/issue
uname -sr
uname -a
4.15.0-50-generic
r：目前发布的内核主版本。
x：偶数表示稳定版本；奇数表示开发中版本。（r.x描述内核系列）
y：错误修补的次数。
2.6.9-5.ELsmp
5:  表示这个当前版本的第5次微调patch ， 而ELsmp指出了当前内核是为ELsmp特别调校的
编译内核（https://blog.csdn.net/qq_36290650/article/details/83052315）：
tar -xavf linux-5.9.11.tar.xz
sudo apt-get install gcc make libncurses5-dev openssl libssl-dev build-essential pkg-config libc6-dev bison flex libelf-dev
cp /boot/config-4.15.0-20-generic .config
cd linux-5.9.11
cp /boot/config-4.15.0-20-generic .config
make menuconfig

sudo mv  ~/Desktop/linux-4.18.14  /usr/src/  将源码移动到用户目录下
cd /usr/src/linux-4.18.14/
sudo make install  安装
sudo mkinitramfs -o /boot/initrd.img-4.18.14  （产生initramfs镜像）输出镜像到 (现存：/boot/initrd.img-4.15.0-50-generic）
sudo update-initramfs -c -k 4.18.14
sudo update-grub2
首先把RAM disk(initrd)挂载起来（等到init程序和一些必要的模块运行起来之后，再切到真正的文件系统之中）
initramfs实际是一个cpio归档，启动所需的用户程序和驱动模块被归档成一个文件。因此，不需要cache，也不需要文件系统。


Ubuntu源码：http://archive.ubuntu.com/ubuntu/
http://cdimage.ubuntu.com/releases/
源码页面：
http://cdimage.ubuntu.com/releases/18.04/release/source/

内核包括：
CPU架构、驱动、
虚拟文件系统、内存管理、进程管理（进程通信）、网络栈、
系统调用接口

启动过程(MBR-> grub引导kernel ->init)：
1. BIOS： 1. Power-On Self Test, 读MBR（Master Boot Record） 512B
2. 系统引导，安装在MBR中的引导程序：比如lilo, grub等
3. 启动内核。解析/boot/grub/grub.conf -> 加载内核镜像到内存，将控制权交给内核
   运行/sbin/init程序，执行1号进程。
   /etc/rc1.d/   /etc/rc6.d/   -- /etc/rc.d/
   启动终端来等待用户登录。tty1,tty2,tty3...表示在运行等级1,2,3，4的时，都会执行/sbin/mingetty，执行了6次，linux有6个纯文本终端
   
0 - 停机
1 - 单用户模式
2 - 多用户，但是没有NFS
3 - 完全多用户模式
4 - 没有用到
5 - X11
6 - 重新启动

nc -lp 23 &(打开23端口，即telnet)

pigz
压缩：
time tar -cf - matlab-install/ | pigz -p 22 > matlab-install.tar.gz 
time tar -cf - matlab-install/ | pigz -p 22 > matlab-install.tgz 
16    23.586s
18    22.180s
20    21.710s
22    20.289s
24    21.877s
crete, file

解压：
time tar zxf matlab-install.tar.gz
52.558s
time pigz -p 22 -d matlab-install.tgz
25.982s
tar -xf matlab-install.tar


systemctl list-unit-files

uname -srm
cat /proc/version
Linux version 4.15.0-50-generic 
4 - 内核版本
15 - 主修订版本
0-50 - 次要修订版本
generic (12) - 补丁版本


批量重命名文件：
mmv \*.JPEG \#1.jpeg

修改ulimit -a,    open files
ulimit -HSn 102400

apt-get install –y  (安装默认选yes)

/bin          (binary)系统 必备执行文件
/sbin         系统管理 的必备程序
/usr/bin      应用程序工具 的必备执行文件
/usr/sbin     网络管理 的必备程序

du -h --max-depth=1

nohup bash get_coco_dataset.sh >out.txt 2>&1 &
2>&1 也就表示将错误重定向到标准输出上
/dev/null 表示空设备文件
0 表示stdin标准输入
1 表示stdout标准输出
2 表示stderr标准错误
& 放在命令到结尾，表示后台运行，防止终端一直被某个进程占用，这样终端可以执行别到任务
nohup放在命令的开头，表示不挂起（no hang up），也即，关闭终端或者退出某个账号，进程也继续保持运行状态，一般配合&符号一起使用

look up error: undefined symbol
nm libmklml_intel.so | grep 'mkldnn_stream_submit'

wget
-c 
断点续传(continue) 
-t 0 
反复尝试的次数，0为不限次数(timeout) 

列出文件绝对路径
realpath ppopp19_ae-master.zip
ls | sed "s:^:`pwd`/:"

解压zip
jar xvf abc.zip

解压一个目录下的所有压缩包
find . -name "*.tar" | xargs -n1 tar -xf
## -n1 ：表示每次只传递一个参数

显示一个名字的所有可能:
type -a kill
查看一个命令的执行路径（如果它是外部命令的话）:
type -p gedit 的输出是 /usr/bin/gedit


ldd 
export LD_TRACE_LOADED_OBJECTS=1

ldd libmwhgbuiltins.so
ERROR: libXt.so.6 => not found libXext.so.6 => not found

www.zlib.net/fossils/

释放显存：
sudo fuser /dev/nvidia*
kill -9 pid

df -h 查看各个分区容量
fdisk -l  查看各个硬盘容量
umount /dev/sda4		
mkfs.ext4 /dev/sda4     将/dev/sda4格式话为ext4

开机自启挂载硬盘
vi /etc/fstab
/dev/sdb4 /data /ext4 defaults 0 0

让普通账户使用分区
sudo chmod 777 /data


正在运行的程序到后台运行
按ctrl+z暂停已经运行的进程
bg %1
jobs -l

查看指定用户组(dong)的所有成员
grep dong /etc/group
得到：dong:x:1000:  所以用户组的ID为1000
cat /etc/passwd | grep 1000 | awk -F":" '{print $1"\t"$4}'
（ awk -F":" '{print $1"\t"$4}' /etc/passwd |grep '1000' ）

获取teamviewer的ID：teamviewer -info

杀不死teamviewer进程，停止服务：service teamviewerd stop

让Ubuntu的ssh保持长时间连接
1. 在/etc/ssh/ssh_config文件里加两个参数:
TCPKeepAlive yes
ServerAliveInterval 300
2. 修改或者创建~/.ssh/ssh_config

vi .bash_profile
alias python='python3
source .bash_profile

vmware-toolbox-cmd disk shrink /

可以ping通，但无法通过ssh连接虚拟机的解决方法
sudo ufw disable #关闭防火墙
sudo ufw enable #开启防火墙
sudo ufw status #查看防火墙状态
sudo apt-get install openssh-server

sudo apt-get install sysvbanner
banner linux

linux系统下的FTP传输日志文件xferlog(/var/log/)
/var/log/ambari-agent

显示所有僵尸进程：ps aux | grep Z
杀死僵尸进程的父进程：cat /proc/20118/stat（第一行第四列）


LIBRARY_PATH环境变量用于在程序编译期间查找动态链接库时指定查找共享库的路径
LD_LIBRARY_PATH环境变量用于在程序加载运行期间查找动态链接库时指定除了系统默认路径之外的其他路径

/var/ — 用于贮存variable（或不断改变的）文件，例如日志文件和打印机假脱机文件。

假脱机技术即SPOOLing（Simultaneous Peripheral Operating On-Line）
一项将独占设备改为共享设备的技术

/lost+found/ — 被 fsck 用来放置零散文件（没有名称的文件）
fsck（file system check）

/lib64是内核级的,/usr/lib64是系统级的,/usr/local/lib64是用户级的

load average: 系统在过去1分钟、5分钟、15分钟内运行进程队列中的平均进程数量

ctrl+c不能终止：ctrl z切到后台，用kill 9杀死

Linux修改登录默认进入的目录:用vim编辑器，打开/etc/passwd ，找到相应的用户，修改倒数第一个冒号前面的目录即可

netstat -nltp   n显示数字（不进行域名解析）、l显示监听的端口、t：TCP、p：获取进程名、进程号以及用户ID
netstat -ltpe   pe查看进程的拥有者

用户可用的最大进程数：ulimit -u
查看看进程当前运行的线程数命令为：pstree -p 3660 | wc -l


系统 linux，增加SSH终端连接数最大为1000个
vi /etc/ssh/sshd_config
输入/MaxStartups 定位到如下并修改
1)        #MaxStartups 10，#去掉，修改10为1000，MaxStartups 1000
2)        重启SSH服务，/etc/rc.d/init.d/sshd restart
查看某端口的连接数：netstat -nat | grep -i '22' | wc -l

sudo rm /var/lib/apt/lists/lock

内存使用及其VSZ（虚拟内存大小）和RSS（常驻集大小）:
VSZ表示如果一个程序完全驻留在内存的话需要占用多少内存空间;
RSS指明了当前实际占用了多少内存;


notification_email.sh
notification_email()
{
    emailuser='nongfugengxia@163.com'
    emailpasswd='donghaiwang.1'
    #emailsmtp='smtp.hobot.cc'
    emailsmtp='smtp.163.com'
    sendto='1402499358@qq.com'
    #sendto='haidong.wang@hobot.cc'
    title='fastdfs trackerd died Alarm'
    /data/sdj/fastdfs/notification_email/sendEmail-v1.56/sendEmail -f $emailuser -t $sendto -s $emailsmtp -u $title -xu $emailuser -xp $emailpasswd -o tls=no
}

while :
do
        stillRunning=$(ps -ef |grep "fdfs_trackerd" |grep -v "grep")
        if [ "$stillRunning" ] ; then
                echo "service was already started"
        else
                echo "service was not started"
                echo -e "fastdfs trackerd died" | notification_email
                sleep 600
        fi
        sleep 10
done


disk_check.sh
#!/bin/bash
partition_list=(`df -h | awk 'NF>3&&NR>1{sub(/%/,"",$(NF-1));print $NF,$(NF-1)}'`)
critical=90
notification_email()
{
    emailuser='nongfugengxia@163.com'
    emailpasswd='donghaiwang.1'
    emailsmtp='smtp.163.com'
    sendto='haidong.wang@hobot.cc'
    #sendto='1402499358@qq.com'
    title='Disk Space Alarm'
    /data/sdj/fastdfs/notification_email/sendEmail-v1.56/sendEmail -f $emailuser -t $sendto -s $emailsmtp -u $title -xu $emailuser -xp $emailpasswd -o tls=no
}

crit_info=""
while :
do
        for (( i=0;i<${#partition_list[@]};i+=2 ))
        do
                if [ "${partition_list[((i+1))]}" -lt "$critical" ];then
                        echo "OK! ${partition_list[i]} used ${partition_list[((i+1))]}%"
                else
                        if [ "${partition_list[((i+1))]}" -gt "$critical" ];then
                        crit_info=$crit_info"Warning!!! ${partition_list[i]} used ${partition_list[((i+1))]}%\n"
                        fi
                fi
        done
        if [ "$crit_info" != "" ];then
                echo -e $crit_info | notification_email
        fi
        sleep 6
done



rsync:(http://blog.csdn.net/u011414200/article/details/50411347#71-非-root-身份运行-rsync-服务)
wget https://download.samba.org/pub/rsync/src/rsync-3.1.2.tar.gz
./configure --prefix=/home/wanghaidong/softwares/rsync-3.1.2 --disable-ipv6
/home/wanghaidong/softwares/rsync-3.1.2/bin/rsync --daemon --config=/home/wanghaidong/softwares/rsync-3.1.2/bin/rsyncd.conf （启动后台服务没有显示）
/home/wanghaidong/softwares/rsync-3.1.2/bin/rsync --daemon --config=/home/wanghaidong/softwares/rsync-3.1.2/bin/rsyncd.conf （删除clientserver.c中的#ifdef HAVE_SETGROUPS部分，传输文件成功）
pid file = /home/wanghaidong/softwares/rsync-3.1.2/bin/rsyncd.pid  
lock file = /home/wanghaidong/softwares/rsync-3.1.2/bin/rsyncd.lock  
secrets file = /home/wanghaidong/softwares/rsync-3.1.2/bin/rsyncd.secrets   
motd file = /home/wanghaidong/softwares/rsync-3.1.2/bin/rsyncd.motd
log file = /home/wanghaidong/softwares/rsync-3.1.2/bin/rsyncd.log  
port = 11873
pid = wanghaidong 
gid = wanghaidong
use chroot = no 
max connections = 200  
timeout 600  

[test]  
path = /home/wanghaidong/softwares/rsync-3.1.2/bin/test/  
ignore errors  
read only = true  
list = false  
hosts allow = *  
#hosts deny = 0.0.0.0/32  
auth users wanghaidong  #????                     
comment = wanghaidong  test
*******************重点是这个 port 的设置，记得非 root 用户自定义的 port 必须大于 1024 才行，否则无法启动！(1024以下端口只有root才可使用)*******************
@ERROR: setgroups failed
rsync error: error starting client-server protocol (code 5) at main.c(1503) [sender=3.0.6]
(解决)https://askubuntu.com/questions/919724/rsync-error-setgroup-failed
setcap cap_net_bind_service,cap_setgid=+ep /home/wanghaidong/softwares/rsync-3.1.2/bin/rsync
cap_net_bind_service - 为了绑定1024以下的端口
cap_setgid - 导致setgroups failed错误
#ifdef HAVE_SETGROUPS
        /* Set the group(s) we want to be active. */
        if (setgroups(gid_list.count, gid_array)) {
            rsyserr(FLOG, errno, "setgroups failed");
            io_printf(f_out, "@ERROR: setgroups failed\n");
            return -1;
        }
#endif
setgroups()设置调用进程的补充组ID，需要合适的权限(Linux:the CAP_SETGID capability)。在rsync的二进制文件上需要CAP_SETGID或者root权限。
CAP_SETGID 6 (设定程序允许普通用户使用setgid函数)

rsync -vzrtopg --port=11873 --progress --delete --password-file=F:\ProgramFiles\php\eclipse\workspace\rsync\rsync.pwd run.py wanghaidong@10.19.19.23::test
F:\Horizon\syn\cwRsync_5.5.0_x86_Free\bin\rsync.exe --port=11873 -vzrtopgu --progress --delete wanghaidong@10.19.19.23::test /cygdrive/F/tmp (将test下载到本地F盘下的tmp目录)
/home/fastdb/test/rsync-3.1.2/rsync-3.1.2/bin/rsync --port=11873 -vzrtopgu --progress --delete wanghaidong@10.19.19.23::test /home/fastdb/test/rsync-3.1.2/rsync-3.1.2/bin/tmp  (22同步23的内容；将test下载到本地F盘下的tmp目录)

-a 以archive模式操作、复制目录、符号连接 相当于-rlptgoD
-r 是递归
-l 是链接文件，意思是拷贝链接文件；
-p 表示保持文件原有权限；
-t 保持文件原有时间；
-g 保持文件原有用户组；
-o 保持文件原有属主；
-D 相当于块设备文件；
-z 传输时压缩；
-P 传输进度；
-v 传输时的进度等信息，和-P有点关系，自己试试。可以看文档；
-e ssh的参数建立起加密的连接。
-u 只进行更新，防止本地新文件被重写，注意两者机器的时钟的同时
--progress是指显示出详细的进度情况
--delete是指如果服务器端删除了这一文件，那么客户端也相应把文件删除，保持真正的一致
--password-file=/password/path/file来指定密码文件，这样就可以在脚本中使用而无需交互式地输入验证密码了


Capabilities的主要思想在于分割root用户的特权，即将root的特权分割成不同的能力，每种能力代表一定的特权操作
SUID的作用就是：让本来没有相应权限的用户运行这个程序时，可以访问没有权限访问的资源







lsb_release -a      // 显示操作系统详细信息
cat /proc/meminfo   // 内存
lscpu               // CPU
lsblk               // 磁盘

ab测试：ab -n 100 -c 10 https://www.baidu.com/


Q: Found a swap file by the name ""
A: 因为正在编辑mysql_backup.sh时，VPN断开了，等重新连接上去就出现了这个现象。使用ls -a就能在文件当前目录能看到一个名为.mysql_backup.sh.swp的隐藏文件，使用rm .mysql_backup.sh.swp直接删除后即可解决这个问题。

Q: curl https://github.com/spf13/spf13-vim -L > spf13-vim.sh && sh spf13-vim.sh
curl: (1) Protocol https not supported or disabled in libcurl
A: https://github.com/coneo/blog/issues/19





动态链接库的名称有别名（soname）, 真名(realname)和链接名（linker name）。
别名由一个前缀lib,然后是库的名字，再加上一个后缀“.so”构成。
真名是动态链接库真实名称，一般总是在别名的基础加上一个小版本号，发布版本等构成。
除此之外，还有一个链接名，即程序链接时使用的库的名字。


多个静态.a库合并成一个.so（*.so文件不能直接合并，因为其中已经没有重定向信息）
gcc -shared -o c.so -Wl,--whole-archive a.a b.a -Wl,--no-whole-archive
