
显卡驱动384->375
data/log/EROOR

进入dev容器：bash docker/scripts/dev_into.sh
编译模块：		bash apollo.sh build
编译包含视觉模块和优化：	bash apollo.sh build_opt_gpu
启动相机模块：			bash docker/scripts/usb_camera.sh
获取图片：
perception\obstacle\onboard\camera_process_subnode.cc
ImgCallback()  
FLAGS_image_file_debug=1; 从文件路径读取图片
FLAGS_image_file_path = "/apollo/";
重新编译，运行.sh脚本(percepton_lowcost.sh)启动节点，然后显示图片。
perception.sh
run perception "$@"  运行所有脚本参数的内容
最终将逻辑放到一个新的节点


设置了/boot, swap, /
/和/usr目录太小
vim
openssh-server
nvidia-dirver, cuda, 
cuDNN(runtime,developer,code samples)    https://blog.csdn.net/Nicholas_Wong/article/details/77687949
anaconda
tensorflow
pycharm (Bazal)		https://blog.csdn.net/elaine_bao/article/details/78668657
apollo
docker
vs code   (https://www.cnblogs.com/fuhang/p/8778190.html)



nvidia驱动安装：
sudo add-apt-repository ppa:graphics-drivers/ppa
sudo apt-get update
ubuntu-drivers devices
sudo apt-get install nvidia-XXX  （vidia-384+关闭secure boot）必须是375 和apollo保持一致
CUDA安装：*.run --no-opengl-files -a –s

nvcc -V 找不到：sudo apt-get install nvidia-cuda-toolkit


循环登录：（关闭安全引导）
sudo apt-get remove --purge nvidia-*
sudo apt-get install ubuntu-desktop
sudo rm /etc/X11/xorg.conf
echo 'nouveau' | sudo tee -a /etc/modules
#重启系统
sudo reboot




127.0.0.1 failed: Connection refused.  因为设置了代理
env | grep -i proxy		查看本机代理使用情况
释放所显示的端口占用：
export http_proxy=""
export https_proxy=""
export HTTP_PROXY=""
export HTTPS_PROXY=""


启动docker服务：sudo  service  docker  start
解压3.0的源代码：
sudo bash docker/scripts/release_start.sh （记得要sudo）
sudo bash docker/scripts/release_into.sh
(sudo python docs/demo_guide/rosbag_helper.py demo_2.0.bag #download rosbag)
rosbag play demo_2.0.bag --loop


vscode:
./bin/code --user-data-dir=.

Bazel
https://docs.bazel.build/versions/master/install-ubuntu.html
sudo apt-get install pkg-config zip g++ zlib1g-dev unzip python



图片分类：
https://blog.csdn.net/Missayaaa/article/details/79119839
代码：百度网盘\code\picture.zip
googlenet:	https://blog.csdn.net/akadiao/article/details/78634431











1.安装Ubuntu14.04

2.安装Ros-indigo
sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu trusty main" > /etc/apt/sources.list.d/ros-latest.list'
wget http://packages.ros.org/ros.key -O - | sudo apt-key add -  
sudo apt-get update
sudo apt-get install ros-indigo-desktop-full
初始化ros
sudo rosdep init (若提示rosdep update 则执行rosdep update)
设置环境变量(终端执行roscore进行测试)
echo "source /opt/ros/indigo/setup.bash" >> ~/.bashrc  
source ~/.bashrc

3.安装apollo-kernel（实时内核补丁，对linux内核的修改）
tar zxvf linux-4.4.32-apollo-1.5.0.tar.gz
cd install
sudo ./install_kernel.sh

4.安装apollo-platform（对ros修改，使其达到实时共享内存通信）
下载apollo-platform并解压
https://github.com/ApolloAuto/apollo-platform/releases/download/2.1.2/ros-indigo-apollo-2.1.2-x86_64.tar.gz
下载Apollo本体的源码：
git clone https://github.com/ApolloAuto/apollo.git  (https://github.com/ApolloAuto/apollo/archive/v3.0.0.tar.gz)
将文件夹中的ros拷贝到apollo工程中：
rsync -av ros/ ~/apollo/third_party/ros_x86_64
apollo目录下执行：
source ./third_party/ros_x86_64/setup.bash

5.安装Apollo本体
安装docker环境：
cd ~/apollo
bash docker/scripts/install_docker.sh
先注销再重新登录，然后测试一下docker是否安装成功：
docker ps
设置环境：
bash docker/scripts/release_start.sh -C
bash docker/scripts/release_into.sh
进入Docker，再执行如下命令，启动Dreamview服务端程序：bash scripts/bootstrap.sh	(参考：https://www.csdn.net/article/a/2018-04-24/15946728)

运行rosbag play之前必须运行roscore
rosbag play demo_2.5.bag --loop



https://blog.csdn.net/davidhopper/article/details/79819587
安装Visual Studio Code
sudo add-apt-repository ppa:ubuntu-desktop/ubuntu-make
sudo apt-get update
sudo apt-get install ubuntu-make
umake web visual-studio-code
~/.local/share/umake/web/visual-studio-code$ ./code


(sudo bash docker/scripts/dev_start.sh
sudo bash docker/scripts/dev_into.sh)
编译：
bash apollo.sh build

6.apollo测试
cd ~/apollo
bash docker/scripts/dev_start.sh
bash docker/scripts/dev_into.sh 
source ./third_party/ros_x86_64/setup.bash     //执行后可以在docker下使用ros
sh scripts/hmi.sh      //进入交互环境
在浏览器输入http://localhost:8887后回车，出现以下界面开启Dreamview，然后点击右上方的Dreamview。
新开一个终端里输入：
rosbag play -l ./docs/demo_guide/demo.bag
然后就可以看到界面播放demo.bag数据啦





