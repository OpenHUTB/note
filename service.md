

# 初始化
## 0. 安装Ubuntu系统18.04
查看正在使用的网卡名：
```
cat /proc/net/dev
```

```
vi /etc/netplan/01-network-manager-all.yaml
network:
  version: 2
  renderer: networkd
  ethernets:
    enp0s31f6:
      addresses: [115.157.195.140/24]
      gateway4: 115.157.195.253
      nameservers:
        addresses: [8.8.8.8]
      dhcp4: false
      optional: false

network:
  version: 2
  #renderer: NetworkManager
  ethernets:
    ens33:  
      addresses: [10.96.0.139/24]
      gateway4: 10.96.0.2
      nameservers:
        addresses: [1.2.4.8]
netplan apply
```

## 1. 显卡驱动及CUDA安装：
Driver Version: 418.56       CUDA Version: 10.1
```
wget http://us.download.nvidia.com/XFree86/Linux-x86_64/418.56/NVIDIA-Linux-x86_64-418.56.run
lsmod | grep nouveau

sudo vim /etc/modprobe.d/blacklist-nouveau.conf
blacklist nouveau
blacklist lbm-nouveau
options nouveau modeset=0
alias nouveau off
alias lbm-nouveau off

sudo bash -c "echo blacklist nouveau > /etc/modprobe.d/blacklist-nvidia-nouveau.conf"
sudo bash -c "echo options nouveau modeset=0 >> /etc/modprobe.d/blacklist-nvidia-nouveau.conf"

sudo update-initramfs -u

sudo /etc/init.d/lightdm stop # 关闭图形界面

sudo ./NVIDIA-Linux-x86_64-418.56.run --no-opengl-files

1. Are you sure you want to continue?    --> continue installation
2. building kernel modules......
3. would you like to sign the NVIDIA kernel module?   --> sigh the kernel module
4. would you like to generate a new one?   --> generate a new key pair
5. would you like to delete the private signing key?  --> no
6. certification  --> ok
7. key  --> ok
8. this will likely require rebooting your computer.  --> install signed kernel module
9. ...  --> ok
10. would you like to run the nvidia-xconfig utility... update?  --> no
11. see for details  --> ok

sudo /etc/init.d/lightdm start # 打开图形界面
sudo mokutil --import /usr/share/nvidia/nvidia*.der
sudo reboot


sudo apt-get remove cuda
sudo apt autoremove
sudo apt-get remove cuda*

cd /usr/local/
sudo rm -r cuda-10.1

sudo service lightdm stop
sudo service lightdm start

wget http://developer.download.nvidia.com/compute/cuda/10.1/Prod/local_installers/cuda_10.1.243_418.87.00_linux.run
sudo sh cuda_10.1.243_418.87.00_linux.run

vim ~/.bashrc
export PATH=/usr/local/cuda-10.1/bin:$PATH
export LD_LIBRARY_PATH=/usr/local/cuda/lib64:$LD_LIBRARY_PATH # 输入完毕后保存推出
更新一下
source ~/.bashrc

sudo cp cuda/include/cudnn.h /usr/local/cuda/include/
sudo cp cuda/lib64/libcudnn* /usr/local/cuda/lib64/
sudo chmod a+r /usr/local/cuda/include/cudnn.h
sudo chmod a+r /usr/local/cuda-9.0/lib64/libcudnn*

cat /usr/local/cuda/include/cudnn.h | grep CUDNN_MAJOR -A 2

sudo ln -s /usr/local/cuda-9.0 /usr/local/cuda
```

## 2. （申请固定IP）
查看IP地址
```
ifconfig
```
命令行登录
```
ssh zhangsan@115.157.195.140
```
安装ssh服务
```
sudo apt-get install openssh-server
```
下载Windows登录软件
MobaXterm

## 3. 管理员
添加用户
```
adduser zhangsan
```
用户登录
```
ssh zhangsan@115.157.195.140
```

## 4. 添加额外硬盘
查看插入的硬盘：/dev/sdb, /dev/sdc
```
sudo fdisk -lu
```
对硬盘进行分区：
```
sudo fdisk /dev/sdb

mount /dev/sdc /data2   
vi /etc/fstab
/dev/sdc                                  /data2          ext4    defaults          0       1
```
大于2T：
```
sudo parted /dev/sdb
```
分区管理工具
```
mklabel gpt
gpt
mkpart
ext4
0
-1
quit
sudo mkfs.ext4 -T largefile /dev/sdb1;       
sudo mount /dev/sdb1 /data1/
获取硬盘分区UUID：a3aaa507-6661-4b75-b275-c19131842778
sudo blkid /dev/sdb1
```


## 5. 服务器管理命令

### 用户管理
删除用户
```
sudo userdel -r hzs
```

### 修改登录提示信息 
(motd是message of the day的缩写，意思是“当天的提示信息”)
```
vi /etc/update-motd.d/00-header
```


```
top
nvidia-smi
```


198 磁盘挂载
```
echo "kkk" | sudo -S mount /dev/sda2 /data
echo "kkk" | sudo -S mount /dev/sdb1 /data1
echo "kkk" | sudo -S mount /dev/sdc1 /data2
```


下载CUDA:
```
wget http://developer.download.nvidia.com/compute/cuda/11.0.2/local_installers/cuda_11.0.2_450.51.05_linux.run
sudo sh cuda_11.0.2_450.51.05_linux.run

export PATH=$PATH:/usr/local/cuda/bin
export LD_LIBRARY_PATH=/usr/local/cuda/lib64:$LD_LIBRARY_PATH
```

### ubuntu设置不休眠
sudo vi /etc/systemd/logind.conf
打开文件后修改下面这行：#HandleLidSwitch=suspend
改成这样：HandleLidSwitch=ignore
保存文件，重启 Login Manager 服务
service systemd-logind restart


### docker
https://hub.docker.com/r/ufoym/deepo
https://github.com/Stephenfang51/command_for_deeplearning/blob/master/Docker%20%E6%B7%B1%E5%BA%A6%E5%AD%A6%E4%B9%A0%E9%85%8D%E7%BD%AE.md




### 查看内核加载模块的状态
lsmod | grep nvidia.drm
lsof | grep nvidia-drm
被用户空间进程使用的文件（nvidia-drm是内核模块）
systemctl isolate multi-user.target （启动运行等级，即多用户模式（命令行），multi-user.target，表示多用户命令行状态；另一个是graphical.target，表示图形用户状态，它依赖于multi-user.target）
systemctl stop systemd-logind （使用这两句之后才能卸载nvidia-drm模块）
sudo modprobe -r nvidia-drm

sudo apt-get remove --purge nvidia*
install NVIDIA-driver.148


### 显示万兆网卡
```
lspci -vvv | grep Ethernet
```

### ubuntu远程桌面实现
（包括解决connection problem,giving up问题）

[参考](http://c-nergy.be/blog/?p=13455)
```
sudo add-apt-repository ppa:martinx/xrdp-hwe-18.04
sudo apt-get update
sudo apt-get install xrdp xorg
Y, Y
```



# 网络

## Clash for Windows
为git设置代理，找到 Clash for Windows 常规选项卡中的API核心端口（而不是主程序默认端口）
```commandline
git config --global https.proxy http://127.0.0.1:49890
git config --global https.proxy https://127.0.0.1:49890
```

为TortoiseGit设置代理，右键 -> TortoiseGit -> Settings -> Network
```commandline
Server address : http://127.0.0.1
Port : 7890  （主程序默认端口） 
```

## ZeroTier
不需要代理服务器，免费。

[步骤](https://www.jianshu.com/p/9f7691cb32d3) 
Ubuntu安装
```shell
curl -s https://install.zerotier.com | sudo bash
```
```shell
You are ZeroTier address [ 3942543bd2 ].
```

接入网络
```shell
sudo zerotier-cli join e5cd7a9e1c0f04b8
```


## OpenVPN
[设置](https://www.ywbj.cc/?p=663) 
注意：需要代理服务器。



## 查看
查看所有的网卡（包括禁用的，flag后没有数字）
```
ifconfig -a
```
禁用网卡
```
ifconfig eth0 down
```
启用网卡
```
ifconfig eth0 up
```

查看当前使用的网卡 以及 查看某进程使用的网络带宽情况 以及 端口占用的情况
```
sudo nethogs
sudo lsof -i | grep 8888
```


## 网络代理
在198上设置http代理服务器
```
sudo apt-get install tinyproxy
vi /etc/tinyproxy/tinyproxy.conf
Port 8888
```
允许所有的人连接代理
```
# Allow 127.0.0.1

systemctl restart tinyproxy.service
```

从其他机器测试是否可以连接（需要有返回“百度”的中文，不然还是表示不可以连接）
```
curl -x 115.157.195.198:8888 www.baidu.com
```
查看访问日志
```
sudo tail -f /var/log/tinyproxy/tinyproxy.log
```

临时使系统不响应ping
```
echo 1 > /proc/sys/net/ipv4/icmp_echo_ignore_all
```

## 网络问题
### 网卡灰色
```
sudo /etc/init.d/networking restart
下面那个网线孔(140)
```

### Name or service not known
```
vi /etc/resolv.conf
```
添加
```
nameserver 8.8.8.8
nameserver 114.114.114.114
```
永久修改[参考](https://blog.csdn.net/lengye7/article/details/88877867)
```
vi /etc/systemd/resolved.conf
```






## nginx共享目录
location / {
    alias   /;
    autoindex on;
}



开机自启 /etc/rc.local
echo "jjj" | sudo -S /***/nginx




开启自启动
vi /lib/systemd/system/nginx.service
Description=nginx - high performance web server
After=network.target remote-fs.target nss-lookup.target
[Service]
Type=forking
ExecStart=/data2/whd/software/nginx-1.7.9/sbin/nginx -c /data2/whd/software/nginx-1.7.9/conf/nginx.conf
ExecReload=/data2/whd/software/nginx-1.7.9/sbin/nginx -s reload
ExecStop=/data2/whd/software/nginx-1.7.9/sbin/nginx -s stop
[Install]
WantedBy=multi-user.target

使配置生效
systemctl daemon-reload
设置开机启动
systemctl enable nginx.service
nginx操作指令
systemctl start nginx.service
systemctl stop nginx.service
systemctl reload nginx.service
systemctl restart nginx.service
systemctl status nginx.service

```shell
sudo apt install samba
```
服务器共享文件夹给Windows
```shell
vi /etc/samba/smb.conf
```
```text
[share]
    path = /
    browseable = yes
    writeable = yes
```
（注意颜色必须变，避免敲错）
```shell
systemctl start smbd
或者: sudo service smbd start
```

开机自启：
```shell
systemctl enable smbd
检查自启动：systemctl is-enable smbd
检查启动：  systemctl is-active smbd
```


创建samba创建用户名和密码
```shell
sudo smbpasswd -a d
```

Windows映射网络驱动器-> 文件夹
\\115.157.195.140\share
输出的网络凭证为samba的用户名和密码









命令行登录后，都是白色
```
vi /etc/passwd
/home/d的/bin/csh改成/bin/bash
```

文件同步
```
nohup scp -r /data2/whd/ d@115.157.195.198:/data2/ > scp.out 2>&1 &

单向同步：（https://www.cnblogs.com/qinhir/p/6589403.html）
sudo apt-get install rsync

sudo rsync -avzP --delete /data2/whd/doc/harddisk.txt d@115.157.195.198::d --password-file=/etc/rsync/rsyncd.secrects
```


```
# ps -ef|grep rsync（发现没有服务）
# rsync --daemon（即可）
Failed to parse config file: /etc/rsyncd.conf
```


双向同步文件(ref:https://www.jianshu.com/p/20ac48b0b0ad)：
sudo apt-get install unison
sudo apt-get install inotify-tools


QT程序启动报错(rstudio)
增加调试信息：
export QT_DEBUG_PLUGINS=1
再启动时显示: Cannot load *.so
查看缺少的.so的依赖：ldd *.so
安装QT5.12
https://download.qt.io/official_releases/qt/5.12/5.12.9/

下载工具：
aria2c *.run


ModuleNotFoundError: No module named 'CommandNotFound'
```
sudo vi /usr/lib/command-not-found
#!/usr/bin/python3.6
```

升级Python
https://www.jb51.net/article/152486.htm
Q: No module named 'lsb_release'
A: 将/usr/bin/lsb_release中首行改为：
```
#! /usr/bin/python3.6 -Es (-E:忽略像PYTHONPATH和PYTHONHOME这样修改解释器行为的环境变量； -s：不增加用户的site目录给sys.path）
```

Q: ModuleNotFoundError: No module named '_ctypes'
A: libffi-dev

Q: ImportError: cannot import name 'main'
A: vi /usr/bin/pip
from pip._internal import main


允许root远程登录：
vi /etc/ssh/sshd_config
修改 PermitRootLogin yes
service sshd restart

nmon
可以监控所有

测CPU、内存
top 


测磁盘
lsof /dev/sda | head
lsof -p $pid
cat /proc/$pid/io
No module named 'iotop'
/usr/bin/iotop  -> python3.6
sudo iotop -o   只显示有IO操作的进程
-b 				批量显示，无交互，主要用作记录到文件
-d SEC			间隔SEC秒显示一次
-p PID     		监控指定的进程
-u USER			监控指定用户名的进程
-k              使用千字节而不是人类友好的单位
交互式命令：
左右箭头：		改变排序方式，默认是按IO排序
r:				反向排序
o:				只显示有IO输出的进程
p:				进程/线程的显示方式切换
a:				显示累积使用量

sudo apt install sysstat
iostat -x -k
w_await: 写请求释放给设备的平均时间（包括在请求队列中等待的时间和服务时间）

%user：CPU处在用户模式下的时间百分比。
%nice：CPU处在带NICE值的用户模式下的时间百分比。
%system：CPU处在系统模式下的时间百分比。
%iowait：CPU等待输入输出完成时间的百分比。
%steal：管理程序维护另一个虚拟处理器时，虚拟CPU的无意识等待时间百分比。
%idle：CPU空闲时间百分比。

rrqm/s：  每秒进行 merge 的读操作数目.即 delta(rmerge)/s： requests merged
wrqm/s： 每秒进行 merge 的写操作数目.即 delta(wmerge)/s
%util： 一秒中有百分之多少的时间用于 I/O
如果%util接近100%，说明产生的I/O请求太多，I/O系统已经满负荷
   idle小于70% IO压力就较大了，一般读取速度有较多的wait。
svctm:平均每次设备I/O操作的服务时间  service time
await:平均每次设备I/O操作的等待时间 
avgqu-sz:平均I/O队列长度  average queue

测网速
wget -O speedtest-cli https://raw.githubusercontent.com/sivel/speedtest-cli/master/speedtest.py
chmod +x speedtest-cli
./speedtest-cli


RTX6000 24G    35200*2=70400 元
RTX8000 48G    53500*2=107000元

Virtualbox NAT
Intel PRO/1000 MT Desktop (82540EM)

新的机器：
service network-manager restart
dns临时配置：
vi /etc/resolv.conf
永久修改DNS：
vi /etc/systemd/resolved.conf
DNS=8.8.8.8
LLMNR=no  
设置的是禁止运行LLMNR(Link-Local Multicast Name Resolution)，否则systemd-resolve会监听5535端口
在DNS 服务器不可用时，DNS 客户端计算机可以使用本地链路多播名称解析 (LLMNR—Link-Local Multicast Name Resolution)（也称为多播 DNS 或 mDNS）来解析本地网段上的名称。
sudo systemctl restart systemd-resolved  (ping 不同www.baidu.com但是能ping通8.8.8.8，重启这个就能上网了）
Systemctl是一个systemd工具，主要负责控制systemd系统和服务管理器。
Systemd的功能是用于集中管理和配置类UNIX系统。Systemd是用来启动守护进程，守护进程（daemon）
能ping通www.baidu.com然后浏览器不能上网，需要启动代理v2ray。

只能上很少一部分网站。
设置->网络-> 禁用网络代理

删除用户：
sudo userdel -r mww

使用X11转发远程打开Pycharm操作起来卡：
修改Help-> Edit Custom VM Options:
-XX:+UseCompressedOops
new一个空对象在32为系统中占用内存大小是8byte（对象头，在堆中）+4byte（对象的引用地址，在栈中）=12byte；
new一个空对象在64为系统中占用内存大小是16byte（对象头，在堆中）+8byte（对象的引用地址，在栈中）=24byte；
可想而知同一个对象在64位系统中占的内存加大一半了，不仅消耗运行内存，而且GC回收时挺耗cpu的（ jvm 的堆大小有限,用 32bits 就足够标识了甚至还多了 -> 32bits 有 2^32-1 * 8bytes 的空间，已经远远大于常见 JVM 堆内存了）
jvm的属性-XX:+UseCompressedOops在JDK 1.6和之后的版本都默认开启了，所以jvm开启了压缩之后64为系统的对象也只占用12byte。
Ordinary Object Pointer （普通对象指针），它用来表示对象的实例信息，看起来像个指针实际上是藏在指针里的对象。

不能上网，重启网卡
ifdown enp0s31f6
sudo ifup enp0s31f6

查看插入的硬盘：
sudo blkid
mount /dev/sdc /data2
vi /etc/fstab
/dev/sdc                                  /data2          ext4    defaults          0       1


插入移动硬盘：
sudo fdisk -l

主菜单快捷键：Ctral+Esc

监控实时流量（指定网卡）
iftop -i enp0s31f6

virtualbox
mac: OS X 10.11 El Capitan GM Candidate by TechReviews.rar
setting->storage -> 第一个后边下拉选择：OS X 10.11 El Capitan GM by TechReviews.vmdk
（EFI是勾上的）






# GPU
## 初始化
```
Driver Version: 418.56
CUDA Version: 10.1
cudnn-10.1-linux-x64-v7.5.0.56.tgz
```

## 查看
```
gpustat
fuser -v /dev/nvidia*   # 查找占用GPU资源的PID，通过kill -9 PID杀死程序
```

## 压力测试
```buildoutcfg
wget https://codeload.github.com/wilicc/gpu-burn/zip/master
mv master master.zip
unzip master.zip
make
export CUDA_VISIBLE_DEVICES=0,1,2,3
./gpu_burn 100
```
## 限制
影响单个GPU（从0开始算）: -i
```
sudo nvidia-smi -i 3 -pl 100
```
限制GPU功率（应该在100W-280W之间）
从250W调到100W
```
sudo nvidia-smi -pl 100
sudo nvidia-smi -cc 1 # 使用p0性能模式计算, 默认是p2, 玄学, 效果不明显
```
查看支持的时钟频率：
```
nvidia-smi -q -i 3  -d SUPPORTED_CLOCKS
```


限制瓦特数[参考](https://blog.csdn.net/qq_25562325/article/details/120369929)
```
--power-limit=POWER_LIMIT
sudo nvidia-smi -pm 1 # 允许调节
sudo nvidia-smi -pl 150 # 调节显卡功耗, 注意不能太低, 否则会执行高负载任务可能会失败重启 （默认250）
```
Power limit for GPU 00000000:19:00.0 was set to 120.00 W from 250.00 W.
Warning: persistence mode is disabled on this device. This settings will go back                                                           to default as soon as driver unloads (e.g. last application like nvidia-smi or                                                           cuda application terminates). Run with [--help | -h] switch to get more informat                                                          ion on how to enable persistence mode.



## 问题
安装CUDA时候出现不支持的编译器
```
sudo apt install gcc-6 g++-6
sudo ln -s /usr/bin/gcc-6 /usr/local/bin/gcc
sudo ln -s /usr/bin/g++-6 /usr/local/bin/g++

/usr/lib/xorg/Xorg
xorg startx
```




service sshd stop
service sshd start

只允许指定用户登录，其他用户报：Permission denied, please try again.
vi /etc/ssh/sshd_config
AllowUsers d root whd hx
systemctl restart sshd

重置指定用户的密码：
sudo passwd <user_name>


pt.hnu.edu.c
portal








# 打印机
```
http://127.0.0.1:631/printers
/etc/init.d/cups start
http://115.157.195.140:631/printers/HP-LaserJet-M1005
printer -> 菜单Server -> setting -> 允许远程连接
配置文件：/etc/cups/cupsd.conf
```

## samba共享打印机
```
vi  /etc/samba/smb.conf
[printers]
        comment = All Printers
        path = /var/spool/samba
        printable = Yes
        create mask = 0600
        browseable = No
        writable = no
        guest ok =yes
```

Windows连接打印机



# 虚拟机

## 迁移windows虚拟机到服务器

备份win10[参考](https://www.diskgenius.cn/exp/migrate-physical-windows-to-vmware.php)（不包括导入）：

导入.vmdk文件[参考](https://kb.vmware.com/s/article/2010196?lang=zh_CN)：        

分辨率设置为1920×1080

## 挂载windows文件共享
### 共享目录给ubuntu
```
https://blog.csdn.net/qq_42906907/article/details/103236297
other (file://DESKTOP-MNN5UIL/other)
```
需要重启

```
apt-get install samba*  cifs-utils
echo "jjj" | sudo -S mount -t cifs -o rw,username=Administrator,password=jjj //192.168.160.131/d/   /data2/whd/win10

sudo mount -t cifs -o rw,username=Administrator,password=jjj,nounix,sec=ntlmssp,rw,uid=1000,gid=1000,dir_mode=666,file_mode=666 //192.168.160.131/d/   /data2/whd/win10
-t --types fstype: filesystem type(Common Internet File System)
-o options：使用逗号分隔。
id -u 获取用户ID；
id -g 获取组ID；（安装系统时初始用户通常都为1000）
dir_mode
file_mode
```

## 开机启动
gnome-session-properties（启动图形界面vmware成功）

## 不能打开/dev/vmmon
Q: could not open /dev/vmmon, Please make sure that the kernel module 'vmmon' is loaded
A: sudo /etc/init.d/vmware start

## 配置
虚拟机Cannot connect the virtual device sata0:1
删除CD/ROM

共享目录给Ubuntu虚拟机，在VMWare设置好之后到Ubuntu的/mnt/hgfs/host_root目录下找。





ModuleNotFoundError: No module named 'sklearn.metrics.base'








以用户（用户组）为单位进行限制
vi /etc/security/limits.conf  （shell重新登录生效）
whd              hard    nproc           10
whd              hard    as              16024000

ref: https://www.cnblogs.com/jiftle/p/12904248.html


# 限制

## 限制进程的资源（这里以内存为例）
/sys/fs/cgroup/cpu/
sudo apt install cgroup-tools
为用户whd创建一个名为whd_limit的cgroup
```
sudo cgcreate -a whd -g memory:whd_limit
cat memory.kmem.limit_in_bytes  （查看）
#: echo 1024000 > memory.kmem.limit_in_bytes   （修改）
sudo cgexec -g memory:whd_limit bash  （测试）

echo $$
sudo sh -c "echo 27385 > cgroup.procs"

stress --vm 2 --vm-bytes 3000M --vm-keep
```
显示：无法分配内存

## 限制网络带宽
sudo apt-get install wondershaper


# 磁盘

## 文件服务器
```shell
sudo apt-get install nginx
sudo vi /etc/nginx/conf.d/file_server.conf

server {
  listen 8013; 
  server_name 172.21.121.130; # 自己PC的ip或者服务器的域名 charset utf-8; # 避免中文乱码 
  root /; # 存放文件的目录 
  location / { 
    autoindex on; # 索引 
    autoindex_exact_size on; # 显示文件大小 
    autoindex_localtime on; # 显示文件时间 
  }
}

sudo rm /etc/nginx/sites-enabled/default
sudo service nginx start|stop|reload|
```

## 移动硬盘
Disk /dev/loop0：111.6 MiB，117014528 字节，228544 个扇区
单元：扇区 / 1 * 512 = 512 字节
扇区大小(逻辑/物理)：512 字节 / 512 字节
I/O 大小(最小/最佳)：512 字节 / 512 字节


Disk /dev/loop1：548 KiB，561152 字节，1096 个扇区
单元：扇区 / 1 * 512 = 512 字节
扇区大小(逻辑/物理)：512 字节 / 512 字节
I/O 大小(最小/最佳)：512 字节 / 512 字节


Disk /dev/loop2：704 KiB，720896 字节，1408 个扇区
单元：扇区 / 1 * 512 = 512 字节
扇区大小(逻辑/物理)：512 字节 / 512 字节
I/O 大小(最小/最佳)：512 字节 / 512 字节


Disk /dev/loop4：2.5 MiB，2658304 字节，5192 个扇区
单元：扇区 / 1 * 512 = 512 字节
扇区大小(逻辑/物理)：512 字节 / 512 字节
I/O 大小(最小/最佳)：512 字节 / 512 字节


Disk /dev/loop5：2.5 MiB，2658304 字节，5192 个扇区
单元：扇区 / 1 * 512 = 512 字节
扇区大小(逻辑/物理)：512 字节 / 512 字节
I/O 大小(最小/最佳)：512 字节 / 512 字节


Disk /dev/loop6：140.7 MiB，147492864 字节，288072 个扇区
单元：扇区 / 1 * 512 = 512 字节
扇区大小(逻辑/物理)：512 字节 / 512 字节
I/O 大小(最小/最佳)：512 字节 / 512 字节


Disk /dev/loop7：2.6 MiB，2748416 字节，5368 个扇区
单元：扇区 / 1 * 512 = 512 字节
扇区大小(逻辑/物理)：512 字节 / 512 字节
I/O 大小(最小/最佳)：512 字节 / 512 字节


Disk /dev/nvme0n1：1.9 TiB，2048408248320 字节，4000797360 个扇区
单元：扇区 / 1 * 512 = 512 字节
扇区大小(逻辑/物理)：512 字节 / 512 字节
I/O 大小(最小/最佳)：512 字节 / 512 字节
磁盘标签类型：gpt
磁盘标识符：A6855150-E88F-4E44-B61B-E22714A6A831

设备              起点       末尾       扇区  大小 类型
/dev/nvme0n1p1    2048    1050623    1048576  512M EFI 系统
/dev/nvme0n1p2 1050624 4000796671 3999746048  1.9T Linux 文件系统


Disk /dev/sda：7.3 TiB，8001563222016 字节，15628053168 个扇区
单元：扇区 / 1 * 512 = 512 字节
扇区大小(逻辑/物理)：512 字节 / 4096 字节
I/O 大小(最小/最佳)：4096 字节 / 4096 字节


Disk /dev/sdb：2.7 TiB，3000592982016 字节，5860533168 个扇区
单元：扇区 / 1 * 512 = 512 字节
扇区大小(逻辑/物理)：512 字节 / 4096 字节
I/O 大小(最小/最佳)：4096 字节 / 4096 字节


Disk /dev/sdc：14.6 TiB，16000900661248 字节，31251759104 个扇区
单元：扇区 / 1 * 512 = 512 字节
扇区大小(逻辑/物理)：512 字节 / 4096 字节
I/O 大小(最小/最佳)：4096 字节 / 4096 字节


Disk /dev/sdd：7.3 TiB，8001563222016 字节，15628053168 个扇区
单元：扇区 / 1 * 512 = 512 字节
扇区大小(逻辑/物理)：512 字节 / 4096 字节
I/O 大小(最小/最佳)：4096 字节 / 4096 字节


Disk /dev/loop8：2.5 MiB，2605056 字节，5088 个扇区
单元：扇区 / 1 * 512 = 512 字节
扇区大小(逻辑/物理)：512 字节 / 512 字节
I/O 大小(最小/最佳)：512 字节 / 512 字节


Disk /dev/loop9：548 KiB，561152 字节，1096 个扇区
单元：扇区 / 1 * 512 = 512 字节
扇区大小(逻辑/物理)：512 字节 / 512 字节
I/O 大小(最小/最佳)：512 字节 / 512 字节


Disk /dev/loop10：4 KiB，4096 字节，8 个扇区
单元：扇区 / 1 * 512 = 512 字节
扇区大小(逻辑/物理)：512 字节 / 512 字节
I/O 大小(最小/最佳)：512 字节 / 512 字节


Disk /dev/loop11：93.8 MiB，98344960 字节，192080 个扇区
单元：扇区 / 1 * 512 = 512 字节
扇区大小(逻辑/物理)：512 字节 / 512 字节
I/O 大小(最小/最佳)：512 字节 / 512 字节


Disk /dev/loop12：55.5 MiB，58204160 字节，113680 个扇区
单元：扇区 / 1 * 512 = 512 字节
扇区大小(逻辑/物理)：512 字节 / 512 字节
I/O 大小(最小/最佳)：512 字节 / 512 字节


Disk /dev/loop13：110.6 MiB，115986432 字节，226536 个扇区
单元：扇区 / 1 * 512 = 512 字节
扇区大小(逻辑/物理)：512 字节 / 512 字节
I/O 大小(最小/最佳)：512 字节 / 512 字节


Disk /dev/loop14：247.9 MiB，259948544 字节，507712 个扇区
单元：扇区 / 1 * 512 = 512 字节
扇区大小(逻辑/物理)：512 字节 / 512 字节
I/O 大小(最小/最佳)：512 字节 / 512 字节


Disk /dev/loop15：219 MiB，229638144 字节，448512 个扇区
单元：扇区 / 1 * 512 = 512 字节
扇区大小(逻辑/物理)：512 字节 / 512 字节
I/O 大小(最小/最佳)：512 字节 / 512 字节


Disk /dev/loop16：93.8 MiB，98357248 字节，192104 个扇区
单元：扇区 / 1 * 512 = 512 字节
扇区大小(逻辑/物理)：512 字节 / 512 字节
I/O 大小(最小/最佳)：512 字节 / 512 字节


Disk /dev/loop17：55.5 MiB，58212352 字节，113696 个扇区
单元：扇区 / 1 * 512 = 512 字节
扇区大小(逻辑/物理)：512 字节 / 512 字节
I/O 大小(最小/最佳)：512 字节 / 512 字节


Disk /dev/loop18：61.9 MiB，64901120 字节，126760 个扇区
单元：扇区 / 1 * 512 = 512 字节
扇区大小(逻辑/物理)：512 字节 / 512 字节
I/O 大小(最小/最佳)：512 字节 / 512 字节


Disk /dev/loop19：65.1 MiB，68259840 字节，133320 个扇区
单元：扇区 / 1 * 512 = 512 字节
扇区大小(逻辑/物理)：512 字节 / 512 字节
I/O 大小(最小/最佳)：512 字节 / 512 字节


Disk /dev/loop20：65.2 MiB，68378624 字节，133552 个扇区
单元：扇区 / 1 * 512 = 512 字节
扇区大小(逻辑/物理)：512 字节 / 512 字节
I/O 大小(最小/最佳)：512 字节 / 512 字节


Disk /dev/loop21：248.8 MiB，260841472 字节，509456 个扇区
单元：扇区 / 1 * 512 = 512 字节
扇区大小(逻辑/物理)：512 字节 / 512 字节
I/O 大小(最小/最佳)：512 字节 / 512 字节


Disk /dev/loop22：704 KiB，720896 字节，1408 个扇区
单元：扇区 / 1 * 512 = 512 字节
扇区大小(逻辑/物理)：512 字节 / 512 字节
I/O 大小(最小/最佳)：512 字节 / 512 字节


Disk /dev/loop23：140.7 MiB，147517440 字节，288120 个扇区
单元：扇区 / 1 * 512 = 512 字节
扇区大小(逻辑/物理)：512 字节 / 512 字节
I/O 大小(最小/最佳)：512 字节 / 512 字节


Disk /dev/loop24：219 MiB，229638144 字节，448512 个扇区
单元：扇区 / 1 * 512 = 512 字节
扇区大小(逻辑/物理)：512 字节 / 512 字节
I/O 大小(最小/最佳)：512 字节 / 512 字节


Disk /dev/loop25：61.9 MiB，64901120 字节，126760 个扇区
单元：扇区 / 1 * 512 = 512 字节
扇区大小(逻辑/物理)：512 字节 / 512 字节
I/O 大小(最小/最佳)：512 字节 / 512 字节


## /data1
```
1.7T	./whd
726G	./data
21G	./cy
15G	./wq
3.9M	./print
8.3G	./wiki
5.1G	./install
16G	./hzs
544M	./hoo
28G	./wsz
61G	./wyq
50M	./server
42G	./moh
16K	./.Trash-1000
2.8M	./archive
32G	./kitti
16K	./lost+found
2.6T	.
```

# matlab
## matlab 后台运行
```
nohup /data2/whd/workspace/AI/tools/shell/limitCpu.sh >/dev/null  2>&1 &

/usr/local/MATLAB/MATLABWebAppServer/R2018a
/usr/local/MATLAB/MATLAB_Runtime
```


# 集群
## MJS
Matlab Job Scheduler (MJS)，是否支持GPU。
需要从 matlab_2020a 中拷贝mjs文件
```commandline
cp /data2/whd/software/matlab_2020b/toolbox/parallel/bin/mjs /data3/software/matlab_2022a_linux/toolbox/parallel/bin/
```
运行 `toolbox\parallel\bin\admincenter.bat`


注意：使用root用户登录，否则没有写/var/run的权限报错。


## slurm
slurm搭建的初衷是为了将多个GPU机器连接起来，从来利用多台机器的计算能力

## Torque
PBS是功能最为齐全，历史最悠久，支持最广泛的本地集群调度器之一。 PBS的目前包括openPBS，PBS Pro和Torque三个主要分支。其中OpenPBS是最早的PBS系统，目前已经没有太多后续开发，PBS pro是PBS的商业版本，功能最为丰富。Torque是Clustering公司接过了OpenPBS，并给与后续支持的一个开源版本。

## PBS pro
Matlab 中支持 Windows。

# 用户
实验室的服务器，有4块RTX 2080的GPU，供大家使用
IP地址：172.21.121.130
用户名：ubuntu
密码：a123456
磁盘空间有限，用的时候用自己的名字新建一个目录，不要用管理员账户权限以免弄坏系统。

通过命令行启动向日葵远程：
```commandline
sudo /usr/local/sunlogin/bin/sunloginclient
```
如果运行出现错误`MoTTY X11 proxy: Unsupported authorisation protocol`，则需要将位于~ 目录中的.Xauthority 文件复制到/root目录中：
```commandline
sudo cp ~/.Xauthority /root
```

向日葵软件控制Ubuntu一直连不到桌面或者一直黑屏的解决办法


# 问题排查
## 系统自动关机
排查
```buildoutcfg
grep -iv ': starting\|kernel: .*: Power Button\|watching system buttons\|Stopped Cleaning Up\|Started Crash recovery kernel' \
  /var/log/messages /var/log/syslog /var/log/apcupsd* \
  | grep -iw 'recover[a-z]*\|power[a-z]*\|shut[a-z ]*down\|rsyslogd\|ups'
```
当意外关闭电源或发生硬件故障时，文件系统将无法正确卸载，因此在下次启动时，您可能会收到如下日志：[参考](https://qastack.cn/unix/9819/how-to-find-out-from-the-logs-what-caused-system-shutdown)
```buildoutcfg
/var/log/syslog:Dec 24 10:18:52 amax kernel: [ 2549.038990] systemd-journald[856]: File /var/log/journal/e17594ae9cea4e28992eb79bc7fc1ce9/user-1012.journal corrupted or uncleanly shut down, renaming and replacing.
```

## NVML初始化失败 
Failed to initialize NVML: Driver/library version mismatch
卸载驱动
```
sudo /usr/bin/nvidia-uninstall
sudo apt-get --purge remove nvidia-*
sudo apt-get purge nvidia*
sudo apt-get purge libnvidia*
```
直到命令不输出任何内容
```
sudo dpkg --list | grep nvidia-*
```
重启
重新安装驱动

## Ubuntu 20.04 在休眠之后，网络出现无法连接的问题
A: 重启network kernel modules/drivers
查找自己网络内核模块的型号：
``` 
sudo lshw -C network | grep dirver
```
找到 configuration：字段中driver=your_kernel_name
重启 i40e
```
sudo modprobe -r your_kernel_name
sudo modprobe -i your_kernel_name
```
从内核中添加或移除模块，可以不重启系统就扩充内核的功能
-r或--remove：模块闲置不用时，即自动卸载模块；
-i, --ignore-install, --ignore-remove

## 磁盘空间有，但是不能创建目录
df-h (查的磁盘的block数量)显示磁盘有空间，却显示：mkdir: cannot create directory `xxx’: No space left on device
df -i 索引节点 (inode)满了
查看到底哪个目录下面的文件最多
find /data1 -xdev -printf '%h\n' | sort | uniq -c | sort -k 1 -n


## 图形界面启动失败
 error while loading shared libraries: libatk-1.0.so.0: cannot
```
 sudo apt-get install libatk-bridge2.0-0
 （sudo apt-get install -y libatk-bridge2.0-0 libgtk-3.0）
```

## screen目录没有权限
Cannot make directory '/var/run/screen': Permission denied
```
sudo /etc/init.d/screen-cleanup start
```


