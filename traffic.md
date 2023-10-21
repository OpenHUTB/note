
# Carla
[构建Carla](https://carla.readthedocs.io/en/0.9.13/build_windows/#unreal-engine) 

```commandline
make launch
```

[导出到carla](https://ww2.mathworks.cn/help/roadrunner/ug/export-to-carla.html) 

将插件复制到carla工程的插件目录：workspace\carla\Unreal\CarlaUE4\Plugins

启动的是CarlaUnreal里的UE4Editor（workspace\CarlaUnreal\Engine\Binaries\Win64\UE4Editor.exe）

使用CARLA Filmbox导出和导入

协同仿真

https://ww2.mathworks.cn/help/roadrunner-scenario/cosimulate-actors-with-carla.html

https://ww2.mathworks.cn/help/roadrunner-scenario/ug/export-scenes-visualizations-to-carla.html


# Unreal
[安装步骤](https://dev.epicgames.com/community/learning/tutorials/k8Ve/unreal-engine-how-to-build-the-unreal-editor-github)

下载[4.26.2源代码](https://github.com/EpicGames/UnrealEngine/archive/refs/tags/4.26.2-release.zip)

[构建](https://docs.unrealengine.com/4.26/en-US/ProductionPipelines/DevelopmentSetup/BuildingUnrealEngine/)

需要将RoadRunner插件放到Unreal源代码的Plugin插件中一起进行编译（以保证插件的Binaries\Win64目录下有文件）。


修改第22行的加载Python接口（.whl）的异常：
C:\BaiduSyncdisk\matlab\software\RoadRunner_2022b\bin\win64\Tools\CARLA\SimulationClient\CarlaBridge.py

关闭代理运行 
C:\BaiduSyncdisk\matlab\software\RoadRunner_2022b\bin\win64\Tools\CARLA\examples\setup.bat

Cannot find an OpenDRIVE file C:/BaiduSyncdisk/workspace/RoadRunner/Scenarios/../Scenes/ScenarioBasic.xodr. 
To correct this error you can import your scene in CARLA or export it to 
the OpenDRIVE file C:/BaiduSyncdisk/workspace/RoadRunner/Scenarios/../Scenes/ScenarioBasic.xodr.
解决办法：将该场景设置为 Unreal Editor 第一个显示的场景，并重新生成。


ERROR:  (id: CARLA Bridge ) : CARLA Bridge: Error connecting to the CARLA server: RuntimeError('failed to generate map')
解释：RoadRunner作为仿真客户端，去连接CARLA服务时候出现CARLA Bridge错误（产生地图失败）。
代码：C:\buffer\carla\PythonAPI\carla\dependencies\include\carla\client\Map.cpp:25
.fbx - 构建地图所需的所有mesh，比如道路、车道标记、人行道等（二进制文件）
.xodr - OpenDRIVE，汽车需要在地图上流通的路网信息。
导入新资产（将ScenarioBasic.xodr复制到 C:\buffer\carla\Unreal\CarlaUE4\Content\RoadRunner\Maps\OpenDrive
Unreal Editor就会提示导入资产，出错：Assertion failed: IsValid() Templates/SharedPointer.h] [Line: 890]
[如何导入新地图](https://carla.readthedocs.io/en/0.9.7/how_to_make_a_new_map/)
解决：不能从资源浏览器中复制进去，必须从Unreal Editor进行点击导入。


## 例子
[香港街道](https://www.unrealengine.com/marketplace/zh-CN/product/hong-kong-street)



## SketchUp
SketchUp 导入 虚幻引擎

中南 中大设计院
https://baike.baidu.com/item/%E9%BB%84%E5%90%88%E6%9D%A5/253223?fr=aladdin
黄合来

开题PPT

# 开源
## 交通仿真和动态智能交通指挥系统
[vissim](http://flypig.cc/2017/06/24/uicom/) 

[基于模型的自动交通仿真框架MOBATSim](https://github.com/MOBATSim/MOBATSim) 

[交通仿真软件](https://www.caliper.com/transmodeler/default.htm) 

[仿真和智慧](http://www.dview.com.cn/rjcp_zz_394.html)


## 交通灯仿真

[交通灯系统](https://github.com/jerrychong25/traffic-light-system) 

[交通灯模糊控制器](https://github.com/ASoleimaniB/Fuzzy-Traffic-Light-Controller) 


# 百度
## 案例
非现场执法

长沙警务云中心（望城）

公交运营公司、交管部门（红绿灯）

株洲天元区
66个路口

## 信控POC

推进到哪一步的，什么类型的城市，岳阳/株洲 到哪一步，有什么问题

学习配时方案，周/节假日，不同

有没有成功实时检测的案例，碰到什么问题
车辆检测数量、再识别是什么车、


信号数据接入。

### 红绿灯
红绿灯是根据车辆导航轨迹来推算的，但是如果这里有动态信控就可能搞不定了，少数地方有接交管的信号系统。
车辆导航时候是会时刻回传他的定位的，进而可以计算速度，方向，行驶或停止状态等~通过这些来计算红绿灯可能状态。
这个其实存在不稳定性和误差。误差是一般都会有几秒误差，不稳定是一旦路口有人工干预的调整或者智能信控系统的动态调整，车辆实际行驶特征和他系统里推算的红绿灯逻辑不一致，他就会暂时下线这个路口红绿灯预测，直到持续一段时间又稳定下来再上线这个路口。

百度车辆位置是真实gps数据，不是推算的


## 数据获取
车道级路网，

红绿灯（csv，什么地方隐掉），交警大楼一起办公，在视频专网中进行连接。

交管 李军龙支队长

视频数据


















# 华为

TOCC 鹏城交通智能体
ICT技术
云底座、端云 摄像机、融合通信，三断情况、沉浸显示（web?）

高速：路段？
（路车感知设备：相机、雷达等，雷视拟合->注入）物联接入；

AI超微光卡口；

云中台（对数字孪生哪些技术、智能驾驶、车辆网）； 

非商业

## 需求

用校园算力中心（鲲鹏）

# 联想

车计算：蔡总、何总、玉总、客户经理、工程师宋

汽车、算力

硬件：车载大屏（智能座舱）、自动驾驶、

车载计算平台：国产芯片

商业模式：合作



--> 生态
车路云边端


地平线（征程；余凯、； 长安）、长沙智驾、
江淮、奇瑞；

交通：岳阳：浏阳市、岳麓区

自动驾驶（虚拟场景、虚拟人） + 大模型（座舱->交通） + 语音交互++


合作点：
产学研（清华）：产业升级、落地
西交大：行业大数据（技术推进、车计算）

西交大课题申报：CCF一等奖
计算所
文档识别

中车（常德）、中联、
清扫车、矿卡、高速


技术合作、应用试点（项目）、

