
模型转换：
pip install -i https://pypi.tuna.tsinghua.edu.cn/simple/ onnx
pip install onnx-tf


apt-get install gnome-panel gnome-settings-daemon metacity nautilus gnome-terminal 
sudo gedit ~/.vnc/xstartup  
export XKL_XMODMAP_DISABLE=1  
unset SESSION_MANAGER  
unset DBUS_SESSION_BUS_ADDRESS    
[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup  
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources  
xsetroot -solid grey  vncconfig -iconic &  
x-terminal-emulator -geometry 1920x1080+0+0 -ls -title "$VNCDESKTOP Desktop" &gnome-panel &  
gnome-settings-daemon &  
metacity &  
nautilus &  
gnome-terminal & 
gnome-session &

xrdp

提交容器成为新的镜像，例如叫做ubuntu-ssh，输入docker commit 容器ID ubuntu-ssh
docker commit e22797f1efb9 gpu_flow
sudo nvidia-docker run -it --privileged gpu_flow bash （修改不可以修改core文件）
echo "core.%e.%t" > /proc/sys/kernel/core_pattern

/home/gpu_flow/build/compute_flow --gpuID=0 --type=1 --vid_path=/home/data/UCF-101 --out_path=/home/data/gesture/flow --stride=1
/home/gpu_flow/build/compute_flow --gpuID=0 --type=1 --vid_path=home/data/UCF-101/ApplyEyeMakeup --out_path=/home/data/gesture/flow --stride=1

sudo docker ps -a
sudo docker attach e22797f1efb9
sudo nvidia-docker run -it ufoym/deepo bash

运行停止的容器：sudo docker start e9d44081c56f
进入容器：docker attach e9d44081c56f

修改系统文件失败：
docker run -it --ulimit core=-1 --privileged testuser/debug_hacks /bin/bash

https://github.com/feichtenhofer/gpu_flow
sudo apt-get install cmake qt5-default qtcreator
sudo apt-get install libopencv-dev python-opencv
安装opencv依赖：apt-get install cmake git libgtk2.0-dev pkg-config libavcodec-dev libavformat-dev libswscale-dev
wget http://developer.download.nvidia.com/compute/cuda/6_5/rel/installers/cuda_6.5.14_linux_aarch64_native.run

PATH includes /usr/local/cuda-6.5/bin
LD_LIBRARY_PATH includes /usr/local/cuda-6.5/lib64, or, add /usr/local/cuda-6.5/lib64 to /etc/ld.so.conf and run ldconfig as root

/usr/lib/x86_64-linux-gnu/libopencv_highgui.so.2.4.9: undefined reference to `TIFFReadRGBAStrip@LIBTIFF_4.0'
编译opencv的时候要加上 -D BUILD_TIFF=ON
cmake -D CMAKE_BUILD_TYPE=RELEASE -D BUILD_TIFF=ON WITH_CUDA=ON ..
cmake -D BUILD_TIFF=ON .. （加上release或者cuda就报错：/usr/local/cuda/bin/nvcc: Syntax error: "(" unexpected     CMake Error at cmake/FindCUDA.cmake:604 (string):
https://blog.csdn.net/u014613745/article/details/78310916

git clone https://github.com/feichtenhofer/gpu_flow.git
wget http://crcv.ucf.edu/data/UCF101/UCF101.rar


这是交通手势识别的一些总结（在自己录制视频上测试的准确率）：
1.单张图片分类准确率：91%；在图片分类的基础上统计出现最多的手势作为视频预测结果的准确率：93%
2.利用时空特征进行交通手势视频分类的准确率：63%
结论：在网上提供数据集和自己采集数据集测试的效果发现，利用单张图片进行交通手势识别的准确率相比利用时空特征进行视频分类的准确率更高，加上图片序列投票的方式能进一步提高准确率，推荐此方法。




用所有数据进行测试：
go_straight
class sum: 565, predicted corrected: 565, accuracy: 1.000000
park_right
class sum: 471, predicted corrected: 421, accuracy: 0.893843
stop
class sum: 356, predicted corrected: 356, accuracy: 1.000000
turn_right
class sum: 455, predicted corrected: 341, accuracy: 0.749451
Sum: 1847, predicted corrected: 1683, accuracy: 0.911207


81.181 s
103+157+86+102=448
0.1812 s

原来91%的模型，用自己的数据测试
Sum: 1847, predicted corrected: 581, accuracy: 0.314564

边框刚好框住手，而不是有多余的；人面对的方向和蓝色墙壁平行
go_straight（应该从右后45度(135度)拍摄，第一帧就是双臂打开，朝右看）
class sum: 565, predicted corrected: 44, accuracy: 0.077876
park_right（右边40度拍摄）
class sum: 471, predicted corrected: 291, accuracy: 0.617834
stop（右边40度拍摄）
class sum: 356, predicted corrected: 246, accuracy: 0.691011
turn_right（从右后40度拍摄（130度）拍摄，
class sum: 455, predicted corrected: 0, accuracy: 0.000000
Sum: 1847, predicted corrected: 581, accuracy: 0.314564


DL(Visual Geometry)
http://www.robots.ox.ac.uk/~vgg/software/two_stream_action/#sec-code
https://github.com/feichtenhofer/twostreamfusion
UCF101数据集：http://crcv.ucf.edu/data/UCF101/

INRIA组的Improved Dense Trajectories(IDT)
sudo add-apt-repository --yes ppa:xqms/opencv-nonfree
sudo apt-get update 
sudo apt-get install libopencv-nonfree-dev
sudo add-apt-repository ppa:kirillshkrogalev/ffmpeg-next 
sudo apt-get update 
sudo apt-get install ffmpeg
局部时空特征构造视频表示+SVM
D:\workspace\traffic-gesture-recognition\Action Recognition Code

重新涂了背景的stop
Sum: 73, predicted corrected: 4, accuracy: 0.054795
原来
Sum: 65, predicted corrected: 37, accuracy: 0.569231


采集4个人4中姿势：Sum: 1847, predicted corrected: 746, accuracy: 0.403898

tensorflow训练模型测试(测试集准确度60%)：Sum: 489, predicted corrected: 413, accuracy: 0.844581
xiongjingjing视频(go_straight+stop)：Sum: 185, predicted corrected: 155, accuracy: 0.837838


使用官方图片作为测试集
File number:  131
Accuracy:  0.9389312977099237
自己拍的图片：
直行：173张，准确率1.0
stop: 79张，准确率0.0


训练时删除了flow_from_directory里的classes分类，keras自动进行分类（不然就只会读取一类，导致正确率始终为1）


模型(models/inception_v4.py)：
https://github.com/titu1994/Inception-v4/releases/
ros_gesture_detection.py	tf.keras.models.load_model() 从模型路径加载警察、姿势的模型（这个训练好的模型从哪里来，从train.py中训练来？）
初始化GestureRecog __init__()的时候回调self.process -> predict_policeman() 和  detect_gesture()，分别调用模型的predict()

train.py  main() ->  load_model() -> inception_v4.py  load_weight()
有权重就加载Inception-v4权重（-w 作为训练的初始权重）到inception-v4模型，训练完保存模型



https://blog.csdn.net/liaoshenglan/article/details/78484851
opencv2
sudo apt-get install libcv-dev
sudo apt-get install cmake qt5-default qtcreator
sudo apt-get install ros-indigo-desktop-full ros-indigo-nmea-msgs ros-indigo-nmea-navsat-driver ros-indigo-sound-play ros-indigo-jsk-visualization ros-indigo-grid-map ros-indigo-gps-common
sudo apt-get install ros-indigo-controller-manager ros-indigo-ros-control ros-indigo-ros-controllers ros-indigo-gazebo-ros-control ros-indigo-sicktoolbox ros-indigo-sicktoolbox-wrapper ros-indigo-joystick-drivers ros-indigo-novatel-span-driver
sudo apt-get install libnlopt-dev freeglut3-dev qtbase5-dev libqt5opengl5-dev libssh2-1-dev libarmadillo-dev libpcap-dev gksu libgl1-mesa-dev libglew-dev

sudo apt-get install -y  python-catkin-pkg python-rosdep python-wstool ros-$ROS_DISTRO-catkin
sudo add-apt-repository ppa:mosquitto-dev/mosquitto-ppa
sudo apt-get update
sudo apt-get install libmosquitto-dev

git clone https://github.com/CPFL/Autoware.git --recurse-submodules


Creating symlink "/home/dong/Autoware/ros/src/CMakeLists.txt" pointing to "/opt/ros/indigo/share/catkin/cmake/toplevel.cmake"


tensorflow:
sudo apt-get install python3-pip
sudo pip3 install https://storage.googleapis.com/tensorflow/linux/cpu/tensorflow-1.2.1-cp34-cp34m-linux_x86_64.whl
sudo pip3 install https://storage.googleapis.com/tensorflow/linux/cpu/tensorflow-1.4.1-cp34-cp34m-linux_x86_64.whl
测试：
import tensorflow as tf
a=tf.constant([1.0,2.0,3.0],shape=[3],name='a')
b=tf.constant([1.0,2.0,3.0],shape=[3],name='b')
c=a+b
sess=tf.Session(config=tf.ConfigProto(log_device_placement=True))
print(sess.run(c))


ImportError: `load_weights` requires h5py.
sudo apt-get install cython
sudo apt-get install libhdf5-dev
sudo pip3 install h5py

sudo pip3 install pillow
sudo apt-get install gfortran
sudo pip3 install scipy		(--default-timeout=100)























sudo apt-get install python-pip python-dev
sudo pip3 install tensorflow