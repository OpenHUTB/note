
dependency engine：基础的调度引擎，尽量发掘并行性；
symbolic graph: 预先优化graph，减少内存用量，优化后的操作丢给dependency engine执行；
expression template：C++模板，属于静态编译优化，只能在一个计算单元内部使用，不能用于动态调度；

加速的预测库
Convolution
	NCHW to NHWC(channel)
BLAS (定点化优化)
Quantization

编译到不同平台
Android(jni)
Raspberry Pi(树莓派)



Gradle是一个基于Apache Ant和Apache Maven概念的项目自动化构建工具

Halide是由MIT、Adobe和Stanford等机构合作实现的图像处理语言，它的核心思想即解耦算法和优化，事实也证明它是成功的，
在各种实例中它均以几分之一的代码量实现出同等或者数倍于手工C++代码的效能，更不用提代码的可维护性和开发效率。

NNVM（用于任务调度和内存管理的高级中间表示），另一层是TVM（用于优化计算内核的富有表现力的低级中间表示）

TVM: 一种将深度学习工作负载部署到硬件的端到端IR（中间表示）堆栈。
换一种说法，可以表述为一种把深度学习模型分发到各种硬件设备上的、端到端的解决方案。
intermediate representation （中间表示）

General matrix multiply(GEMM)

Intel MKL，全称 Intel Math Kernel Library，提供经过高度优化和大量线程化处理的数学例程，面向性能要求极高的科学、工程及金融等领域的应用。MKL是一款商用函数库，提供C、Fortran 和 Fortran 95的支持，但仅支持Intel自家旗下的CPU。
在Intel CPU上，MKL的性能要远高于Eigen, 虽然OpenBLAS和其差距不是太大，但OpenBLAS提供的函数太少。

预测库源码：
https://github.com/apache/incubator-mxnet/blob/50564bd7261fafe6aee809a23e8a1173fe060ea1/example/image-classification/predict-cpp/image-classification-predict.cc
MXPredCreate：创建一个predictor
      SetInput：设置predictor的输入
      Forward：输入handle，进行forward操作
      GetOutputShape：获取输出结果的shape，可以用这个shape申请保存结果的空间
      GetOutput：获取计算结果
      Free：释放

风格迁移
在图像内容附近通过白噪声初始化一个输出结果，然后通过网络对这个结果进行风格和内容两方面的约束进行修正。
特定层来匹配样式，特定层来匹配内容。
越靠近输入层越容易匹配内容和样式的细节信息，越靠近输出层越倾向于语义的内容和全局样式。
风格的度量用Gram矩阵：有自己的特征才叫做风格，自己的特点越突出，别人的越不突出最好。
在同一个维度上面的值相乘的时候原来越小就变得越小，越大就变得越来；不同维度上的关系也在相乘的表达式中表示出来。
靠近输出层，学到的图片里有大量高频噪音。


SSD: Single Shot MultiBox Detector
Intersection over Union (IoU)


feature map 由卷积核(Fliter) 和输入做卷积运算得到

Adagrad:让模型中每个元素都是用不同学习速率的优化方法；
如果模型损失函数有关一个参数元素的偏导数一直都较大，那么就让它的学习率下降快一点；反之，如果模型损失函数有关一个参数元素的偏导数一直都较小，那么就让它的学习率下降慢一点。

RMSProp使用了梯度按元素平方的指数加权移动平均变量来调整学习率。


win10简易安装：
1.安装cuda_8.0.44_win10.exe
2.安装Anaconda3-4.3.0-Windows-x86_64.exe
3.pip install --pre mxnet-cu80 -i https://pypi.douban.com/simple

Ubuntu：
1.安装Python  1 apt-get install python 
2.安装Git   1 apt-get install git 
3.安装依赖包  1 apt-get install -y build-essential git libatlas-base-dev libopencv-dev 
4.从Github上获取代码  1 git clone --recursive https://github.com/dmlc/mxnet 
5.进入到Mxnet目录进行编译命令如下：
   1 cd mxnet/ 2 make -j$(nproc) #利用多核特性 
6.安装Python的必备库
   1 apt-get install python-setuptools 
   2 apt-get install python-numpy 
7.安装Python支持，进入Mxnet下的Python目录执行如下命令
   1 python setup.py install 
8.进入example目录下的image-classification目录执行如下命令：
  1 python train_mnist.py 

编译mxnet
http://blog.csdn.net/huareal/article/details/74085513

安装OpenBLAS
git clone https://github.com/xianyi/OpenBLAS.git
make  –j4
make PREFIX=/home/wanghaidong/mxnet/software/openblas  install

安装python
wget https://www.python.org/ftp/python/2.7.9/Python-2.7.9.tgz
python setup.py install --prefix=/home/wanghaidong/mxnet/mxnet/python/install 
./configure --prefix=/home/wanghaidong/mxnet/software/python27
make -j4
make install
python -V
vi ~/.bashrc
export PATH=/home/wanghaidong/mxnet/software/python27/bin:$PATH

setuptools
wget https://pypi.python.org/packages/e9/93/e53fb79dbf5f4a1407feed7a19ea6d0e83765b354754e003cce7aa12b976/setuptools-28.8.0.zip#md5=0983d2f68bb4c73f9e7331883fa39220
unzip setuptools-28.8.0.zip
python setup.py install（如果有两个python，将python3安装就python3代替python）

pip
wget "https://pypi.python.org/packages/source/p/pip/pip-1.5.4.tar.gz#md5=834b2904f92d46aaa333267fb1c922bb" --no-check-certificate
python setup.py install

graphviz-0.8.1
wget https://pypi.python.org/packages/a9/a6/ee6721349489a2da6eedd3dba124f2b5ac15ee1e0a7bd4d3cfdc4fff0327/graphviz-0.8.1.zip#md5=88d8efa88c02a735b3659fe0feaf0b96

requests-2.18.4
wget https://pypi.python.org/packages/b0/e1/eab4fc3752e3d240468a8c0b284607899d2fbfb236a56b7377a329aa8d09/requests-2.18.4.tar.gz#md5=081412b2ef79bdc48229891af13f4d82 

numpy
wget https://pypi.python.org/packages/bf/2d/005e45738ab07a26e621c9c12dc97381f372e06678adf7dc3356a69b5960/numpy-1.13.3.zip#md5=300a6f0528122128ac07c6deb5c95917


编译mxnet
git clone --recursive https://github.com/dmlc/mxnet
cp make/config.mk .
ADD_LDFLAGS = '-L/home/wanghaidong/mxnet/software/openblas/lib'
ADD_CFLAGS = '-l/home/wanghaidong/mxnet/software/openblas/include'
USE_BLAS = openblas
USE_OPENCV = 0
make -j4
cd python
python setup.py install
(python setup.py install --prefix=/home/wanghaidong/mxnet/software/python27 （后面接/lib/python2.7/site-packages/）)

cd mxnet/example/image-classification
python train_mnist.py


远程调式python
(easy_install pycharm-debug.egg      (PyCharm 2017.3\debug-eggs))



