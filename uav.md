OpenCV在Jetson TK1上的安装和使用
http://www.myexception.cn/other/1829048.html
http://www.cnblogs.com/platero/p/3993877.html

1、Jetson TK1平台的OpenCV优化包下载

下载地址：https://developer.nvidia.com/linux-tegra-rel-19（需要注册才可以下载）


2、使能通用存储库和更新apt-get
sudo apt-add-repository universe
sudo apt-get update


3、安装OpenCV优化包
sudo dpkg -i libopencv4tegra_2.4.8.2_armhf.deb
sudo dpkg -i libopencv4tegra-dev_2.4.8.2_armhf.deb


4、安装一些函数库
# Some general development libraries
sudo apt-get install build-essential make cmake cmake-curses-gui g++
# libav video input/output development libraries
sudo apt-get install libavformat-dev libavutil-dev libswscale-dev
# Video4Linux camera development libraries
sudo apt-get install libv4l-dev
# Eigen3 math development libraries
sudo apt-get install libeigen3-dev
# OpenGL development libraries (to allow creating graphical windows)
sudo apt-get install libglew1.6-dev
# GTK development libraries (to allow creating graphical windows)
sudo apt-get install libgtk2.0-dev


5、下载OpenCV源码

下载地址：http://opencv.org/（注意选择OpenCV for Linux/Mac）

或者在TK1平台上直接下载，方法是：

wget http://downloads.sourceforge.net/project/opencvlibrary/opencv-unix/2.4.9/opencv-2.4.9.zip


6、解压OpenCV源码，并进行配置
cd Downloads
unzip opencv-2.4.9.zip
mv opencv-2.4.9 ~
cd ~/opencv-2.4.9
mkdir build

cmake -DWITH_CUDA=ON -DCUDA_ARCH_BIN="3.2" -DCUDA_ARCH_PTX="" -DBUILD_TESTS=OFF -DBUILD_PERF_TESTS=OFF

sudo make -j4 install

注意，中途可能会报错
opencv-2.4.9/modules/gpu/src/nvidia/core/NCVPixelOperations.hpp(51): error: a storage class is not allowed in an explicit specialization
解决方法在此：http://code.opencv.org/issues/3814  下载 NCVPixelOperations.hpp 替换掉opencv2.4.9内的文件， 重新build。
OpenCV isn't compatible with CUDA 6.5 (Bug #3814) 


8、make sure your system searches the "/usr/local/lib" folder for libraries

Finally, make sure your system searches the "/usr/local/lib" folder for libraries:

echo "# Use OpenCV and other custom-built libraries." >> ~/.bashrc
echo "export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/local/lib/" >> ~/.bashrc
source ~/.bashrc


9、测试OpenCV并运行几个例子

# Make sure we have installed a C++ compiler.
sudo apt-get install build-essential g++

第一个示例：
# Test a simple OpenCV program. Creates a graphical window, hence you should plug a HDMI monitor in or use a remote viewer such as X Tunneling or VNC or TeamViewer on your desktop.
cd ~/opencv-2.4.9/samples/cpp
g++ edge.cpp -lopencv_core -lopencv_imgproc -lopencv_highgui -o edge
./edge

第二个示例：
# If you have a USB webcam plugged in to your board, then test one of the live camera programs.
g++ laplace.cpp -lopencv_core -lopencv_imgproc -lopencv_highgui -lopencv_calib3d -lopencv_contrib -lopencv_features2d -lopencv_flann -lopencv_gpu -lopencv_legacy -lopencv_ml -lopencv_objdetect -lopencv_photo -lopencv_stitching -lopencv_superres -lopencv_video -lopencv_videostab -o laplace
./laplace
（注意：此示例没有演示出来，待解决。。。，错误提示见上图。）

第三个示例：
# Test a GPU accelerated OpenCV sample.
cd ../gpu
g++ houghlines.cpp -lopencv_core -lopencv_imgproc -lopencv_highgui -lopencv_calib3d -lopencv_contrib -lopencv_features2d -lopencv_flann -lopencv_gpu -lopencv_legacy -lopencv_ml -lopencv_objdetect -lopencv_photo -lopencv_stitching -lopencv_superres -lopencv_video -lopencv_videostab -o houghlines
./houghlines ../cpp/logo_in_clutter.png




Cannot get gpu opencv 2.4.10 to work. Cuda 6.5, Intel C++ 15. GCC 4.6-4.9, Ubuntu 14.10 (Bug #4115)
Description

GTX 760, Ubuntu 14.10, tried Intel c++ 15 (with CUDA hack), GCC from 4.6 to 4.9.

"cmake -D CMAKE_BUILD_TYPE=RELEASE -D CMAKE_INSTALL_PREFIX=/usr/local -D WITH_CUBLAS=ON -D WITH_CUFFT=ON -D WITH_EIGEN=ON -D WITH_OPENGL=ON -D WITH_QT=ON -D WITH_TBB=ON -D BUILD_DOCS=ON -D BUILD_EXAMPLES=ON -D BUILD_TESTS=ON -D CUDA_ARCH_BIN="3.0" .."

Purged system of 2.4.9 but seems "/build/buildd/opencv-2.4.9+dfsg..." (below) still there. Also openGlut problems on openCV examples.

"OpenCV Error: No GPU support (The library is compiled without CUDA support) in mallocPitch, file /build/buildd/opencv-2.4
.9+dfsg/modules/dynamicuda/include/opencv2/dynamicuda/dynamicuda.hpp, line 126
terminate called after throwing an instance of 'cv::Exception'
what(): /build/buildd/opencv-2.4.9+dfsg/modules/dynamicuda/include/opencv2/dynamicuda/dynamicuda.hpp:126: error: (-216
) The library is compiled without CUDA support in function mallocPitch"

install opencv4tegra again

********************************************************************
Ubuntu ARM install of ROS Indigo

armv7l armhf
ROS for Ubuntu Trusty armhf

1. Configure your Ubuntu repositories
win+ "Software Sources"
Configure your Ubuntu repositories to allow "restricted," "universe," and "multiverse."

2. Set your Locale
sudo update-locale LANG=C LANGUAGE=C LC_ALL=C LC_MESSAGES=POSIX

3. Setup your sources.list
sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu trusty main" > /etc/apt/sources.list.d/ros-latest.list'

4. Set up your keys
sudo apt-key adv --keyserver hkp://ha.pool.sks-keyservers.net --recv-key 0xB01FA116

5. Installation
sudo apt-get update (twice)
sudo apt-get install ros-indigo-ros-base
sudo apt-get install ros-indigo-navigation
(apt-cache search ros-indigo)

6. Initialize rosdep
sudo apt-get install python-rosdep
sudo rosdep init
rosdep update

7. Environment setup
echo "source /opt/ros/indigo/setup.bash" >> ~/.bashrc
source ~/.bashrc

8. Getting rosinstall
sudo apt-get install python-rosinstall

9. Verifying OS name
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=14.04
DISTRIB_CODENAME=trusty
DISTRIB_DESCRIPTION="Ubuntu 14.04"

(10. Build farm status)




































