
# 本子
## 博士后面上项目
音频建模

## 青年基金
MOT 

## 面上项目
背侧流+腹侧流

音频视频融合

# 量子力学
量子网络实现从从图像识别识别开始做

量子理论代码，跟踪和量子力学的关系

量子力学和广义相对论统一于大脑（意识、神经网络）

神经网络中的广义相对论

量子力学、广义相对论建模皮层网络

[量子快充](https://mp.weixin.qq.com/s/Q4uI3t-wZePVrkcv0UnKew)


# 中间层进行训练
```
class MyModel(nn.Module):
    def __init__(self):
        super(MyModel, self).__init__()
        self.fc1 = nn.Linear(10, 64)
        self.fc2 = nn.Linear(64, 10)

    def forward(self, x):
        x1 = F.relu(self.fc1(x))
        x = self.fc2(x1)
        return x, x1


x = torch.randn(10, 10)
y = torch.randn(10, 10)
model = MyModel()
optimizer = optim.SGD(model.parameters(), lr=1e-0)
criterion = nn.MSELoss()

for epoch in range(100):
    optimizer.zero_grad()
    output, aux = model(x)
    loss = criterion(output, y)
    loss = loss + (aux**2).mean()
    loss.backward()
    optimizer.step()
    
    print('Epoch {}, loss {}, aux norm {}'.format(
        epoch, loss.item(), aux.norm()))
```

面部识别vs房子识别python库的例子：
https://nilearn.github.io/stable/auto_examples/07_advanced/plot_haxby_mass_univariate.html#sphx-glr-auto-examples-07-advanced-plot-haxby-mass-univariate-py

腹侧流和背侧流的合并，以处理视频

音乐流派的fMRI，分类音乐流派的深度模型
音乐->fMRI->Decoder(训练数据集训练)->预测模式
fMRI数据：https://openneuro.org/datasets/ds003720/versions/1.0.0
刺激：http://marsyas.info/downloads/datasets.html

CORnet Keras
https://github.com/PreranaKumar/CORnetS_Keras

LSTM:
https://github.com/ruohoruotsi/LSTM-Music-Genre-Classification

fMRI音频处理：
https://github.com/brainhack-school2020/BHS-AuditoryMultimodal

目标解码ImageNet
fMRI: https://openneuro.org/datasets/ds001246/versions/1.2.1


生成fMRI
https://github.com/BlissChapman/ICW-fMRI-GAN

fMRI 补全-->（生成<--） 图像



视觉逆向工程： https://www.youtube.com/watch?v=Vv944hkTH7s


单词的试听：
https://openneuro.org/datasets/ds003717/versions/1.0.0
https://osf.io/qxcu8/



Debug：检查训练网络的输入和输出数据是否正确，将转换前和转化后的数据进行可视化。
参考：
热力图可视化：https://github.com/jacobgil/pytorch-grad-cam
可视化联合训练前/后的特征分布对比：t-SNE

优化程序运行效率：
1. 预取下一次迭代需要的数据；
2. 多CPU数据处理、多GPU并行训练；
3. 减少CPU、GPU之间的数据拷贝；
4. 增大batch_size。

消去实验（对比跟踪效果，预期效果：1<2≈3）：
1. 固定DLA网络参数，只训练SST网络参数；
2. 固定DLA网络参数，先训练SST网络参数，再进行DLA和SST的联合训练；
3. 一开始就进行DLA和SST的联合训练。




FairMOT加上时间序列的信息进行检测再识别

MOT+SOT
数据
神经
数学（优化）

建模成一个序列预测问题（序列之间会有关联）

检测+再识别
关联时加上空间位置的关系，越近表示越可能是同一个

用计算性的方法理解灵长类视觉智能在大脑内的形成机制

多目标跟踪 -> 多视频剪辑（导演）
比如任务是发现危险分子，越危险分越高

MTMC:
在检测和再识别的基础上构建MDP过程，最优化跟踪轨迹。（DRL替换最优化方法）
建模为行人图片（可能加上空间位置信息）分类问题，来一张，答对得+1分，答错-1分（为检测结果分配ID）
在线跟踪（有时间同步信息、监控区域重叠）

AlphaStar：持续时间达一个小时、基于不完全观测信息
天气预测、气候建模、语言理解

rapid miner

分层强化学习： 自动驾驶中，感知、控制、决策的分层

在适应新的环境时，使用多智能体协同，加快适应环境的速度。

LSTM作为task特征的记忆。
增加泛化
只是对每个任务有很好的encoder，类似于利用几步，记忆这个任务的特征。

先用强化学习教会相机跟着人走  再教会计算机把相机采集到的视频剪辑出来
有五个相机对准一个场景  要把五个相机采集的所有视频剪成一个精彩的视频  
用机器取代了director  导演


Hierarchical deep reinforcement learning   +  知识图谱

Salience Detection 显著性检测

Lu Huchuan 卢湖川12-16


神经科学原理：
细胞、突触、
认知（基础）、感知
运动、神经信号（非意识、意识）
生成、
语言、思想、情感、学习
