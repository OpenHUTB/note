

# 学习
无模型：不构建状态空间
基于状态（值函数）、基于策略（pi）

基于模型
Over 状态+转换


# 人脸
V1 朝向
V2 朝向的组合
V4 边界信息、曲率形状
IT  模式

# tensorflow
[版本与显卡的对应关系](https://tensorflow.google.cn/install/source)
tensorflow_gpu-1.14.0	2.7、3.3-3.7	GCC 4.8	Bazel 0.24.1	7.4	 10.0


张量是数学理论中比向量，矩阵更为抽象，更为一般的概念。
多维数组是张量概念在编程语言中的具体实现

初始学习率大些，广撒网

提出了LRN（Local Response Normalization）层，对局部神经元的活动创建竞争机制，
使得其中响应比较大的值变得相对更大，并抑制其他反馈较小的神经元，增强了模型的泛化能力。
局部响应归一化原理是仿造生物学上活跃的神经元对相邻神经元的抑制现象（侧抑制），
侧抑制指的是被激活的神经元抑制相邻神经元。
归一化（normalization）的目的是“抑制”。
LRN层模仿生物神经元系统的侧抑制机制，对局部神经元的活动创建竞争机制，使得响应比较大的值相对更大，提高模型泛化能力。

经过巧妙构建，卷积可以用矩阵乘法的方式实现，这也是cuDNN计算卷积的方法之一
CUBLAS 就是 CUDA 专门用来解决线性代数运算的库。
Basic Linear Algebra Subprograms，基础线性代数程序集

L2正则化项让w变小可以防止过拟合：
1. 模型复杂度更低，对数据的拟合更好（奥卡姆剃刀）
2. 过拟合需要顾忌每一个点，最终形成的拟合函数波动很大（导数、系数很大）。

softmax: 柔性最大值传输函数

hard negative就是每次把那些顽固的棘手的错误,再送回去继续练,练到你的成绩不再提升为止.这一个过程就叫做'hard negative mining'.
得到错误的检测patch时，会明确的从这个patch中创建一个负样本，并把这个负样本添加到你的训练集中去

训练过程从低频到高频依次收敛。（低频占优的深度学习）
而奇偶函数是高频占优的。

动量：+ 下坡
AdaGrad：动学习率，不好走的鞋子（走直线）
RMSProp

卷积的意义：加权叠加
平滑山峰

batch-size=512  7.45G显存峰值 11G
batch-size=256	5.3 G		`6G

two stream网络，主要分为两个流，空间流处理静止图像帧，得到形状信息，时间流处理连续多帧稠密光流，得到运动信息。两个流最后经过softmax后，做分类分数的融合，可以采用平均法或者是SVM。不过这两个流都是二维卷积操作。


反射变换(reflection): 改变图像内容的朝向;
对比度变换(contrast): 在图像的HSV颜色空间，改变饱和度S和V亮度分量，保持色调H不变. 对每个像素的S和V分量进行指数运算(指数因子在0.25到4之间), 增加光照变化;
输入图像随机选择一块区域涂黑，参考《Random Erasing Data Augmentation》:随机遮掉图像中部分区域，用空白或噪声代替，从而实现能够对图像的全局信息特征进行学习，增强鲁棒性

孪生神经网络（siamese network）中，其采用的损失函数是contrastive loss(对比损失)，
这种损失函数可以有效的处理孪生神经网络中的paired data的关系。
用在降维中，即本来相似的样本，在经过降维（特征提取）后，在特征空间中，两个样本仍旧相似；
而原本不相似的样本，在经过降维后，在特征空间中，两个样本仍旧不相似。


BP SGD公式推导
推导SVM,LR,决策树，贝叶斯分类，EM和K-means联系
用SMO求解SVM的对偶优化问题
写逻辑回归的极大似然估计的推导
解释caffe每个超参的作用:
	weight decay（权值衰减），最终目的是防止过拟合；
	在损失函数中，weight decay是放在正则项（regularization）前面的一个系数，正则项一般指示模型的复杂度，
	所以weight decay的作用是调节模型复杂度对损失函数的影响，
	若weight decay很大，则复杂的模型损失函数的值也就大。
	按照特征进行normalization（为了防止“梯度弥散”），这样做的好处有三点：（解决在训练过程中，中间层数据分布发生改变Internal Covariate Shift）
		1、提高梯度在网络中的流动。Normalization能够使特征全部缩放到[0,1]，
		这样在反向传播时候的梯度都是在1左右，避免了梯度消失现象。
		2、提升学习速率。归一化后的数据能够快速的达到收敛。
		3、减少模型训练对初始化的依赖。
		在网络的每一层输入的时候，又插入了一个归一化层，也就是先做一个归一化处理，然后再进入网络的下一层。
		这一层网络所学习到的特征分布被你搞坏了-> 变换重构，引入了可学习参数γ、β
Dropout为什么可以解决过拟合：不同的网络可能产生不同的过拟合，取平均则可能让一些“相反的”拟合互相抵消；减少神经元之间复杂的共适关系（生物适应特定的环境，而环境改变时不适应）；
正则化来防止过拟合：给模型参数w添加一个协方差为1/alpha的零均值高斯分布先验。加入正则化是在bias和variance之间做一个tradeoff。
Batch-normalization的思想
迁移学习和fine-tune:
	用别人已经训练好的Imagenet模型，把Alexnet里卷积层最后一层输出的特征拿出来，然后直接用SVM分类。这是Transfer Learning，因为用到了Alexnet中已经学到了的“知识”。
	也可以直接使用fine-tune这种方法，在Alexnet的基础上，重新加上全连接层，再去训练网络。
	Transfer Learning关心的问题是：什么是“知识”以及如何更好地运用之前得到的“知识”。这可以有很多方法，而fine-tune只是其中的一种手段。
在分类中如何处理训练集中不平衡问题（训练集中某些类别的样本数远大于另一些类别）：
	增加小样本数据（对大类数据进行欠采样）；
	尝试其他评价指标：混淆矩阵（TP，FN，FP和TN）；
	对小类的数据进行过采样（添加部分样本的副本），对大类的数据样本进行欠采样；
	尝试产生人工数据样本：对每个属性特征的取值空间中随机选取一个组成新的样本；SMOTE；
	尝试不同的分类算法：决策树在不均衡数据上表现不错
	尝试对模型进行惩罚：对分类器的小样本数据增加权值，降低大样本的权值；
目标检测中anchor box的做法 和 adaboost人脸检测中的滑窗检测 的区别
	anchor候选窗口
SSD：Single Shot MultiBox Detector, Faster R-CNN的anchor box和YOLO单个神经网络检测思路(end-to-end)
	region proposal（目标位置和大小）-> CNN（类别的判定）
	Haar特征/矩形特征：Sum(白)-Sum(黑)
Locacl Conv：人脸在不同的区域存在不同特征；普通conv的参数在整个feature map上是共享的，而local conv是在一个map上的局部区域内参数是共享的不同区域内的参数是不同的（过了局部区域参数就不共享了，就要换一组参数（参数量大大增加））
跟踪和检测的区别：检测用到单帧；跟踪是在已有目标的位置，在后续帧中匹配
网络够深(Neurons足够多)，总能避开较差Local Optima (参考 The Loss Surfaces of Multilayer Networks)
Cross-Entropy / MSE(均方误差) / K-L散度（相对熵 relative entropy 用来衡量两分布质检的不相似性）
KL(p||q) = - f p(x) ln q(x) dx  - ( -f p(x) ln p(x) dx )
		 = -f p(x) log(q(x)/p(x)) dx
熵：H(p) = -sum( p(x)log p(x) )
p(x)是数据的真实概率分布，q(x)是由数据计算得到的概率分布；希望q(x)尽可能地逼近甚至等于p(x)，从而使得相对熵接近最小值0；

权值初始化：（5、6很适合ReLU）
1.constant初始化
2.uniform
3.Gaussian
4.positive_unitball初始化：权值和为1
5.XavierFiler初始化：权值的分布（均值为0，方差为 1/输入的个数），即均匀分布
6.MSRAFiler初始化：权值分布就均值为0，方差为 1/输出的个数 的高斯分布
7.BilinearFiler初始化：常用在反卷积神经网络里的权值初始化

激活函数用来加入非线性因素。
造成梯度消失的一个原因是，许多激活函数将输出挤压在一个很小的区间内，在
激活函数两端较大范围的定义域内梯度为0，造成学习停止。

CNN能处理NLP、Speech因为都存在局部与整体的关系，由低层次的特征经过组合，组成高层次的特征，
并且得到不同特征之间的空间相关性。（局部连接、权值共享、池化操作、多层次结构）

机器中原始数据中提取模式的能力。

无监督学习：按照一定偏好（特征空间距离最近）
强化学习：试错；如果胜利，就学习记忆。
半监督学习：部分数据有标签（数据标注非常困难）
弱监督学习：数据+对应的弱标签（分类）-> 分割
多示例学习：数据包（1000张图是否有猪的出现）

softmax函数用于多分类，将输出映射到（0,1）区间内（概率（最大））；e^i/sum(e^j)
交叉熵损失函数：-sum(yi * lnai)
softmax函数的本质就是将一个K维的任意实数向量压缩（映射）成另一个K维的实数向量，其中向量中的每个元素取值都介于（0，1）之间

sigmod
f(x) = 1/(1+e^(-x))


tanh(x) = (1-e(-2x)) / (1+e(-2x))

ReLU
y = 0 (x<=0)
	x (x>0)
更快收敛；操作简单；缓解梯度消失的问题；提供了神经网络的稀疏表达能力。


标注图Label Map
数据增强 来增加输入数据的量
以1/2的概率进行随机的ROI采样（如下图蓝色矩形框所示），而其余1/2的概率则以某个positive instance为对象产生ROI（如下图绿色矩形框所示），确保该目标物体能够以合适的大小出现在其中

假设我们手上有60个正样本，40个负样本，我们要找出所有的正样本，系统查找出50个，其中只有40个是真正的正样本，计算上述各指标。
TP: 将正类预测为正类数  40
FP: 将负类预测为正类数  10
TN: 将负类预测为负类数  30
FN: 将正类预测为负类数  20
准确率(accuracy) = 预测对的/所有 = (TP+TN)/(TP+FN+FP+TN) = 70%
精确率(precision) = TP/(TP+FP) = 80%       （分母：预测为正的样本数）精确率是针对我们预测结果而言的，它表示的是预测为正的样本中有多少是真正的正样本
召回率(recall) = TP/(TP+FN) = 2/3          （分母：所有的正样本数）召回率是针对我们原来的样本而言的，它表示的是样本中的正例有多少被预测正确了



深度学习：可微分、强监督、封闭静态系统。

风格迁移:https://github.com/awentzonline/image-analogies
pip install virtualenv
pip install neural-image-analogies
python F:\ProgramFiles\Anaconda3\Scripts\make_image_analogy.py images/sugarskull-A.jpg images/sugarskull-Ap.jpg images/sugarskull-B.jpg out/arch

python F:\ProgramFiles\Anaconda3\Scripts\make_image_analogy.py images/arch-A.jpg images/arch-Ap.jpg images/arch-B.jpg out/arch

Check the version of keras installed using:: pip show keras
If it is Keras version 2 then pip uninstall keras followed by:: pip install keras==1.1.1


DL Book
Toeplitz矩阵：拓普利兹矩阵

使核相对输入进行翻转

稀疏连接、参数共享、平移不变性（平移等变）

稀疏连接会因为深层的节点而关联到整副图像

超参数：机器学习模型里的框架参数

通过正则化（防止过拟合），保持参数值较小；减少参数的候选空间，使得模型更加“简洁”。

正则化项即罚函数，该项对模型向量进行“惩罚”，从而避免单纯最小二乘问题的过拟合问题。

L2正则化就是在代价函数后面再加上一个正则化项；添加先验
经验风险最小化 + 正则化项 = 结构风险最小化
代价函数+正则化项的惩罚
对函数的偏好（去掉空间中的某个函数可以看做是对不赞成这个函数的无限偏好）


第十章 序列建模：循环和递归网络
CNN：处理网格化数据（如一个图像）；
RNN：处理序列x1, ..., xt；
在模型的不同部分共享参数（否则只能处理固定长度的句子）。
如果在每个时间点都有一个单独的参数，不但不能泛化到训练时没有见过的序列长度，也不能再时间上共享不同序列长度和不同位置的统计强度。


mxnet 中 cannot find -lcblas问题
进入 mxnet 文件夹，将config.mk中的USE_BLAS = atlas 改成USE_BLAS = blas





mxnet

git clone --recursive https://github.com/dmlc/mxnet
cd mxnet;
cp make/config.mk .
make -j4

python example/image-classification/train_mnist.py


http://lucianlv.blog.51cto.com/9871307/1812733



http://m.blog.csdn.net/article/details?id=50260419



sudo apt-get install -y build-essential git libblas-dev libopencv-dev

git clone --recursive https://github.com/dmlc/mxnet





Tensorflow
安装
http://blog.csdn.net/law_130625/article/details/60611810

https://repo.continuum.io/archive/index.html
Anaconda3-4.3.0-Windows-x86_64

CPU版本安装：pip install tensorflow-1.3.0rc2-cp36-cp36m-win_amd64.whl
pip install tensorflow-gpu

nvcc -V，即可看到相应的信息，同时把cuDNN解压后把里面的三个文件夹剪切到安装CUDA文件夹的v7.5下

>>> import tensorflow as tf
>>> hello = tf.constant('Hello, TensorFlow!')
>>> sess = tf.Session()
>>> print(sess.run(hello))



笔记：

入门简介
正则化、优化
感知器不能处理异或，线分开，中间增加神经元，组合优化问题
80年代，BP神经网络；局部极小点
学习数据的多层表示
SVM领域专家来设计 vs 学习特征
logistic，阶跃->光滑
内积的值越大，越容易激活
图片->vector 向量的夹角
第一层，输入图像在同一空间，相似则激活
具体到抽象，告诉目标输出是什么
x求导，传梯度；求导数，沿着什么方向改变；改变w得到想要的
沿着什么方向，使损失函数变小
两层（一层，在同一空间，SVM，没有特征的组合）
用BP找到它的梯度方向，（优化：loss不降，局部极小点）
掉到坑里，平的高原

算法工程师
同样数据，结果不好；调整优化策略，正则化方法
在训练集上表现足够好，->验证集上（不）好(过拟合）
训练集上有噪声，模式、噪声都记住：背景是雪的都是阿拉斯加犬
数据可视化，找数据中的问题；把噪声数据也激活
数据覆盖更全

损失函数变小，调神经网络参数，参数空间,(w1,w2)，固定某一个权值
损失函数梯度，圈上有相同loss，最陡峭的方向来改变w1,w2
来回折着走，峡谷
所有数据放在一起（随机找一部分，随机梯度下降），batch learning，算平均梯度一样
噪声，逃脱局部极小值点

参数初始化，数据、参数初始化（batch normalization:训练过程保证0均值，对参数取均值)一般小一点的batch
0均值的神经元
朝那个方向，走多远（学习率），最优学习率，大于一倍，来回震荡；大于两倍，跳出去了
loss变大，学习率过大；参数初始化小一点
两个极小值，参数初始化就很重要了

(步长->）动量，重球在峡谷中越滚越快
历史情况做平均0.9（用老汤）
可视化：why monment really works?   http://distill.pub/2017/momentum/
最优学习率，二阶导数，曲率，Hessian矩阵，近似它（考虑历史的梯度）
没见过的词，学习率就要高一点
Resillient propagation
梯度方向符号一直变化、不变

Adam用来训练网路，可视化
危险：鞍点

神经元ReLU



Preventing overfitting
简单，邻近的两个点光滑（局部光滑假设）
更多有代表性的数据，数据复制一万份（x）
模型不要太复杂
平均多个模型

loss->0 没法降到0：优化方法不对；某一层梯度变为0；同样图一个标0，一个标为1
深度、神经元数，胖；时间越长，模型越大，参数数值范围
随机加一些扰动

L2 and L1 penality
L2:越大压得越大
L1:越大变化一定

Weight constraints

Dropout：0.5的概率关闭神经元，岗位变，防止作弊，一直在换；随机选择基因，防止被放大；

怎么数据前向、误差怎么传播





DenseBox
FCN 最后的全连接 变成卷积层

upsumpling
对最后一层进行上采样，映射回原图（在尺度上拉回和原图一致）

使用crop_layer来配合deconvolution层

以pooling分层，只有pooling把图进行缩小


Multi-Task Training

BoundingBox
迭代次数超过100Loss不降低了，就可以停止，不用到最大迭代次数（经验值）

在KITTI上实验，车型（车有意义的特征点）







用Map Reduce实现矩阵乘法
NLP相关的encoding问题 (CBOW vs Skipgram)
Gradient Boosting
Random Forest
SVM的Gaussian Kernel的dimension
用Regex分析文本
永和用python/R读取JSON，并且系数据
用C++实现Mote Carlo
coding: 用DFS走迷宫

























