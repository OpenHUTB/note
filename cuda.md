

# 下载文件
[CUDA 11.5](https://developer.download.nvidia.com/compute/cuda/11.5.1/local_installers/cuda_11.5.1_495.29.05_linux.run)

[CUDA 11.0](http://developer.download.nvidia.com/compute/cuda/11.0.2/local_installers/cuda_11.0.2_450.51.05_linux.run)

[CUDA 10.2](https://developer.download.nvidia.com/compute/cuda/10.2/Prod/local_installers/cuda_10.2.89_440.33.01_linux.run)

[CUDA 10.1](https://developer.nvidia.cn/compute/cuda/10.1/Prod/local_installers/cuda_10.1.168_418.67_linux.run)

[CUDA 10.0](https://developer.nvidia.cn/compute/cuda/10.0/Prod/local_installers/cuda_10.0.130_410.48_linux)

## 版本对应关系
检查当前机器合适的驱动
```shell script
ubuntu-drivers devices

sudo systemctl isolate multi-user.target
sudo modprobe -r nvidia-drm
```

tensorflow-gpu v1.9.0 | cuda9.0 |  cuDNN7.1.4可行  | 备注：7.0.4/ 7.0.5/ 7.1.2不明确

tensorflow-gpu v1.8.0 | cuda9.0 |  cuDNN  不明确 | 备注：7.0.4/ 7.0.5/ 7.1.2/ 7.1.4

tensorflow-gpu v1.7.0 | cuda9.0 |  cuDNN  不明确 | 备注：7.0.4/ 7.0.5/ 7.1.2/ 7.1.4

tensorflow-gpu v1.6.0 | cuda9.0 |  cuDNN  不明确 | 备注：7.0.4/ 7.0.5/ 7.1.2/ 7.1.4

tensorflow-gpu v1.5.0 | cuda9.0 |  cuDNN  不明确 | 备注：7.0.4/ 7.0.5/ 7.1.2/ 7.1.4

tensorflow-gpu v1.4.0 | cuda8.0 |  cuDNN 6.0 | 备注：6.0正常使用, 7.0.5不能用，5.1未知
 
tensorflow-gpu v1.3.0 | cuda8.0 |  cuDNN 6.0 | 备注：6.0正常使用, 7.0.5不能用，5.1未知 

tensorflow-gpu v1.2.0 | cuda8.0 |  cuDNN 5.1 | 备注：5.1正常使用, 6.0/ 7.0.5 未知

tensorflow-gpu v1.1.0 | cuda8.0 |  cuDNN 5.1 | 备注：5.1正常使用, 6.0/ 7.0.5 未知


# 问题

## NVIDIA-SMI has failed because it couldn't communicate with the NVIDIA driver. Make sure that the latest NVIDIA driver is installed and running
主要原因是系统内核升级了，导致新版本内核和原来显卡驱动不匹配
```commandline
sudo apt-get install dkms
sudo dkms install -m nvidia -v 440.44 
```
440.44表示的是驱动版本号。
利用命令ll /usr/src/可查看下面有一个nvidia-440.44文件夹，版本号因电脑而异。

compile gpu_burn
Q: /usr/bin/ld: cannot find -lcublas
A:
locate libculas.so
export LIBRARY_PATH=/path/to/your/cuda/lib64:${LIBRARY_PATH}
LIBRARY_PATH环境变量用于在程序编译期间查找动态链接库时指定查找共享库的路径
LD_LIBRARY_PATH环境变量用于在程序加载运行期间查找动态链接库时指定除了系统默认路径之外的其他路径
开发时，设置LIBRARY_PATH，以便gcc能够找到编译时需要的动态链接库。
发布时，设置LD_LIBRARY_PATH，以便程序加载运行时能够自动找到需要的动态链接库。

nvidia-smi -q
查询所有GPU的当前详细信息

GPU开启持久模式(persistence mode)，保证你的NVIDIA驱动即使没有应用正在运行也是出于加载状态的
sudo nvidia-smi -pm 1

nsight 启动eclipse

直接安装所有的NVIDIA的加速驱动，然后进入黑屏，进入第一个修复模式（第二项），选择dpkg的修复选项
【1】安装驱动
1. 卸载系统里的Nvidia低版本显卡驱动
sudo apt-get purge nvidia*
2.把显卡驱动加入PPA
sudo add-apt-repository ppa:graphics-drivers
sudo apt-get update
3. 使用终端命令查看Ubuntu推荐的驱动版本：
ubuntu-drivers devices
4. 采用apt-get命令在终端安装：
sudo apt-get install nvidia-384 nvidia-settings nvidia-prime
4.重启系统并验证，在终端输入以下命令行：
lsmod | grep nvidia
如果没有输出，则安装失败
5. Ubuntu自带的nouveau驱动是否运行：
lsmod | grep nouveau
如果终端没有内容输出，则显卡驱动的安装成功

【2】安装CUDA
1. 删除显卡驱动残留
sudo apt-get remove --purge nvidia*
sudo dpkg --forcel-all -P nvidia-384  (需要全名)
2. 使驱动管理休眠
sudo service lightdm stop
cd到所下载显卡驱动文件位置,执行:    
sudo ./NVIDIA-Linux-x86_64-390.25.run      (此处换成你所对应的文件名)
执行run文件前可能需要先使该文件增加可执行属性:    chmod +x NVIDIA-Linux-x86_64-390.25.run
在第一次确认是否安装acceleration driver时，选择no，因为前面已经安装好驱动了。如果这里选yes，很可能会出现无法登陆桌面的情况（循环登录）
5. 叫醒display manager 
sudo service lightdm start



ImportError: libcuda.so.1: cannot open shared object file: No such file or directory
将/usr/lib/x86_64-linux-gnu目录添加到LD_LIBRARY_PATH中。
驱动版本384.81，对应cuda版本为9.0
将.so文件和链接直接拷贝到/usr/lib下
/usr/local/cuda-8.0/lib64/stubs$ sudo cp libcuda.so* /usr/lib

cudnn 安装 cudnn-9.0-linux-x64-v7.tgz
sudo cp cuda/include/cudnn.h /usr/local/cuda/include
3 sudo cp cuda/lib64/libcudnn* /usr/local/cuda/lib64
4 sudo chmod a+r /usr/local/cuda/include/cudnn.h /usr/local/cuda/lib64/libcudnn*

查看cudnn版本：
cat /usr/local/cuda/include/cudnn.h | grep CUDNN_MAJOR -A 2
（-A 2）显示后面两行

查看CUDA版本
cat /usr/local/cuda/version.txt

sudo dpkg --list | grep NVIDIA-*
lspci | grep -i vga
lspci -v -s 01:00.0
nvidia-smi

测试tensoflow是否使用GPU进行计算
import tensorflow as tf
sess = tf.Session(config=tf.configProto(log_device_placement=True))


http://www.cnblogs.com/lvchaoshun/p/6411697.html

lspci | grep -i nvidia
在安装cuda时，会出现提示，询问你是否需要安装 openGL Libraries。
如果你的电脑是双显，而且用来显示的那块GPU不是NVIDIA，则OpenGL Libraries就不应该安装，
否则不是NVIDIA的那块GPU使用的OpenGL Libraries会被覆盖，然后GUI就无法工作了

http://blog.sina.com.cn/s/blog_51fad6900102wlmx.html

ctrl+alt+f1进入命令行模式，禁用lightdm图形界面管理器，卸载之前所有的nvidia驱动，将开源驱动加入黑名单，
然后运行相应的cuda安装run文件，由于现在版本的cuda都自带显卡的驱动，所以不需要单独安装GPU的驱动，最后一步重新启动lightdm并且重启即可。

