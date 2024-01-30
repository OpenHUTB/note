
# 虚拟机
[磁盘扩充容量](https://blog.csdn.net/qq_34160841/article/details/113058756) 
1. VMware 扩充容量；
2. 到虚拟机中使用分区编辑器进行扩容；
```shell
gparted
```


# 其他
去除chrome启动时需要输入密码：
启动seahorse，在“密码-login”下修改密码为空。

ubuntu gnome下 alt+tab 切换窗口设置 : 修改为不要合并窗口配置
1. 运行 dconf-editor
2. 打开: org/gnome/desktop/wm/keybindings
3. 可以看到, Tab 是放在了 switch-application 里面的（剪切Alt+Tab，并关闭使用默认）. 要把它拿出来, 放到 switch-windows 中.
4. switch application 就是 把相同的窗口合并. 这个就是罪魁祸首.
5. 保存. 立马生效.


UltraISO刻录Ubuntu镜像：
写入硬盘镜像->
便捷启动 -> 写入新的硬盘主引导记录（MBR） -> USB-HDD+ -> 写入

关闭显示器：
xset dpms force off
设置-设备-键盘-添加快捷键: Alt+Shift+-

执行apt-get install 报错：Errors were encountered while processing
清空/var/lib/dpkg/info目录下面的内容

sudo apt-get install cmake-curses-gui

Clearsigned file isn't valid, got 'NOSPLIT' (does the network require authentication?)
校园网需要授权，浏览器登录账号密码

安装OpenCV 3.4.1
wget https://github.com/opencv/opencv/archive/3.4.1.tar.gz


安装gcc 6.3
https://blog.csdn.net/yrc19950911/article/details/86184269
sudo apt-get install libgmp-dev

解压tar.bz2文件
tar -jxvf ×××.tar.bz2



解压  .tar.lz
sudo apt-get install lzip
lzip -d gmp-6.1.2.tar.lz
解压成:gmp-6.1.2.tar
tar -xvf gmp-6.1.2.tar

删除一个PPA源
1,到 源的 目 录:cd  /etc/apt/sources.list.d/
2,可以看 到 关 于 源的 文件,删除即可 .
实例：错误的安装ppa导致每次更新源都会载最后出现无法下载大情况，

sudo apt-get install gfortran
gfortran -v

查看用户zj运行的进程
ps -u zj 

资源管理器： gnome-system-monitor

修复grub开机引导：
set boot=(hd2,gpt8)       ??(root)
set prefix=/(hd2,gpt8)/boot/grub
insmod normal				// 启动normal启动
normal							// 进入熟悉的西东菜单栏
按C进入命令行模式
root=
prefix=
linux /vmlinuz-xxx-xxx root=/dev/sda8
initrd /initrd.img-xxx-xxx
boot

sudo update-grub
sudo grub-install /dev/sda


解决依赖的软件没有满足
包下载地址：https://ubuntu.pkgs.org

关闭防火墙：sudo ufw status

ALT + CTRL + F1
ps -t tty7来查看在终端7中运行的是什么进程
kill 9 PID (自动重新启动Xorg)

禁用Xorg使用GPU
在大多数的发向版本中此文件在 /etc/X11/xorg.conf
但是子ubuntu中X11下却没有这个文件。经过查看 /var/log/Xorg.0.log发现有这样一行：
[    18.913] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
创建文件：20-nvidia.conf
Section "Device"
	Identifier "MyGPU"
	Driver "nvidia"
	Option "Interactive" "0"
EndSection

添加软链接：
ln -s 源文件 目标文件
sudo ln -s /usr/local/cuda-8.0/lib64/stubs/libcuda.so /usr/local/cuda-8.0/lib64/stubs/libcuda.so.1

xy server is refusing connections火狐拒绝联网：
edit——>preference——>advanced——>Network——>settings选择'no proxy'点击下面'ok'即可。


vscode:
安装c++插件
Ctrl+P之后输入
ext install c++
重启VSCode生效

1. ctrl p
输入 >ext install，选择”扩展：安装扩展” 
2. 调用可执行程序执行代码
快捷键：ctrl+shift+D 或者是点击左侧的第三个图标（小虫子的图标）
点击设置图标，选择上面安装的扩展 C++(GDB) 
3. 对 launch.json 进行编辑（主要修改目标是program以及args）：
4. task.json
"command": "make"



下载工具
uget安装
启动uget: uget-gtk

****************************************


按物理硬盘查看硬盘信息：fdisk -l
mount /dev/sda1 /data

查看安装软件：dpkg -l | grep ftp

查看OpenCV版本
pkg-config --modversion opencv

https://github.com/ufoym/deepo
Install Docker and nvidia-docker.
sudo docker pull ufoym/deepo
sudo nvidia-docker run --rm ufoym/deepo nvidia-smi
sudo nvidia-docker run -it ufoym/deepo bash


CUDA NVCC target flags: -gencode;arch=compute_20,code=sm_20;-gencode;arch=compute_20,code=sm_21;-gencode;arch=compute_30,code=sm_30;-gencode;arch=compute_35,code=sm_35;-gencode;arch=compute_30,code=compute_30

-- Checking for module 'libavresample'
--   No package 'libavresample' found
-- CUDA detected: 9.0
-- CUDA NVCC target flags: -gencode;arch=compute_20,code=sm_20;-gencode;arch=compute_20,code=sm_21;-gencode;arch=compute_30,code=sm_30;-gencode;arch=computcode;arch=compute_30,code=compute_30
-- Found PythonInterp: /usr/bin/python2 (found suitable version "2.7.12", minimum required is "2.0")



安装teamviewer
wget https://download.teamviewer.com/download/linux/teamviewer_amd64.deb
sudo dpkg -r teamviewer		(dpkg -l | grep 'team')
sudo apt-get update
sudo apt-get install -f		（出现Errors were encountered while processing:teamviewer，需要安装丢失的依赖）
sudo dpkg -i teamviewer_amd64.deb
1014805571 (1953)

https://blog.csdn.net/pwb1994001/article/details/78528747
sudo teamviewer --passwd 12345678 #设置密码




ubuntu16.04下安装docker
开始安装
由于apt官方库里的docker版本可能比较旧，所以先卸载可能存在的旧版本：
$ sudo apt-get remove docker docker-engine docker-ce docker.io
更新apt包索引：
$ sudo apt-get update
安装以下包以使apt可以通过HTTPS使用存储库（repository）：
$ sudo apt-get install -y apt-transport-https ca-certificates curl software-properties-common
添加Docker官方的GPG密钥：
$ curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
使用下面的命令来设置stable存储库：
$ sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
再更新一下apt包索引：
$ sudo apt-get update
安装最新版本的Docker CE：
sudo apt-get install -y docker-ce
在生产系统上，可能会需要应该安装一个特定版本的Docker CE，而不是总是使用最新版本：
列出可用的版本：
apt-cache madison docker-ce
选择要安装的特定版本，第二列是版本字符串，第三列是存储库名称，它指示包来自哪个存储库，以及扩展它的稳定性级别。要安装一个特定的版本，将版本字符串附加到包名中，并通过等号(=)分隔它们：
sudo apt-get install docker-ce=<VERSION>
验证docker
查看docker服务是否启动：
systemctl status docker
若未启动，则启动docker服务：
sudo systemctl start docker
经典的hello world：
sudo docker run hello-world （需要运行两次）


nvidia-docker安装（https://github.com/NVIDIA/nvidia-docker）
docker volume ls -q -f driver=nvidia-docker | xargs -r -I{} -n1 docker ps -q -a -f volume={} | xargs -r docker rm -f
sudo apt-get purge -y nvidia-docker （在curl后面执行）
curl -s -L https://nvidia.github.io/nvidia-docker/gpgkey | \
  sudo apt-key add -
distribution=$(. /etc/os-release;echo $ID$VERSION_ID)
curl -s -L https://nvidia.github.io/nvidia-docker/$distribution/nvidia-docker.list | \
sudo tee /etc/apt/sources.list.d/nvidia-docker.list
sudo apt-get update    （如果报key错：sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys F60F4B3D7FA2AF80 ）
sudo apt-get install -y nvidia-docker2
sudo pkill -SIGHUP dockerd
sudo docker run --runtime=nvidia --rm nvidia/cuda nvidia-smi




sudo pip install shadowsocks 
sudo ssserver -p 4321 -k znjsyjy -m rc4-md5 --user nobody -d start

开机启动不到图形界面
/etc/X11/xorg.conf不见了
sudo cp xorg.conf.failsafe xorg.conf
sudo reboot


su: Authentication failure
sudo passwd
sudo passwd root

install vmware tools:
tar  zxf    vm..................gz(vmware tools文件明)
然后，进入解压的文件夹下，运行./vmware-install.pl


ps aux | grep ssh
sudo apt-get install openssh-server

统计文件大小
ls -l *.txt | awk 'BEGIN{sum=0} {sum+=$5} END {print sum}'


Ubuntu目录说明: http://www.cnblogs.com/ajianbeyourself/p/4187535.html
usr并不是user的缩写，而是Unix Software Resource的缩写，即“Unix 操作系统软件资源”放在该目录
/var 就是在系统运行过程中渐渐占用硬盘容量的目录。包括缓存cache，日志log，以及某些软件运行所产生的文件，包括程序文件（lock file, run file）

输入密码以解锁你的登录环

设置IP地址不可以保存（灰色）：新建管理员账户并用图形界面登录，设置IP保存，再用普通账户登录。

截图工具Shutter, 系统设置->Keyboard->Shortcut->Custom shortcuts

ubuntu中所谓super建，就是win建, 显示桌面的快捷键是 ctrl+super+D          http://www.oschina.net/news/33431/34-simple-and-useful-ubuntu-shortcuts
窗口最大化： ctrl+super+向上箭头
Super+w: 展开所有窗口
ctrl+H: 显示隐藏文件
Shift: 右击
Control + L：复制路径前得按Control + L组合键将路径显示出来
Ctrl+T: 在 Na    utilus 打开新的 Tab，再按ctrl+PgUp,Ctrl+PgDn
Ctrl+Q: 退出应用
Ctrl + 1/2: 修改文件夹视图为图标或者列表模式
Ctrl + Alt + F2(F3)(F4)(F5)(F6): 选择不同的虚拟终端
Ctrl + Alt + F7: 切换到当前登录会话
Alt + F7: 计划移动窗体选项，你可以使用键盘上的方向键来移动窗口
F9: 显示和关闭 Nautilus 边栏

双击 sogoupinyin_2.1.0.0082_amd64.deb
系统设置>语言支持>键盘输入方式系统，然后选择 fcitx 项
注销系统并重新登陆，在屏幕右上角就能看见输入法了，然后选择搜狗拼音就可使用并输入了。

sudo apt-get install terminator

http://blog.csdn.net/hanshileiai/article/details/45872423
whereis SecureCRT
sudo perl securecrt_linux_crack.pl /usr/bin/SecureCRT
每个信息手动填充：
Name:        xiaobo_l
Company:    www.boll.me
Serial Number:    03-61-166978
License Key:    ABC89D UFDU94 C94CBU 7V17SU ABTUS5 QXX9E5 PF12H6 R62SHC
Issue Date:    12-22-2013
显示彩色：
optins>session options
Terminal>emulation
xterm再勾选ASNI color，use color scheme
Apperence>current color scheme
选择traditional




uname -a        电脑以及操作系统的相关信息
cat /proc/version   运行的内核版本
cat /etc/issue      发行版本信息

sudo passwd root

sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
sudo vi /etc/apt/sources.list
sudo apt-get update

deb http://mirrors.163.com/ubuntu/ trusty main restricted universe multiverse 
deb http://mirrors.163.com/ubuntu/ trusty-security main restricted universe multiverse 
deb http://mirrors.163.com/ubuntu/ trusty-updates main restricted universe multiverse 
deb http://mirrors.163.com/ubuntu/ trusty-proposed main restricted universe multiverse 
deb http://mirrors.163.com/ubuntu/ trusty-backports main restricted universe multiverse 
deb-src http://mirrors.163.com/ubuntu/ trusty main restricted universe multiverse 
deb-src http://mirrors.163.com/ubuntu/ trusty-security main restricted universe multiverse 
deb-src http://mirrors.163.com/ubuntu/ trusty-updates main restricted universe multiverse 
deb-src http://mirrors.163.com/ubuntu/ trusty-proposed main restricted universe multiverse 
deb-src http://mirrors.163.com/ubuntu/ trusty-backports main restricted universe multiverse


# 默认注释了源码镜像以提高 apt update 速度，如有需要可自行取消注释
deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ xenial main restricted universe multiverse
# deb-src https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ xenial main restricted universe multiverse
deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ xenial-updates main restricted universe multiverse
# deb-src https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ xenial-updates main restricted universe multiverse
deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ xenial-backports main restricted universe multiverse
# deb-src https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ xenial-backports main restricted universe multiverse
deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ xenial-security main restricted universe multiverse
# deb-src https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ xenial-security main restricted universe multiverse


Q：curl不支持https协议
curl: (1) Protocol https not supported or disabled in libcurl
wget https://curl.haxx.se/download/curl-7.54.1.tar.gz
./configure --with-darwinsslsu 
make
sudo make install

su命令和su -命令区别就是：
su只是切换了root身份，但Shell环境仍然是普通用户的Shell；而su -连用户和Shell环境一起切换成root身份了。只有切换了Shell环境才不会出现PATH环境变量错误，报command not found的错误。

