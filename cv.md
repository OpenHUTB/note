




# 其他
deinterlacer 去交错
Hough变换是图像处理中从图像中识别几何形状的基本方法之一。Hough变换的基本原理在于利用点与线的对偶性，
FIR(Finite Impulse Response)滤波器：有限长单位冲激响应滤波器，可以在保证任意幅频特性的同时具有严格的线性相频特性。
Kanade-Lucas-Tomasi(KLT)进行目标跟踪

multiple view geometry in computer vision 计算机视觉中的多视图几何
Bundle Adjustment  光束法平差(是一个优化模型，其目的是最小化重投影误差)

图片的随机剪裁（random crop）IRC

模式分类方法主要分为两类，
一类是生成式方法，比如GMM，这类方法主要反映同类数据之间的相似度；
一类是判别式方法，比如SVM，主要是反映异类数据之间的差异。

 fisher kernel被应用于图像分类的主要思路是，用生成式模型(GMM)对样本输入进行建模，进而得到样本的一种表示(fisher vector)，
 再将这种表示(fisher vector)输入判别式分类器(SVM)得到图像分类结果。
 fisher vector是fisher kernel中对样本特征的一种表示，它把一幅图片表示成一个向量。 

Bag of Feature 是一种图像特征提取方法，它借鉴了文本分类的思路（Bag of Words），从图像抽象出很多具有代表性的「关键词」，形成一个字典，再统计每张图片中出现的「关键词」数量，得到图片的特征向量。
bag of words（BOW）是文档的一种建模方法，它可以把一个文档表示成向量数据。
把一幅图看成一个文档，图片分割成的patch对应的sift特征看成单词；
 1）把图像分割成一个个patch，并对每个patch的中心点计算sift特征。sift算法可以提取图像中的局部不变特征，这一步是做dense sift.
 2）利用kmeans算法，将这些patch的中心点的sift特征聚成为k个类，用这k个聚类中心来构造单词表

方向梯度直方图（Histogram of Oriented Gradient, HOG）特征（行人检测），通过计算和统计图像局部区域的梯度方向直方图来构成特征。
LBP（Local Binary Pattern，局部二值模式）是一种用来描述图像局部纹理特征的算子；
	3*3邻域内的8个点经比较可产生8位二进制数（通常转换为十进制数即LBP码，共256种），即得到该窗口中心像素点的LBP值，并用这个值来反映该区域的纹理信息
Haar-like特征（人脸）：定义该模板的特征值为白色矩形像素和减去黑色矩形像素和。Haar特征值反映了图像的灰度变化情况。Viola-Jones算法
Blob分析(Blob Analysis)是对图像中相同像素的连通域进行分析，该连通域称为Blob。Blob分析可为机器视觉应用提供图像中的斑点的数量、位置、形状和方向，还可以提供相关斑点间的拓扑结构。

HOF(Histogramsof Oriented Optical Flow)与HOG类似，是对光流方向进行加权统计，得到光流方向信息直方图

Harris Corner是最典型的角点检测子Corner Detector。角点经常被检测在边缘的交界处、被遮挡的边缘、纹理性很强的部分

Speeded Up Robust Features(SURF,加速稳健特征),是一种稳健的局部特征点检测和描述算法
SIFT(Scale-Invariant Feature Transform)特征，即尺度不变特征变换
DOG（Difference of Guassian）：简称  高斯函数的差分，是灰度图像增强和角点检测的一种方法。

检测人：aggregate channel features
INRIA Person Dataset
Viola-Jones人脸检测算法

相机主点(principal point)，即相机畸变中心

pitch是围绕X轴旋转，也叫做俯仰角。
yaw是围绕Y轴旋转，也叫偏航角。
roll是围绕Z轴旋转，也叫翻滚角。

霍夫变换是图像处理中从图像中识别几何形状的基本方法之一。
最基本的霍夫变换是从黑白图像中检测直线(线段)。
方程y0=kx0+b在参数k--b平面上是一条直线，(你也可以是方程b=-x0*k+y0对应的直线)。
这样，图像x--y平面上的一个前景像素点就对应到参数平面上的一条直线。

随机抽样一致算法（Random sample consensus，RANSAC）
RANSAC是改革派：首先假设数据具有某种特性（目的），为了达到目的，适当割舍一些现有的数据。
RANSAC的作用有点类似：将数据一切两段，一部分是自己人，一部分是敌人，自己人留下商量事，敌人赶出去。
RANSAC开的是家庭会议，不像最小二乘总是开全体会议。