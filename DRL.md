


RL四要素：状态、动作、奖励、策略、

PPO（Proximal Policy Optimization）
多臂老虎机（MAB）问题（NAS 任务中，agent 与环境没有交互，可以降阶为无状态的多臂老虎机（MAB，Multi-Armed Bandit）问题）

改变预测（决策）
写入规则；目标是人设定的（现实的目标和人的目标不符合）
数据驱动
会点击的物品、还是放商品的位置 （推荐会对用户造成影响）
预测好（更可能推荐）、预测不好（不会推荐）->影响决策
反馈滞后
根据几十个特征进行打分
线上 A/B测试：性能提升10%
不能用历史的数据，只能用线上交互的数据（探索，试错，代价）
试错代价低
当前画面是否曾经见过
处理不会变的规律（如物理定律）
逆RL、GAN
用历史数据构建模拟器？？
砍价机器人 零和


认知科学领域的研究人员认为人类和动物行为是基于层次结构的
HRL: 使用技能来减少问题的搜索复杂性
停止学习任务，开始学习技能
自动学习层次结构

计算机科学、神经科学、心理学、经济学、数学、工程学
机器学习、奖励系统、经典(SL)/操作(RL)条件反射、有限理性、运筹学、最优控制
“罗塞塔石碑”也被用来暗喻要解决一个谜题或困难事物的关键线索或工具

可以认为RL囊括了人工智能的所有要素：一个智能体被置于一个环境中，并且必须学会在其间游刃有余（Reinforcement Learning might be considered to encompass all of AI: an agent is placed in an environment and must learn to behave successfully therein.） 

开发平台
NAO机器人（类人机器人）

spinningup
sudo apt-get install libglew-dev

哲学领域也强调了行为与反馈对智能形成的意义。生成论（Enactivism）认为行为是认知的基础，行为与感知是互相促进的，智能体通过感知获得行为的反馈，而行为则带给智能体对环境的真实有意义的经验

一个智能体被置于一个环境中，并且必须学会在其间游刃有余（Reinforcement Learning might be considered to encompass all of AI: an agent is placed in an environment and must learn to behave successfully therein.）

强化学习一次选择一个action，feedback不可导，难以训练； 
attention机制在每一个time step都同时选取所有的directions，通过权重将它们merge成为一个solution

tensorflow=1.8.0

Error! TimeLimit' object has no attribute 'ale'
pip install gym==0.7.0

找不到atari
pip install --no-index -f https://github.com/Kojoley/atari-py/releases atari_py


写奖励函数技巧:
https://bons.ai/blog/deep-reinforcement-learning-models-tips-tricks-for-writing-reward-functions

partially observable markov decision process (pomdp)

视觉导航：https://github.com/zfw1226/icra2017-visual-navigation
模拟环境：https://github.com/zfw1226/gym-unrealcv


http://baijiahao.baidu.com/s?id=1603960719399757928&wfr=spider&for=pc
https://github.com/ml-jku/baselines-rudder
依赖：
sudo pip3 install /home/dong/rl/tensorflow-layer-library

wget http://www.mpich.org/static/downloads/3.2.1/mpich-3.2.1.tar.gz
./configure
make && make install
wget https://bitbucket.org/mpi4py/mpi4py/downloads/mpi4py-3.0.0.tar.gz
python setup.py install


sudo docker attach e22797f1efb9



github项目：
开发和评估项目学习算法的框架（兼容OpenAI）
https://github.com/rll/rllab

算法：
https://github.com/haarnoja/softqlearning


仿真软件：
城市交通道路仿真规划(SUMO)：可以帮助用户模拟不同场景下的各种交通情况。它可以帮助建模道路网络、道路标志、交通灯、大量汽车，而且还可以促进在线的交互和车辆控制。


高维range image
连续空间
利用深度强化学习进行视频追踪

行为心理学 + 强化学习
机器心理学 Machine Psychology
强化心理学
行为学习

DRL论文集
https://blog.csdn.net/lqfarmer/article/details/72868471?locationNum=6&fps=1

matlab代码
http://waxworksmath.com/Authors/N_Z/Sutton/sutton.html