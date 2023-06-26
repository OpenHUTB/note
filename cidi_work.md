

王海东2018.11.12~2018.11.16
----------------------------------
- **本周工作总结**
1. 调整RefineDet车辆检测模型的前向预测参数，在高速公路场景下测试检测-跟踪算法，效果提升一般（出现漏检和误检）  -close
2. 根据不同车辆在视频中标注不同颜色，在车辆进入和离开相机视野时判断不稳定（本是同一辆车判为不同车辆，待解决） -50% 
3. 尝试用之前测试过的Detectron作为检测-跟踪算法的检测器 -80%
- **下周工作计划**
1. 测试Detectron作为检测器时的跟踪效果，并与RefineDet作为检测器时的效果进行对比（需要标注视频序列）；
2. 找出车辆进入和离开相机视野车辆实例判断不稳定原因并解决；

自动标注工具


王海东2018.11.5~2018.11.10
----------------------------------
- **本周工作总结**
1. 利用检测-跟踪算法在bbk数据上测试多车辆跟踪  -close
2. 在录制的高速公路场景下使用现用的RefineDet车辆检测模型测试检测-跟踪算法 -close 
遇到的问题： 1.现有的RefineDet车辆检测模型误检较多；
2. 长时间跟踪时出现部分实例误判 ，将前后本是同一辆车判断成为多辆车。
- **下周工作计划**
1. 调整并提升车辆检测模型的检测精度；
2. 优化长时间跟踪时出现的实例误判；


bird Lemming  Liquor

王海东2018.10.29~2018.11.2
----------------------------------
- **本周工作总结**
1. 标注部分高速公路场景的跟踪数据，并测试跟ADNet踪模型的效果  -close
2. 利用检测-跟踪算法测试多车辆跟踪（检测模型使用ACF或Faster RCNN，效果一般） -close 
遇到的问题：。
- **下周工作计划**
1. 使用现用的高精度检测模型来完善检测-跟踪算法的检测模型的精度；
2. 标注高速公路场景下的连续帧视频用于跟踪算法模型的训练和测试；

相关滤波、粒子滤波、稀疏表达。

CMU研究生教程上的原题：设计一个直流变压器。https://github.com/sherrysherryli/simulink-python-communication
Matlab调用Python： https://www.zhihu.com/question/31674529
低压是直接输出，高压打到电容进行充电。
MATLAB： Bidirectional DC-DC Converter

CPS问题：可达性（自动检验这个是否可达：出错）、安全性

精度: 0.895857， fps: 15.828065


王海东2018.10.22~2018.10.27
----------------------------------
- **本周工作总结**
1. 阅读ADNet论文，并利用VOT2013,VOT2014,VOT2015的数据进行跟踪模型的训练  -close
2. 调研目标跟踪的基准测试框架tracker_benchmark_v1.0，利用其绘制模型预测结果并打印出检测器性能曲线指标OPE、TRE、SRE -close 
3. 标注部分高速场景的跟踪数据用于测试跟踪模型的性能 -50%
遇到的问题：。
- **下周工作计划**
1. 标注高速公路场景的跟踪数据用于测试跟踪模型的准确率，并绘制OPE、TRE、SRE曲线；
2. 尝试加入高速公路数据用于跟踪训练；


王海东2018.10.15~2018.10.19
----------------------------------
- **本周工作总结**
1. 总结并撰写利用Detectron进行车辆识别的文档  -close
2. 调研目标跟踪的相关方法和应用 -close 
3. 使用开源实现ADNet在OTB100数据集上跑出目标跟踪demo，和车辆跟踪相关效果的视频链接：https://pan.baidu.com/s/1oOh1s8fHqvAaVAFACmgbwg -close
遇到的问题：在对CarScale视频进行测试时，发现跟踪框的尺度适应不好。
- **下周工作计划**
1. 阅读ADNet论文，并利用OTB100的数据进行跟踪模型的训练；
2. 尝试寻找解决跟踪时出现的跟踪框尺度缩放不适应的问题。






公司这边对深度强化学习在车辆变道、超车、停车等应用也安排人调研和尝试，问了规划组的老大，明确表示这个技术尚不成熟，后面也不会安排人力物力做相关的工作，关于自己后面可能的课题方面想找您咨询咨询，不知道您最近什么时候会在基地，我过来找您。


超车变道
输入：模拟器中获得的环境数据（已经识别到的）；输出：变道的规划信息（是否变道） 		感知->规划->控制
模拟器：SUMO -> trackSim（公司自己开发的模拟器）
DQN
tensorflow -> tensorforce 实现的DQN  （最后工程需要转换成C++）

王海东2018.10.8~2018.10.13
----------------------------------
- **本周工作总结**
1. 整理深度学习目标检测模型准确率和召回率的代码和文档，增加附件python和matlab代码和测试数据 -close
2. 整理深度学习手册文档 -close 
3. 调研和撰写自动驾驶场景下深度强化学习实践技术方案 -close
- **下周工作计划**
1. 调研多目标跟踪的车辆跟踪的应用；

李老师 最近您什么时候会在基地


王海东2018.9.24~2018.9.29
----------------------------------
- **本周工作总结**
1. 利用BDD100k中车的标记数据进行车辆识别训练 -close
2. 撰写《深度学习训练技巧_v1》文档 -close
- **下周工作计划**
1. 评价车辆识别训练的精度；
2. 调研提高车辆识别精度的方法。


王海东2018.9.17~2018.9.21
----------------------------------
- **本周工作总结**
1. 完成BDD100k数据到coco数据格式的转换 -close
2. 利用BDD100k中车的标记数据进行车辆识别训练，并评价训练的精度 -60%
3. 调研模型精度判别标准，测试并绘制模型的ROC曲线和PR（精确率-召回率）曲线 -close
- **下周工作计划**
1. 完成BDD100k中训练车辆识别模型的训练和模型精度评价；
2. 调研和实验常用模型训练技巧。


王海东2018.9.10~2018.9.15
----------------------------------
- **本周工作总结**
1. 完成Detectron的Caffe2环境的搭建 -close
2. 跑Detectron目标检测的Demo，选用的是在coco数据集上box AP为41.5的X-101-64x4d-FPN模型 -close
3. 利用coco数据集进行训练，测试给定场景下场景下进行车辆的识别的demo，测试视频链接https://pan.baidu.com/s/1QFCVIXrh2K7fEKtjpOnPoA -close
4. 利用BBK100k的数据进行Detectron框架的训练 -10%
- **下周工作计划**
1. 完成BDD100k数据到coco数据格式的转换并进行车辆识别训练；
2. 尝试将算法部署到apollo平台。


python2 tools/train_net.py \
    --cfg configs/12_2017_baselines/e2e_mask_rcnn_R-50-FPN_2x.yaml \
    OUTPUT_DIR /tmp/detectron-output
    
AssertionError: Im dir '/detectron/detectron/datasets/data/coco/coco_train2014' not found

http://images.cocodataset.org/zips/train2017.zip 
http://images.cocodataset.org/annotations/annotations_trainval2017.zip

http://images.cocodataset.org/zips/val2017.zip 
http://images.cocodataset.org/annotations/stuff_annotations_trainval2017.zip

http://images.cocodataset.org/zips/test2017.zip 
http://images.cocodataset.org/annotations/image_info_test2017.zip 

王海东2018.8.27~2018.9.1
----------------------------------
- **本周工作总结**
1. 调研YOLO使用检测和分类的数据进行联合训练 -close
2. 跑ACF、FasterRCNN车辆检测demo -close
3. 调研精度高的目标检测算法，RefineDet，Mask R-CNN, RetinaNet，并搭建运行Detectron的Caffe2环境 -50%
- **下周工作计划**
1. 跑通Detectron的Mask R-CNN和RetinaNet的例子；
2. 使用BDD100k数据训练车辆识别模型。


http://www.matlabexpo.com/cn/2018/proceedings/proceedings.html#tracka


++ getconf _NPROCESSORS_ONLN
+ MAX_JOBS=12
+ BUILD_TYPE=Release
+ [[ -n '' ]]
+ [[ -n '' ]]
+ echo 'Building in Release mode'
Building in Release mode
+ mkdir -p /home/dong/install/pytorch/torch/lib/tmp_install
+ for arg in '"$@"'
+ [[ nccl == \n\c\c\l ]]
+ pushd /home/dong/install/pytorch/third_party
~/install/pytorch/third_party ~/install/pytorch/build
+ build_nccl
+ mkdir -p build/nccl
+ pushd build/nccl
~/install/pytorch/third_party/build/nccl ~/install/pytorch/third_party ~/install/pytorch/build
+ cmake ../../nccl -DCMAKE_MODULE_PATH=/home/dong/install/pytorch/cmake/Modules_CUDA_fix -DCMAKE_BUILD_TYPE=Release -DCMAKE_INSTALL_PREFIX=/home/dong/install/pytorch/torch/lib/tmp_install '-DCMAKE_C_FLAGS= -I"/home/dong/install/pytorch/torch/lib/tmp_install/include"   -I"/home/dong/install/pytorch/torch/lib/tmp_install/include/TH" -I"/home/dong/install/pytorch/torch/lib/tmp_install/include/THC"   -I"/home/dong/install/pytorch/torch/lib/tmp_install/include/THS" -I"/home/dong/install/pytorch/torch/lib/tmp_install/include/THCS"   -I"/home/dong/install/pytorch/torch/lib/tmp_install/include/THNN" -I"/home/dong/install/pytorch/torch/lib/tmp_install/include/THCUNN" -DOMPI_SKIP_MPICXX=1 ' '-DCMAKE_CXX_FLAGS= -I"/home/dong/install/pytorch/torch/lib/tmp_install/include"   -I"/home/dong/install/pytorch/torch/lib/tmp_install/include/TH" -I"/home/dong/install/pytorch/torch/lib/tmp_install/include/THC"   -I"/home/dong/install/pytorch/torch/lib/tmp_install/include/THS" -I"/home/dong/install/pytorch/torch/lib/tmp_install/include/THCS"   -I"/home/dong/install/pytorch/torch/lib/tmp_install/include/THNN" -I"/home/dong/install/pytorch/torch/lib/tmp_install/include/THCUNN" -DOMPI_SKIP_MPICXX=1  -std=c++11  ' -DCMAKE_SHARED_LINKER_FLAGS= -DCMAKE_UTILS_PATH=/home/dong/install/pytorch/cmake/public/utils.cmake -DNUM_JOBS=12
CMake Error: The source directory "/home/dong/install/pytorch/third_party/nccl" does not exist.
Specify --help for usage, or press the help button on the CMake GUI.
Failed to run 'bash ../tools/build_pytorch_libs.sh --use-cuda --use-nnpack --full-caffe2 nccl caffe2 libshm gloo THD c10d'


蔡超
陈颖
建芳
水强
乃科
海东
赛舟
轶强
肖旺
锡铭
李洋


检测排行榜
http://cocodataset.org/#detection-leaderboard

王海东2018.8.20~2018.8.24
----------------------------------
- **本周工作总结**
1. 标注部分交通灯和地面箭头数据 -close
2. 验证SVM用于特征分类的效果 -close
3. 改造C语言版SVM用于YOLO的分类预测 -50%
碰到的问题：1.地面箭头提取的特征值异常，暂时还没找到原因；
- **下周工作计划**
1. 配合提交交通标志分类模型的精度；


王海东2018.8.13~2018.8.18
----------------------------------
- **本周工作总结**
1. 标注部分交通标志和地面箭头数据 -close
2. 完善交通手势识别全流程的文档 -close
3. 将行人检测、行人警察分类和手势分类用tensorflow实现(python3)串起来 -close
碰到的问题：1.行人检测效率有待提高；
- **下周工作计划**
1. 优化行人检测效率，并考虑手势分类功能的部署；
2. 配合轶强交通标志识别功能的完善。



王海东2018.8.60~2018.8.10
----------------------------------
- **本周工作总结**
1. 标注部分交通标志数据 -90%
2. 分析Apollo平台架构，重点查看视觉感知perception模块源码，实现从相机或者平台获得视频流并显示（手势识别模型预测未加，暂时不弄这个） -close
3. 交通场景人的识别+警察和行人分类+手势识别分类全流程跑通，实现matlab和tensorflow模型的互相转换并验证模型正确 -close
碰到的问题：1.交通场景人的识别仅仅调整预测框的大小来进行手势识别的效果不好，暂时没想到好的方法准确框住人的手；
2.加入警察和行人分类的流程，需要一套警服来拍摄手势识别视频验证全流程的准确率。
- **下周工作计划**
1. 整理交通标志数据成能训练的格式并训练；
2. 录制穿警服做交通手势得视频，并想办法提升交通场景警察识别和全流程的准确率；


王海东2018.7.30~2018.8.4
----------------------------------
- **本周工作总结**
1. 在工作机上搭建Apollo运行环境，并跑官方示例 -close
2. 分析Apollo平台架构，重点查看视觉感知perception模块源码 -close
3. 实现matlab训练的模型和tensorflow模型的互相转换并验证模型正确，证明将模型转化为Apollo所支持的模型的可行性 -close
碰到的问题：Apoll数据集中把不需要识别的交通标注也标注来，需要进行数据清洗；经过缩小送入网络的图片对应大部分标注框过小；
- **下周工作计划**
1. 进行数据清洗；
2. 验证Faster R-CNN在交通标志识别中的训练效果；


王海东2018.7.30~2018.8.4
----------------------------------
- **本周工作总结**
1. 调研检测适合多类别交通标志的目标检测和识别的方法，暂时确定用Faster R-CNN和YOLO来尝试 -close
2. 调研同时存在交通标志、交通灯、箭头的数据集，Apoll的数据集满足基本要求（检测和识别分开） -close
3. 从轶强那拿到抽取后的标注数据，将标注数据处理成Faster R-CNN训练的格式，并开始测试性训练 -close
碰到的问题：Apoll数据集中把不需要识别的交通标注也标注来，需要进行数据清洗；经过缩小送入网络的图片对应大部分标注框过小；
- **下周工作计划**
1. 进行数据清洗；
2. 验证Faster R-CNN在交通标志识别中的训练效果；


王海东2018.7.23~2018.7.27
----------------------------------
- **本周工作总结**
1. 提取ucf101完整数据集的光流信息 -close
2. 搭建个人docker环境用于模型的训练 -close
3. 撰写交通手势识别操作手册，并测试在简单背景和复杂背景下的识别率 -close
4. 调研深度强化学习在自动驾驶中车道线保持、视觉导航、通过交叉路口的应用 -20%
- **下周工作计划**
1. 继续调研深度强化学习在自动驾驶中的应用（待定）；
2. 尝试深度强化学习环境的搭建；


切换后（室内）：
go_straight
class sum: 155, predicted corrected: 146, accuracy: 0.941935
park_right
class sum: 111, predicted corrected: 98, accuracy: 0.882883
stop
class sum: 103, predicted corrected: 103, accuracy: 1.000000
turn_right
class sum: 59, predicted corrected: 0, accuracy: 0.000000
Sum: 428, predicted corrected: 347, accuracy: 0.810748

切换后（室外）：
go_straight
class sum: 164, predicted corrected: 160, accuracy: 0.975610
park_right
class sum: 117, predicted corrected: 110, accuracy: 0.940171
stop
class sum: 70, predicted corrected: 60, accuracy: 0.857143
turn_right
class sum: 55, predicted corrected: 8, accuracy: 0.145455
Sum: 406, predicted corrected: 338, accuracy: 0.832512

杨雪峰（室内）：
go_straight
class sum: 185, predicted corrected: 146, accuracy: 0.789189
park_right
class sum: 113, predicted corrected: 74, accuracy: 0.654867
stop
class sum: 103, predicted corrected: 103, accuracy: 1.000000
turn_right
class sum: 111, predicted corrected: 0, accuracy: 0.000000
Sum: 512, predicted corrected: 323, accuracy: 0.630859

室外：
go_straight
class sum: 164, predicted corrected: 160, accuracy: 0.975610
park_right
class sum: 110, predicted corrected: 30, accuracy: 0.272727
stop
class sum: 74, predicted corrected: 60, accuracy: 0.810811
turn_right
class sum: 117, predicted corrected: 0, accuracy: 0.000000
Sum: 465, predicted corrected: 250, accuracy: 0.537634






王海东2018.7.16~2018.7.21
----------------------------------
- **本周工作总结**
1. 测试加入自己采集数据后训练的手势图片分类模型的准确率（91%） -close
2. 测试训练的时空序列模型在手势序列识别的准确率（63%） -close
2. 解决官网下载ucf101和hmdb51图片序列数据集压缩文件部分文件损坏问题，重下载原始视频数据并切分成训练所需图片 -close
- **下周工作计划**
1. 提取完整数据集的光流信息；
2. 重新训练two-stream模型；

这是交通手势识别的一些总结（在自己录制视频上测试的准确率）：
1.单张图片分类准确率：91%；在图片分类的基础上统计出现最多的手势作为视频预测结果的准确率：93%
2.利用时空特征进行交通手势视频分类的准确率：63%
结论：在网上提供数据集和自己采集数据集测试的效果发现，利用单张图片进行交通手势识别的准确率相比利用时空特征进行视频分类的准确率更高，加上图片序列投票的方式能进一步提高准确率，推荐此方法。


王海东2018.7.9~2018.7.13
----------------------------------
- **本周工作总结**
--- 进展情况：
1. 测试基于时空兴趣点方法在交通姿势视频分类的准确率 -close
2. 阅读基于空间和光流进行人体动作识别的论文，并跑视频分类demo -80%
遇到的问题：1.基于传统时空兴趣点的方法在交通手势识别当中的准确率不高，尝试用深度学习的方法进行交通手势识别。
- **下周工作计划**
--- 工作内容：
1. 提取交通手势动作序列的光流作为训练数据；
2. 训练基于空间和光流人体动作识别的交通手势模型；


王海东2018.7.2~2018.7.7
----------------------------------
- **本周工作总结**
--- 进展情况：
1. 自己拍摄交通手势视频测试对不同拍摄角度的影响 -close
2. 标注392张车道线变道图片 -close
3. 阅读局部时空特征进行视频分类论文，跑出基于时空兴趣点的demo，并测试在KTH数据集上的精度（95%） -close
4. 基于时空兴趣点的方法在交通手势视频数据上进行模型训练 -close
遇到的问题：1.预训练的模型中，基于时空兴趣点的方法对交通姿势视频进行分类的准确率比在KTH数据集上训练的分类器准确率低，具体准确率有待测试。
2. 深度学习人体行为识别方法two-stream的源码编译出现版本不一致问题，有待解决。
- **下周工作计划**
--- 工作内容：
1. 测试基于时空兴趣点方法在交通姿势视频分类的准确率；
2. 阅读two-stream方法论文，并跑视频分类demo；
3. 用交通手势视频数据训练two-stream模型；


全局视频描述子：http://crcv.ucf.edu/projects/gist3d/
作业：http://www.di.ens.fr/~laptev/teaching/trento14/practical3/index.html
复杂手势：https://github.com/hthuwal/sign-language-gesture-recognition



http://www.duanmeiwen.com/pingyu/45494.html
文献综述	B良好	
论文选题	A优秀	
研究成果	A优秀	
论文写作	C中等


总体评价 B良好


熟悉程度（您对论文的熟悉程度）：一般


同意答辩：同意经过小的修改后答辩（可不再送审）


综合评价
对学术论文的学术评语（请根据您对博士学位论文的要求，对本学位论文的选题、创新性研究成果和论文写作等做出评价）
	该课题选题新颖，紧密结合智能汽车的应用场景，设计科学合理，属于本学科的研究热点，研究工作处理好了理论和实际价值的关系，资料丰富，层次分明，条理清楚，结构完整，格式规范。文献材料收集丰富，基本上涵盖了本学科相的主要文献，综合运用了所学知识解决问题，方法设计得当，结果可信，并对本学科的发展趋势有必要的归纳和形成自己的想法。论文撰写严谨认真，结论和研究具有较好的现实作用，取得了一系列有创造性的研究成果:
　　1.针对恶劣天气对摄像头传感器产生干扰的问题，提出了三种改进的实时图像去雾霾算法来提高ADAS对应雾霾天气场景的能力。
　　2.为了保证ADAS在面对传感器故障时有足够的时间进行应急操作，给系统决策提供更多的数据，提出了一种利用RNN对雷达信号和视频信号进行预测的方法。
　　3.为了给ADAS系统提供更多的环境感知信息，对雷达类主动传感器提供信息冗余，提出了一种结合序列学习和目标检测的目标检测方法。
　　4.为了提高ADAS的决策能力，克服传统决策方法依赖规则库和端对端驾驶控制中的开环映射问题，以及ADAS无法理解交通法规的问题，提出了一种基于深度学习的决策控制解决方案。
　　5.通过公开数据集和仿真环境，展示了实验结果和本文方法的性能，并和当前主流算法进行了比较。
　　论文资料丰富、条理清晰、结构完整，个性是在运用深度学习技术智能汽车容错和决策控制方法的研究和设计过程中对设计方案方面有较大突破。本文是一篇合格的博士学位论文，推荐提交答辩。


论文的不足之处及建议：
1.提出一种基于GAN网络和梯度优化的含有文本的深度增强学习算法，思路新颖，后续可以做除“闯红灯”和“超速”以外更多的交通法规作为实验对象。
2.后续有机会将所设计的方法在实际汽车中进行测试，消除仿真环境和真实场景存在的偏差，会更完善和对现实会产生重大的影响。
3.对方法的创新进行理论的归纳和总结会更好。
4.论文中有些可能的文字和排版异常（一下p表示所在论文的页码，括号中为可能的修正，？表示不确定）。

p2
为智能网联汽车全面退（推）广建立基础 
p6
基于此种推论利用线性回归的方法评估参数并回（恢）复图片
p9
为了解决在RCNN方法中尺度变幻（换）改变了原始图像的特征的问题
如果两个物体落在统（同）一目标上会存在漏检问题
SDD(SSD)模型吸取了以前研究的成果和改进网络的经验
p10
SDD(SSD)在预测速度上进行了妥协从而换取了更高的正确率
智能车控制决策算法也在不断的（地）更新
p13
其中，W(l,i)为权重矩阵（最后多了个、）
p14
则双线性能量函数标（表）示为
其中，b，c为偏执（置）向量
p17
输入序列中的每个元素共享单（参）数和操作
p24
需要搜集的数据也夜（）是个难解决的问题
p29
但是位置（未知）变量的数量大于已知变量数目
p31
线性模型的位置（未知）参数大于已知参数
p35
符号()代表卷积操作
p44
从雾霾如偏（如偏？）恢复图像的目的是为了增加图像信息
p46
判别其同样也由卷积真经（神经）网络构成
p47
表2.4 多种图像恢复算法计算速度比较结（果）
（部分字体和段落设置和其他的不一致）
p59
使用SDD(SSD)方法对恢复图像进行目标检测
p77
ATIS数据库是DARPA受记得（收集的）数据库
剩余的1000样本作为特使（测试）样本
p79
gRes-RNN的准确率好于GRU，若雨（弱于）LSTM
p85
将传感器数据看作时间序列洗好（信号）
p88
FCN等两步方法如YoLo和SDD(SSD)等一步方法外
Engelcke等人[的被告人]将视觉模型和AOG模型融合对目标进行检测
p93
Anchor的使用对改进自YOLO的SDD(SSD)做出了巨大的贡献
p99
从目标的类别和位置信息看，达到了主流算法的顺祝您(顺祝您?)
p125
提出一种“数据采集-数据恢复-场景预测-目标识别-增强控制”。具体地，






王海东2018.6.25~2018.6.29
----------------------------------
- **本周工作总结**
--- 进展情况：
1. 录制四个人，每个人四种交通手势动作视频，并处理成模型输入图片 -close
2. 交通手势识别用录的视频测试训练模型的准确率是63%，其中靠右边停和右转的识别率较低 -close
3. 手动标注一批数据（73张），将图片背景换成蓝色，测试模型的正确率，发现识别率低，识别和背景相关不大 -close
4. 调研动作序列识别方法：
	传统经典方法使用局部时空特征+SVM在区分行走、慢跑、行走、打拳、挥手、鼓掌、骑自行车、冲浪八个类别的识别精度达到95%，在交通手势识别里的效果待验证； -close
	深度学习方法识别动作序列经典且效果较好的方法都是基于two-stream：空间流处理静止图像帧，得到形状信息，时间流处理连续多帧稠密光流，得到运动信息，两个流最后经过softmax后，做分类分数的融合。
遇到的问题：利用实际拍摄的图片进行模型精度测试，准确率有所下降，需要添加自己采集的数据到原始训练集当中。
- **下周工作计划**
--- 工作内容：
1. 录制更多的交通手势视频数据；
2. 训练更加准确的交通手势分类模型；
3. 使用局部时空特征进行交通手势动作序列的识别，测试分类效果；
4. 调研two-stream方法并跑demo；




Leaky ReLU
max(0.1x,x)

Caffe
Blob数据存储
分类：Imdb.sh
hdf5：回归 
.prototex网络优化
netscope可视化工具

减少卷积核来减少内存
多分支，实现多尺度表达能力

SPP-NET
空间金字塔池化
ROI (Fast R-CNN)
分类+回归损失（多任务损失）


资源多，；基础原理、结合问题（目标驱动）
选平台：基础改动、研究，调参；封装层次，同时容易
确定平台（3-5年）
工程性、研究点
GAN、Attention; DRL（风险），实验开展；



李洋
小样本（类别数量差异大）
23:1 -> 5:1
合适的比例，对效果提升的效果程度
样本增强方法，GAN，遮挡（风格变化）
改YOLO，交通领域（每种情况都覆盖） 
旋转不能用
90%组合创新；数字媒体
检测，空间约束（惩罚，只会出现在某些位置）
集中点；小题大作


向锡铭
车道线交汇于道路的消失点
平行、白色、
在轮廓、颜色方面的得分
连续点
求消失点
半监督、预先给一个框
消失点选择（选择精英，考虑所有点；无监督聚类，不需要指定类别数目）
阈值选择：图像处理；不用阈值过滤线



DRL
视觉导航综述































王海东2018.6.19~2018.6.23
----------------------------------
- **本周工作总结**
--- 进展情况：
1. 训练交通手势的识别模型并利用官方提供数据的测试集进行测试，准确率为93.89% -close
2. 学习交通手势规则，录制交通手势识别视频并抽取和裁剪出交通手势图片 -close
3. 利用录制得到的交通手势图片测试训练的模型 -close
遇到的问题：自己录制的交通手势准确率较低（判断直行的准确率偏低），原因不明，暂时解决策略：1：修改网络最后层为fc+softmax+classoutput，再重新训练网络；2：将新采集的交通手势数据加入原数据集中进行训练和测试。
- **下周工作计划**
--- 工作内容：
1. 训练调整网络结构后的网络；
2. 考虑引入残差网络或者新机器加快训练速度；
3. 采集更多的交通手势视频加入原数据集；



2018.6.11~2018.6.15
----------------------------------
- **本周工作总结**
--- 进展情况：
1. 熟悉自动驾驶数据库BDD100K，了解其在标注工具、车道线识别、框识别、多边形标注、端到端控制驾驶方面的应用 -close
2. 调研交通手势识别在autoware中的实现，并抽取交通手势识别功能 -close
3. 训练交警和非交警的识别模型 -close
4. 训练交通手势的识别模型 -70%
遇到的问题：训练模型的精度不高、官方提供的数据只支持四种手势识别；
- **下周工作计划**
--- 工作内容：
1. 完成交通手势识别模型的训练；
3. 提高模型的识别精度；


Sum: 489, predicted corrected: 413, accuracy: 0.844581

