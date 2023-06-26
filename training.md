




tracking
多级的点和框
3D人头
聚类、大图切小图
TLD（Tracking-Learning-Detection）目标追踪算法


学习用户习惯，隐私的考虑，适合端上识别。
老人陪护（多轮对话、面向老人的内容推荐）、危险提醒（身体状况指标、危险报警）
通过相册找东西





Region Proposal stage (Alpha Detect)
CNN后验证stage
pr, fppi


速度比完美更重要
以斗争求和平则和平存，以妥协求和平则和平亡。
产品到技术的鸿沟；拿锤子到处敲。
智能IPC产品：网络摄像头（IP Camera）;电视机小盒子；FPGA
给盘古的算法;beta 盘古做不到的地方


RL
Deep Reinforcement Learning, Decision Maring, and Control
与环境互动
深度学习在RL中的应用：DeepLearning放在增强学习的函数里
PI策略函数，得出action
依赖当前状态、还是也需要依赖于遥远的过去
RL Q-learning vs 控制 悲观 reward function
围棋规则确定，现实世界；不做动作，不知道，没法准确预测
向前预测三步
reward是一个有限的值
policy gradient --> 直接估计Q function
直接通过采样
用model预测将来
快速走子，
转移函数不知道，可以学到，
model-predictive control(MPC)
开车 不断replan
每一个动作（参数）都是可解释的
很少的经验能进行有效的学习：model-base,simulation
走迷宫：墙角，抖动
data 更便宜，训练生成模型（policy function）
end-to-end train
RL作为辅助研究工作，改变做研究的工具；极大增加算例、可解释性。出租车司机（但很有效）
数学工具不好用了，这不是数学；摸黑；这个世界是否是拼拼凑凑出来的
数学工具都有用，但不知道怎么用；
信仰，拼拼凑凑就可以了
从来不数学角度分析 实验心理学
数学工具不够用 自娱自乐 有用
小波 很完美 但到生活中却没有
深度学习理论 不是一两年 但还是要一直做下去
走错一步就对了 很危险 却很有
怎么摸到月亮 造宇宙飞船 摸月亮
不能理解自己的决策 
人脑复杂到人不能理解
生出一个孩子都是可以work的 即使dna出问题了
解决一个特定问题 达不到强人工智能
找到的话 先需要定义空间
看研究历史 过度研究 弯路 需要发文章
gpu和数据
算力乘以100 算法就可以去掉
小孩脑子 有很多model 能举一反三
物理学 天文学 理论和数据相伴相生
曾经被淹没的算法 是否有必要
RL目前还是非常trick
单反变傻瓜相机
数据成倍提升 性能线性提升 人没法标这么多数据
对数据或者分布有假设
假设不一定对 但会加速
人处理很少一部分数据

http://pan.baidu.com/s/1bYYEcu
x689


MXnet
Recent processes on MXNet
longPy支持GPU
CXXNet和Caffe很像，扩展很难
05年开始, iPhone的模型训练
最经一年
前端
交互式Python编程、SQL编程
network根据数据越来越动态，
新的frontend
net, loss
symbolic快
imperative
转换一致，执行模式
server芯片：TPU
低功耗芯片
TVM
一开始收敛，容易陷入局部最优（跳过坑）
硬件厂商：operator
化为用户
云--利用率
定制化芯片;云端，不关心电费
云：抽象、成本
景深摄像头，图片处理也在SOC里
人脸检索 专门芯片 MPU
模型格式之争
AWS模型格式标准 -TVM   ->其他
training 模型更新慢 APP不能超过1M 
云+手机
二值化 需要硬件支持 FPGA；变宽，带宽














MXnet
卷积：展开成矩阵
convolution backward

Operator
mshadow exp 表达式
transform
Tensor张量, 如矩阵就是二维的张量. 如, blob是caffe中的基本数据结构, 简单理解就是一个"4维数组", caffe的blob就相当于一个特殊的tensor. Tensor张量就是多维数组.
Use Tempspace
ResourceSession申请多个Tempspace

DataProvider
ImageRecordlter
Recs-(shuffle,shuffle_chunk_size)->Load -> parse -> Imagerecorder -> batch -> prefetch
多线程


智能语音前端
解决识别率低的问题
Hobot Intelligent Speech Frontend(HISF)
消声实验室，识别率接近100%
10dB电视干扰：88%
让人听懂；让机器听懂（识别）；
设备回声信号（音响）
隐含问题：语音开始和结束

Pre-Proc.   ->  BF/BSS（盲源分离）  -->     AEC   --  Post-Proc.
                                        
DOA                                     VAD             AGC

                                            Speech Recognition（反馈给BF/BSS)
                                            
唤醒的方向为增强的方向 DOA
远场：假设为平面波；否则为球面波
AEC：回声消除
BF： 相加（延迟波束形成）

指向性图Beamform：对某些方向的噪声有抑制，而有些没有
栅瓣（相同）

DAO-Direction of Arrival 
声源定位

VAD判决
识别一段->送给识别器

噪声估计
噪声相对人声比较稳定

AEC 回声消除（音响）
自适应滤波
有参考信号（效果较好）







左右边缘提取：差距
[1 0 -1]
[2 0 -2]
[1 0 -1]

控制模糊级别

保边平滑：结合图像的空间邻近度和像素值相似度的一种折中处理，同时考虑空域信息和灰度相似性，达到保边去噪的目的（双边滤波）。

USM锐化

图像处理
1基色、2偏色、相同：纯色
对比度


C++
1985 -- C++17
C、面向对象的C++、模板
C++11完全兼容C语言
extern "C" 桥梁  -- 按C的方式链接
没有name-mangling、C++有  -- 同样的token编译出不同符号 、函数名编译的结果有唯一的名字
给C进行调用，不要做name-mangling、C++的C语言子集

封装、继承、多态
非虚函数：编译时绑定
虚函数：编译或运行时绑定；指针调用：动态绑定
纯接口：纯虚函数
protected破坏封装性
用继承实现多态
接口的继承、实现继承
多继承：名字冲突（显示指定名字，名字转换）；
菱形继承：从同一个基类继承 -- 虚继承（存的是A的指针）-- 模仿Java 抽象类中纯虚函数

组合在运行时可以修改，除非有明确父子关系，就用类成员变量

动态多态：指向基类的指针或基类的引用调用虚函数。
vptr - vtable
没有super，需要显示指定
直接找符号

模板是C++的静态多态机制
const int* cosnt ptr;  实参顶层const将被忽视

必要的时候才合成默认构造函数

析构：定义拷贝函数、赋值函数
发生异常 栈展开

C++11
decltype不想初始化，与通用引用的推导规则一致
unique_ptr移动语义，用于传递资源, shared_ptr，共享资源
weak_ptr解决shared_ptr的循环引用（它指向的对象引用计数不变）
移动语义，右值引用（不能取地址）：即将被销毁的，安全
函数对象

lamda表示式：捕获列表
->int 尾值

join挂起当前线程，等待结束；detach

《Effective Moder C++》C++11
《C++模板元编程》
《C++ Concurrency in Action》







硬件
信号
差分/差模
共地/共模
总线：I2C(clock、数据线），挂256个器件
SPI
MiPi：手机，差分（高频，传输速率高）、协议层
IIS：高低电平（对应左声道、右声道）
UART
USB：差分、四根线、一对差分线、半双工（只能发或者只能收）
SDIO：SD卡、片选+数据线
网线：Ethernet--802.3，4对双绞线
交换机-交换机：直连网线
CAN总线：仪表盘、刹车（衣服架子）、差分双绞线、抗干扰能力强

控制类芯片
海思--安防、高通、Xilinx、ARM-全志
DSP-数字信号处理（电机控制）、Ceva消费类电子
ASIC-盘古（FPGA固化）

接口类芯片
网卡芯片（PHY,MAC）
88E1111-RCJ
光纤抗干扰能力强

USB host芯片：铁皮外壳 接地 屏蔽罩

存储类芯片
DDRAM
SRAM不需要刷新，数据地址分开；不分开
NVRAM
MMC

射频电路：Wifi/BT

陀螺仪IMU:  MPU-60
加速度计

稳压LDO
DC/DC 直流转换

PCB板子，不打印被腐蚀，印刷电路板；柔性、非柔性

软件如何控制硬件
门电路、二进制、总线寻址、寄存器

模块级设计-> 元器件选取
Protol CPX 
覆铜
差分，干扰能够抵消
差分走线、锐角、线宽、蛇形走线（保持两根线等长，数据同步到达）

电源部分远离高频信号部分
模拟远离射频器件或者功率器件
预留测试点

EMC实验（电磁场实验）
万用表、示波器 -->逻辑分析仪（PC）
雨果，前装，
PCB板 八分板
Hugo原理图





音频IS






Cmake
生成Makefile工程、Xcode工程、MSVC工程
KDE4工程
编译配置文件 -- 所有平台
支持configure file
build目录 build of out of source
复杂的自动化命令 Linux命令
自动生成一个workspance、多个projects
static, share
自动生成文件依赖、并行编译
GUN AutoTools构建流程  config.status

Variables 代表一个值或list:   ${Variables}
工程目录路径的系统变量
CMAKE_CURRENT_BINARY_DIR
CMAKE_CURRENT_SOURCE_DIR
父目录变量可传递到子目录
写到CMakeCache.txt实现变量共享
aux_source_directory(path src) 获取源文件列表
include_directory(pah1 path2 ...)定义头文件包含的路径
link_directories(path1 path2) 定义库文件的包含路径
set(CMAKE_CXX_FLAGS "-Wall -Werror")

Git
rebase避免分叉
绿色，暂存区
sudo apt-get install tig

workflow, stash




Python
读接口
pip install 
easy_install
VS, ipython, Pycharm, 
Jupyter notebook （写文档）



LDAP账号，邮箱账号
登录https://mail.hobot.cc修改邮箱（LDAP）密码
第三方集成的只能输入@前面的内容
PH账号，需要自行注册
北京IDC 20M
网络文件系统  SMB(Windows) CIFS(Common Internet File System) Samba(Unix)
smb://njnas.hobot.cc    \\bjnas.hobot.cc
ssh-copy-id
JIRA: Bug、项目管理
Confluence: 文档管理

Android System
Androi vs Linux Release
Solution
标准化  硬件抽象标准化
A-N  HTC G1  v2.1用户可用
Android O >> The Vendor Interface
测试过了 上面可以随便用
VTS：引入测试集

上手：adb & busybox
boot system userdata

Linux环境下编译
Android.mk
GCC/Makefile    -static
Zygcte -> VM

Android kernel change

匿名共享内存
Binder (RPC) 没有数据拷贝，都在kernel
接近进程间通信
电话，通过binder传递参数(110)

硬件抽象（考虑和汽车）
POSIX（200个函数）

JAR         Java VM
Daivik code Daivk VM

NDK(&JNI)
ls -lt
javah 产生头文件

Android标准工具链（改造过的工具链）






权衡： 标准化 性能
每个厂商会不会改


财务报销
财务、运营、
差旅 <500, <150
晚于8点，补助天数+1
项目编号
增值税专用发票，机器人公司
滴滴行程单
加班打车




