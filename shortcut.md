



# notepad++
列编辑模式：先把光标定在开始的位置，然后按`Alt+Shift`。


# texstudio
自定义
Alt+/               注释
Ctrl+/              取消注释

ctrl+shift+M        插入行内公式： (math的意思)
tex文本与pdf文本相互定位：ctrl+鼠标点击，或者F7(显示鼠标位置的pdf文本)

# matlab


|     快捷键      |        说明         |
|:------------:|:-----------------:|
| Ctrl+Shift+0 |    切换到editor窗口    |
|    Ctrl+0    |     Command窗口     |
|    Ctrl+2    |       当前文件夹       |
|    Ctrl+0    |        工作区        |
|    Alt+Shift+E    | 在资源管理器中或Finder中显示 |


ctrl+pageup和ctrl+pagedown之间可以实现在editor中所打开文件之间的切换

Increase Indent		Ctrl+[
Desrease Indent		Ctrl+]

Next window			Ctrl+F6 (从上到下，再从左到右切换窗口）
Find Selection 		Ctrl+F3（选择下一个选中的单词）  Ctrl+Shift+F3（上一个）
Function Hinds		Ctrl+F1（显示函数的参数提示）
Remove Next Word	Ctrl+Delete （删除光标后的一个单词）
Remove Previous Word	Ctrl+Backspace（删除光标前一个单词）

自定义:
Clear Workspace			Alt+Shift+K （清除workspace中所有变量）
Clear Command Window	Alt+Shift+W （清除命令行的输出）
Set Path				Alt+Shift+T （打开设置Path的对话框）
Change to Lower Case	Alt+Shift+L	（将选中文本中的大写字母全部改为小写字母）
Split Editor Left/Right	Alt+Shift+S （将编辑器切分为左右，编辑的是同一个文件）
Beep		Alt+Shift+B	（发出嘟嘟响）
Kill line: Ctrl+K (在command基础上增加在Editor的操作)
Clear all breakpoint: Alt+Shift+C
NextTab				+Ctrl+Tab
Previous Tab		+Ctrl+Shift+Tab
Change Current Folder to Location:	Alt+Shift+F	(改变当前目录到脚本所在的目录)
Comment								Ctrl+/
Uncomment							Ctrl+,



|     bin\win64下的可执行文件      |       说明       |
|:------------:|:--------------:|
| cpuid_info |   处理器的家族、指令集等  |
| gpu_info |      GPU信息     |
| install_supportsoftware | 从“仅下载的安装包”中安装软件 |
| SupportSoftwareInstaller.exe | "安装支持包"的GUI界面  | 


# terminator

快捷键    |       说明
:---:       |       :---:
Ctrl+Shift+E    | 垂直分割重开一个窗口
Ctrl+Shift+E    | 垂直分割重开一个窗口
Ctrl+Shift+O    | 水平分割重开一个窗口
Ctrl+Shift+W    |  关闭当前命令行窗口
Ctrl-Shift-n    | next terminal 
Ctrl-Shift-p    | previous terminal
Ctrl-Shift-i    | New window:
Ctrl-Alt-w    | 重命名最上面的窗口名
Ctrl-Alt-x    | 重命名每个子窗口的名字

eclipse
Alt+Shift+L         全局 抽取局部变量 
Ctrl+Alt+W			自动换行/取消自动换行


# PDF
[acrobat官方](https://helpx.adobe.com/cn/acrobat/using/keyboard-shortcuts.html)

[收集的快捷键](https://www.wenjiangs.com/doc/keyboard-shortcuts-2)

导航快捷键    |       说明
:---:       |       :---:
Shift+F8    |       将焦点移动到快速工具栏
F6          |       将焦点移到导航栏、“文档”窗格、“任务”窗格、消息栏中的下一个项目
Shift+F6    |       将焦点移到导航栏、“文档”窗格、“任务”窗格、消息栏的上一个项目
Shift+F4    |       打开或关闭“任务”窗格
*           |       展开数钱
Shift+*     |       展开所有书签
/           |       折叠选定的书签
F6          |       将焦点移到“文档”窗格（编辑）、“任务”窗格（主页、工具）、消息栏（工具栏）和导航栏（目录）中的下一个项目
Shift+F6    /       将焦点移到“文档”窗格、“任务”窗格、消息栏和导航栏中的上一个项目






H				手型工具
Z				缩放工具(Zoom)
V 				选择工具
R				选择对象工具（啥都不可以选了）
O				编辑对象工具（不可以选了）
A				进入/退出表单编辑
C				裁剪工具（Clip）
L				链接工具（Link）
F				文本域工具（Filed）
M				3D工具（插入3D）
T				编辑文档文本工具
Ctrl+J		JavaScript调试程序
Ctrl+Shift+I 		插入文件
Ctrl+Shift+D		删除页面
选中,~				中划线删除并注释（同Insert）
~				插入注释

注释工具
S				附注工具
Delete		红中线删除
K				图章工具
U				高亮标记选定工具


matlab
Ctrl+Shift+1 	图窗(Figure)，必须在编辑模式（附着在matlab上也可以, docked figure）
Ctrl+Shift+2		Web浏览器
Ctrl+Shift+3 	变量编辑器
Ctrl+Shift+4		比较工具（Home->Compare）

Ctrl+4  				探查器(Run and Time)
Ctrl+6 				图窗选项板(Figure->View->Figure Palette)
Ctrl+7 				绘图浏览器(Figure->View->Plot Browser)
Ctrl+8				属性编辑器(Figure->View->Property Editor)

Ctrl+F2，可标注（解除标注）这一行
按F2即可自动跳到下一个被标注的位置，按Shift+F2是自动跳到上一个被标注的位置

bin/win64
7z				
压缩：7z a -t7z D:\tmp\DriverTest_1.7z "D:\tmp\mexopts\*"
解压：7z x "D:\tmp\DriverTest_1.7z" -y -aos -o"D:\tmp\Mydir"

zip			:
unzip

cpuid_info
processorFamily:6
processorVendor:GenuineIntel
processorModel:142
processorStepping:9
processorInstructionSets: ADX  AES  AVX  AVX2  BMI1  BMI2  CLFSH  CMOV  CMPXCHG16B  CX8  ERMS  F16C  FMA  FSGSBASE  FXSR  INVPCID  LAHF  LZCNT  MMX  MONITOR  MOVBE  MSR  OSXSAVE  OSYMMSAVE  PCLMULQDQ  POPCNT  RDRAND  RDSEED  RDTSCP  SEP  SSE  SSE2  SSE3  SSE41  SSE42  SSSE3  SYSCALL  XSAVE
processorHighestSIMDVersion:AVX2
processorHyperVisor:0
processorPhysicalCores:2
processorLogicalCores:4
processorHyperThreading:1
gpu_info
Intel Corporation %&#Intel(R) HD Graphics 620 %&#22.20.16.4799 %&#2017-9-14 %&#


simulink
Ctrl+T		仿真开始
Ctrl+J		查看Simple Time
Ctrl+D		更新模型（编译模型看有没有错）
Ctrl+E		配置参数

工具箱缩写（使用"doc+工具箱名"打开对应帮助文档）
aero  		航天（+aeroblks)
antenna		天线
audio		语音
autoblks	动力系统
bioinfo		读取、分析、可视化基因和蛋白质数据
coder		根据Matlab代码生成C和C++代码
comm		设计和模拟通信系统的物理层
compiler	从Matlab程序中构建独立的应用（+compiler_sdk）
control		设计和分析控制系统
curvefit	使用回归、插值、平滑来拟合数据的曲线和表面
daq			连接数据获取卡、设备和模块(data acquisition toolbox)
database	和关系型和非关系型数据库交换数据
datafeed	从服务提供者获取金融数据
distcomp	在多核计算机、GPU、计算机集群上执行并行计算（distributed computing）
driving		设计、仿真、测试辅助驾驶和自动驾驶系统
dsp			设计和仿真流信号处理系统（Digital signal processing）
econ		使用统计方法建模并分析金融和经济系统
exlink		从Excel中使用Matlab
finance		金融工具箱
fininst		设计、定价和对冲复杂的金融工具（金融工具工具箱）
fixedpoint	设计、模拟和分析定点系统
fuzzy		设计、模拟模糊逻辑系统
gpucoder	产生NVIDIA GPUSs的CUDA代码
hdlcoder	为FPGA和ASIC设计生成VHDL和Verilog代码
hdlfilter	为定点滤波器生成HDL代码
hdlverifier	使用HDL模拟器和FPGA在环测试平台验证VHDL和Verilog
ident		从测量的输入输出数据中创建线性和非线性动态系统模型
images		进行图像处理、分析和算法开发
imaq		从标准的工业硬件中获取图像和视频（image acquisition）
instrument	控制，与测试和测量工具进行通信
lte			模拟长期演进技术、高级长期演进技术通信系统的物理层（Long Term Evolution）
ltehdl		为FPGAs和ASICs建模长期演进技术通信子系统
map			分析和可视化地理信息
matlab		技术计算语言
mbc			基于模型的校正工具（model-based calibration）
mpc			设计和模拟模型控制器（model predictive control）
nnet		创建、训练、模拟浅度和深度学习神经网络
opc			从开放系统通信服务器和数据记录系统读写数据（Open Platform Communications）
optim		解决线性、二次、整型、非线性优化问题
pde			使用有限元分析解决偏微分方程（partial differential equation）
phased		设计和模拟相控阵信号处理系统（phased array）
plccoder	为PLCs和PACs产生IEC 61131-3（规范可编程逻辑控制器（PLC），DCS，IPC，CNC和SCADA的编程系统的标准）结构化文本和梯形图（PLC，Programmable Logical Controller，可编程逻辑控制器）（PAC, Programmable Automation controller,可编程自动控制器）
predmaint	设计和测试条件监控和预测保持算法（predictive maintenace）
realtime	从FactSet工作站中获得实时数据
rf			设计、建模、分析射频组建的网路（+rfblks）
risk		开发风险模型和执行风险模拟
robotics	设计和测试机器人应用算法
robust		为不确定设备设计鲁棒控制器
rptgen		设计并自动从Matlab应用中生成报表（report generate）
rtw			从Simulink和Stateflow模型中生成C和C++代码（原来的real-time workshop）
signal		执行信号处理和分析
simbio		建模、模拟、分析生物系统
simevents	建模和模拟离散事件系统
simrf			设计和模拟射频系统
simulink	模拟和基于模型的设计
sl3d			在虚拟现实环境中可视化动力学系统行为
slcheck		验证风格标准和建模标准的合规性
slci			自动复审源代码的安全标准（simulink code inspector）
slcontrol	使模型线性化并设计控制系统
slcoverage	在建模和生成代码时衡量测试的覆盖率
sldo			分析模型的敏感性并精调模型参数
sldrt			在电脑上实时运行simulink模型（simulink desktop real-time）
sldv			验证、隔离设计错误并产生测试
slrequirements	创作、管理并跟踪模型需求，产生代码、测试用例
slrt			管理目标电脑的接口
stateflow	使用状态机和流程图建模并模拟决策逻辑
stats			使用统计和机器学习分析和建模数据
symbolic	执行符号数学计算
textanalytics	分析和建模文本数据
trading		获取价格、分析交易成本、向交易系统发送订单
vdynblks	在虚拟3D环境中建模并仿真车辆动力学
vision		设计并建模计算机视觉和视频处理系统
visionhdl	为FPGAs和ASICs设计图像处理、视频和计算机视觉系统
vnt			使用CAN，J1939和XCP协议和车内网络进行通信（vehicle network toolbox）
wavelet		使用小波分析和合成信号和图片
wlan			模拟、分析和测试无线通信系统的物理层



About Bioinformatics(Opens About Bioinformatics toolbox dialogbox)
Add Data From File
Add to favorites
Adjust to Bottom                    Ctrl+Alt+B(Scrolls to bottom without moving cursor position)
Adjust to Top                       Ctrl+Alt+U(Scrolls to top without moving cursor position)
Autofix Message                     Ctrl+Back Quote(~)
Beep                                Alt+Shift+B (在Command Window里): 蜂鸣，作用同beep命令
Change Current Folder to Location   Alt+Shift+F
Change to Lower Case                Alt+Shift+L
Change to Upper Case                Alt+Shift+U
Clear Breakpoints in All Files      Shift+F12
Clear Command History               Alt+Shift+H (清除了prefdir里History.xml的内容)
Clear Command Window                Alt+Shift+W
Clear Text at Prompt                Escape; Ctrl+U
Clear Workspace                     Alt+Shift+K
Close                               Ctrl+W
Collapse                            Ctrl+Shift+, (Current Floder)关闭 目录展开；左键（右键为展开）
Collapse All                        Ctrl+=
Comment                             Ctrl+R;Alt+/
Copy Full Path to Clipboard         Alt+Shift+C (MATLAB Editor)
Cursor Begin Document               Alt+Shift+Left
Cursor End Document                 Alt+Shift+Right

Decrease Indent                     Ctrl+[  (Ctrl+])
Delete Selected Rows/Column         Ctrl+Minus (Ctrl+-, 删除变量编辑器的一行)
Duplicate Selected Element          Alt+Shift+D (在Workspace中创建选中变量的副本）

Example                             Alt+Shift+X (打开示例文档)
Expand All                          Ctrl+Shift+=

Fold All                            Ctrl+=
Function Browser                    Shift+F1 （浏览各种同名函数）

Go To Next Change                   Ctrl+ DownRow

Import Data                         Ctrl+Shift+O (打开导入数据对话框）
Insert Row Above                    Ctrl++ (在选中的位置上面增加一行)
Insert Section                      Alt+Shift+Enter
Insert Section Breaks Around Selection  Alt+Shift+I

Kill Line                           Ctrl+K (删除当前行光标之后的所有字符，当光标位于行末时表示删除换行符）

New App Designer App                Alt+Shift+A (appdesigner)
New Class                           Ctrl+Shift+N
New Function                        Alt+Shift+N
New Script                          Ctrl+N
Next Bookmark                       F2    (添加或删除书签Shift+F2)
Next Section                        Alt+Page Down (+Fn)
Next Window                         Alt+Back Quote(~)

Open Profiler                       Ctrl+Alt+P

Previous Bookmark                   Alt+Shift+F2

Uncomment                           Ctrl+T;Alt+Shift+/


F1, Shift+Tab(选中最后的链接）, Tab(选中打开文档）
Alt+Shift+T: Set path
快捷键说明：https://ww2.mathworks.cn/help/matlab/matlab_env/keyboard-shortcuts.html#bsjqti6-1
Ctrl+Shift+0 编辑器
Ctrl+Shift+3 变量编辑器
Ctrl+Shift+5  帮助浏览器
Ctrl+Shift+F10		右键

Escape; Ctrl+U		Clear Text at Prompt


****************************************************************************************
acrobat

shift+f4    关闭注释列表

ctrl+B		建立目录（书签）


pycharm
F2              Rename
F4              Stop
F5              Run
F6              Resume
F7              Run to Cursor
F8              Debug
F9              Quick Evaluate Expression
F10             Step over
F11             Step into
Shift+F10       Step out
F12             Toggle Line Breakpoint
Alt+Shift+F12   View Breakpoints

Alt+Enter		自动导入包

自义定：
Ctrl+Alt+Shift+S    Scientific Mode


Endnote
Ctrl+Alt+A: Attach file
Ctrl+D: 显示文件属性
F6				在参考列表和参考面板之间切换
Ctrl+M: 	显示所有引用


AutoHotKey
https://www.zhihu.com/question/19645501
学习：https://autohotkey.com/boards/viewtopic.php?f=29&t=4276
http://ahkcn.github.io/docs/Tutorial.htm
例子：https://autohotkey.com/board/forum/49-scripts-and-functions/page-1?prune_day=100&sort_by=Z-A&sort_key=last_post&topicfilter=all


PHPStorm
Database
Ctrl+Shift+F10: Open Console
Shift+F4: Open DDL in console (data manipulation language)

Alt+1 Project
Alt+7 Structure
Alt+F12 Terminal
Ctrl+F7 Next Difference
Shift+F7 Previous Difference
Ctrl+Shift+K: Push
Ctrl+M: Scroll to Center
Ctrl+Shift+J: Join Lines
Ctrl+E:打开最近的文件  
Ctrl+Shift+X: 代码全部变为大写；选中注释中的一段

Ctrl+Shift+Alt+U 查看类的继承关系
Ctrl + Shift + F12 切换最大化编辑器
当前编辑文件定位 : 方法1) 在编辑的所选文件按ALT+F1, 然后选择PROJECT VIEW; 方法2) 左侧 项目列表框 顶部的 定位图标

自定义：
Alt+0: Database



全局自定义
钉钉：激活窗口：Ctrl+Shift+d
微信：激活窗口：Ctrl+Alt+w

有道云笔记
切换界面模块隐藏（快捷键：ctrl+←）显示（快捷键：ctrl+→）  
新建笔记（快捷键：ctrl+n）
激活窗口（热键：ctrl+shfit+y）
同步（快捷键：F5）
插入当前时间（快捷键shift+alt+d）
隐藏窗口的截屏方式（热键：ctrl+shfit+PrintScreen）；

有道词典
Ctrl+Alt+X: 显示/隐藏有道词典
Ctrl+Alt+V: 单词发音
Ctrl+Alt+S: 添加/删除单词


***************************************************
# chrome
置顶：Alt+Space, Always on Top

Alt+E           打开菜单

vimium (http://einverne.github.io/post/2017/12/most-useful-chrome-shortcut.html)
[页面导航]
shift + / (?)	查看所有快键键
j / k			向下/上翻
gg				向上滚动到页面顶端
G				向下滚动到页面底端
d				向下翻动半页
u				向上翻动半页
h / l			向左/右翻
r				重新加载页面
yy				复制当前页面的URL到剪切板
p / P			在当前（新的）页面打开剪切板里里的URL
i				进入插入模式
v				进入可视化模式
gi				聚焦到当前页面的第一个文本输入框
f				在当前页面打开一个链接（显示出来的字母可以为小写）
F				在新的页面打开一个链接
gf				在页面上选择下一帧（？？？）
gF				在主/顶部帧中选择页面（？？？）
[使用vomnibar]
o				打开URL，书签、历史条目
O				在新的页面打开URL、书签、历史条目
b				打开一个书签网页
B				在一个新的页面打开一个书签网页
T				在当前页面搜索（类似在地址栏中用默认搜索引擎搜索）
/				进入查找模式
[查找]
n / N 			到下一个查找匹配（循环向前/后，查找输入后需要回车）
[导航历史]
H / L 			在历史中回退/向前
[操作标签页]
t				新建标签页(tab)
J, gT			到左边标签页
K, gt			到右边标签页
^				到之前访问的标签页
g0				到第一个标签页(Ctrl+0)
g$				到最后一个标签页(ctrl+9)
yt				复制当前标签页
x				关闭当前标签页
X				恢复关闭的标签页


chrome://extensions/shortcuts
管理搜索引擎->设置关键字（百度b，google(g)）->地址栏按b(或者g)再按Tab
下载链接目标	按住 Alt 键的同时点击链接
查看chrome任务管理器  Shift + ESC
利用搜索引擎搜索  Crtl + K、Ctrl + E

Ctrl+Shift+T 打开最近关掉的所有标签页面
Ctrl+Shift+I(J) 开发者工具
F1, esc: 打开、关闭开发者工具设置对话框
Ctrl + ]  切换到下一个面板
Ctrl + [  切换到上一个面板
Ctrl + Shift + M  切换到设备（移动设备）模式，便于响应式调试(Mode)
F5、Ctrl + R  简单刷新
Ctrl + F5、Ctrl + Shift + R  忽略缓存，全部刷新
Ctrl + F在当前文件或面板中搜索
Ctrl + Shift + F  在所有资源中搜索
Ctrl + O、Ctrl + P  搜索文件

Alt+f, s  设置
ctrl + shift + B  显示书签
ctrl + shift + O 管理书签
跳转到指定标签页： Ctrl+1到Ctrl+8
跳转到最后一个标签页：Ctrl+9
在当前标签页中打开主页 Alt + Home
打开“开发者工具”   Ctrl + Shift + j 或 F12
跳转到地址栏  Alt + d (Ctrl + l 或 F6)
显示当前网页的 HTML 源代码（不可修改）  Ctrl + u
在新窗口中打开链接   按住 Shift 键的同时点击链接
利用new tab redirect插件(设置谷歌Chrome浏览器打开新的标签页为指定网页？)


Word
Ctrl+Shift+F5: 查看书签
Ctrl+Shift+A: 将所选字母设为大写
Ctrl+Shift+L : 应用列表样式
Ctrl+Shift+W: 不给空格加下划线
Ctrl+Shift+H: 隐藏文字
Ctrl+Shift+N : 正文
Ctrl+Shift+* : 显示非打印字符（包括隐藏字符、空格）
Ctrl+Shift+Z : 取消人工设置的字符格式
Ctrl+Alt+1(2,3) : 标题1(2,3)
Ctrl+Alt+C : 版权符号
Ctrl+Alt+R : 注册商标符号
Ctrl+Alt+T : 商标符号
Ctrl+Alt+. : 省略号
Ctrl+K : 插入链接
Ctrl+Backspace : 删除左侧的一个字符
Ctrl+F9 : 插入域
Ctrl+Enter : 分页符
Shift+F1 : 查看文字格式
F4 重复上次操作
word2013设置无格式粘贴快捷方式
Alt+F11 -> Normal，右键“插入”–“模块”
Sub 无格式粘贴()
Selection.PasteSpecial Link:=False, DataType:=wdPasteText, Placement:=wdInLine, DisplayAsIcon:=False
End Sub
自定义键盘界面中，找到类别中的“宏”-> Alt+Shift+v
全屏：Alt+V, U ; 退出：Esc


# Win10

Windows Desktop
自定义
Ctrl+Shift+\        关闭显示器


|       快捷键       |     说明    |
|:---------------:|:---------:|
|    Shift+F10    |     右键    |
| Win+Shift+ Left | 应用在双屏之间移动 |
|    resmon		     |   资源监视器   |
|     mstsc		     |    远程桌面   |
|      Win+I      | Windows设置 |
|    Win+Pause    | 打开系统属性对话框 |
|    Win+Pause    | 打开控制面板－轻松使用设置中心 |



小键盘控制鼠标
Win+I -> 轻松使用 -> 左侧“鼠标” -> 打开”使用数字小键盘在屏幕上移动鼠标”
Num Lock 		切换是否使用小键盘控制鼠标
/						左键单击状态
-						进入右键单击状态
*						同时按下左右键状态
上下左右箭头
Home, End, PageUp, PageDown	沿着对角移动鼠标
Ctrl 					加快移动
Shift					减慢移动
/  5					左键单击
/  +					左键双击
-  5					右键单击
-  +					右键双击 
*  5					同时两个鼠标键单击
*  +					同时连个鼠标键双击
拖放：Ins[选中（抓起）对象] -> 移动 -> Del[释放选中对象]


Win+W  便笺
桌面右击->V->D 		显示/隐藏桌面图标

win+空格		切换语言
Ctrl+Shift+H 显示/隐藏 隐藏文件（在资源浏览器）

拖动窗口到屏幕4个角可以触发 1/4 屏幕大小的 Aero Snap
C:\Users\DELL\AppData\Roaming\Microsoft\Windows\Start Menu\Programs\Startup

Win+ = ：放大（放大镜）

appwiz.cpl 卸载程序  (控制面板项（Control Panel Item）)
desk.cpl	显示设置
firewall.cpl	防火墙设置
hdwwiz.cpl		设备管理器（hdwwiz：添加设备向导）
inetcpl.cpl		Internet设置
intl.cpl		区域设置
main.cpl		鼠标属性
mmsys.cpl		声音
ncpa.cpl		网络连接
powercfg.cpl	电源选项
sysdm.cpl		系统属性
timedate.cpl		日期和时间

iexplore		IE浏览器
cleanmgr		磁盘清理		

Win + Ctrl + Shift + B   重启显卡驱动

Alt+1 : 文件属性
Alt+2 : 新建文件夹
d:, 快速进入d盘
完全控制面板%windir%\explorer.exe shell:::{ED7BA470-8E54-465E-825C-99712043E01C}
回收站: %windir%\explorer.exe shell:::{645FF040-5081-101B-9F08-00AA002F954E}


批量重命名：全选，F2
显示记事本记录的时间：在记事本的开头，写上”.LOG”（注意“LOG”必须是大写）


触摸板
三指：上（多任务）、下（显示桌面）

%windir%	打开系统system32目录

Win+G			打开录制工具


Win+B：光标移至通知区域
win+x		: 快捷菜单
Win+Shift+S 自由截图（用完直接在剪切板了）
Win+W 可截取当前屏幕，并方便地调用便签（win+w, Tab, Shift+Tab, 回车)、草图板及编辑截图
win printscreen截屏
win+I, 移动热点（或者直接Win+hot搜索）
win, 录音机

系统命令
SystemPropertiesAdvanced(sp.exe)    系统属性（环境变量）C:\Program Files\Git\usr\bin
osk 屏幕键盘(On Screen Keyboard)

Shift+Win+1~9：窗口“分身”

Win + Ctrl + F：打开查找计算机窗口
Win + A : 操作中心

Win+减号：缩小（放大镜）
Win+加号：放大（放大镜）
Win+Esc：关闭放大镜
Win+，：临时查看桌面
Win+K		:打开连接显示屏
Win + Ctrl + D  添加虚拟桌面
Win + Ctrl + 向右键    在你于右侧创建的虚拟桌面之间进行切换
Win + Ctrl + F4 关闭你正在使用的虚拟桌面
新建虚拟桌面 左下角的图标或win+Tab
直接关闭当前桌面需要按win+F4
切换窗口的快捷键是win+Ctrl+方向键
任务计划程序：taskschd.msc
计算机管理：compmgmt.msc
快速打开设置环境变量对话框：sysdm.cpl，打开系统属性
F3  在文件资源管理器中搜索文件或文件夹
F4  在文件资源管理器中显示地址栏列表
F6  在窗口中或桌面上循环浏览屏幕元素
F10 激活活动应用中的菜单栏
Alt + F8    在登录屏幕上显示密码
Alt + 空格键   为活动窗口打开快捷菜单
Shift + F10 显示选定项的快捷菜单
Win + Alt + D   显示和隐藏桌面上的日期和时间

命令提示符
Ctrl + Home（标记模式）   将光标移动到缓冲区的起始处
Ctrl + End（标记模式）    将光标移动到缓冲区的末尾

计算器
e 2.718
Ctrl + M    存储在内存中
Ctrl + P    添加到内存
Ctrl + R    从内存中重新调用
Ctrl + L    清除内存
F9  选择 ±（正负号取反）
r   选择 1/x（小写的r）reciprocal
@   求平方根
CE=clear error＝清除当前寄存器数值并在显示器上显示0，和C键的区别在于CE键不清除存储

Alt+1 切换到标准模式
Alt+2 切换到科学型模式
Alt+3 切换到程序员模式
Alt+4 切换到统计信息模式
Ctrl+E 打开日期计算
Ctrl+H 将计算历史记录打开或关闭
Ctrl+U 打开单位转换
Alt+C 计算或解决日期计算和工作表
F1 打开“计算器”帮助
Ctrl+Q 按下 M- 按钮
Ctrl+P 按下 M+ 按钮
Ctrl+M 按下 MS 按钮
Ctrl+R 按下 MR 按钮
Ctrl+L 按下 MC 按钮
% 按下 % 按钮
F9 按下 +/– 按钮
/ 按下 / 按钮
* 按下 * 按钮
+ 按下 + 按钮
- 按下 – 按钮
R 按下 1/× 按钮
@ 按下平方根按钮
0-9 按下数字按钮 (0-9)
= 按下 = 按钮
. 按下 。(小数点)按钮
Backspace 按下 Backspace 按钮
Esc 按下 C 按钮
Del 按下 CE 按钮
Ctrl+Shift+D 清除计算历史记录
F2 编辑计算历史记录
向上箭头键 在计算历史记录中向上导航
向下箭头键 在计算历史记录中向下导航
Esc 取消编辑计算历史记录
输入 编辑后重新计算计算历史记录
F3 在科学型模式下选择“角度”
F4 在科学型模式下选择“弧度”
F5 在科学型模式下选择“梯度”
I 在科学型模式下按 Inv 按钮
D 在科学型模式下按 Mod 按钮
Ctrl+S 在科学型模式下按 sinh 按钮
Ctrl+O 在科学型模式下按 cosh 按钮
Ctrl+T 在科学型模式下按 tanh 按钮
( 在科学型模式下按 ( 按钮
) 在科学型模式下按 ) 按钮
N 在科学型模式下按 ln 按钮
; 在科学型模式下按 Int 按钮
S 在科学型模式下按 sin 按钮
O 在科学型模式下按 cos 按钮
T 在科学型模式下按 tan 按钮
M 在科学型模式下按 dms 按钮
P 在科学型模式下按 pi 按钮
V 在科学型模式下按 F-E 按钮
X 在科学型模式下按 Exp 按钮
Q 在科学型模式下按 x^2 按钮
Y 在科学型模式下按 x^y 按钮
'#' 在科学型模式下按 x^3 按钮
L 在科学型模式下按 log 按钮
! 在科学型模式下按 n! 按钮
Ctrl+Y 在科学型模式下按 y√x 按钮
Ctrl+B 在科学型模式下按 3√x 按钮
Ctrl+G 在科学型模式下按 10x 按钮
F5 在程序员模式下选择 Hex
F6 在程序员模式下选择 Dec
F7 在程序员模式下选择 Oct
F8 在程序员模式下选择 Bin
F12 在程序员模式下选择 Qword
F2 在程序员模式下选择 Dword
F3 在程序员模式下选择 Word
F4 在程序员模式下选择 Byte
K 在程序员模式下按 RoR 按钮
J 在程序员模式下按 RoL 按钮
< 在程序员模式下按 Lsh 按钮
> 在程序员模式下按 Rsh 按钮
% 在程序员模式下按 Mod 按钮
( 在程序员模式下按 ( 按钮
) 在程序员模式下按 ) 按钮
| 在程序员模式下按 Or 按钮
^ 在程序员模式下按 Xor 按钮
~ 在程序员模式下按 Not 按钮
& 在程序员模式下按 And 按钮
A-F 在程序员模式下按 A-F 按钮
空格键 在程序员模式下切换位值
A 在统计信息模式下按 Average 按钮
Ctrl+A 在统计信息模式下按 Average Sq 按钮
S 在统计信息模式下按 Sum 按钮
Ctrl+S 在统计信息模式下按 Sum Sq 按钮
T 在统计信息模式下按 S.D. 按钮
Ctrl+T 在统计信息模式下按 Inv S.D. 按钮
D 在统计信息模式下按 CAD 按钮


# Office
截图快捷键    | 说明
:---:       | :---:
Alt+H      | 显示所有菜单的快捷键


# Ubuntu

截图快捷键    | 说明
:---:       | :---:
alt+f2      | 类似于 windows运行（win+r），当前目录在根目录

截图快捷键   | 说明
:---:       | :---:
Print(Print Screen/SysRq)  | 将屏幕截图保存到 Pictures 目录
Alt+Print   | 将窗口截图保存到 Picture 目录
Shift+Print | 将选区截图保存到 Picture 目录

## 自定义快捷键
需要使用gnome-open命令
```shell script
sudo apt install libgnome2-bin
```

快捷键               | 说明
:---:               | :---:
Alt+Shift+D         | 打开下载目录(gnome-open /home/d/Downloads/)
Alt+Shift+W         | 打开工作区间(gnome-open /data3/dong)
Shift+Ctrl+Alt+P    | 打开图片目录（gnome-open /home/d/Pictures)
Ctrl+Alt+Shift+B    | 打开百度(gnome-open http://www.baidu.com)



终端：
Alt+f 	光标向前移动一个单词
Alt+b 	光标向后移动一个单词
ls !$ 	执行命令ls，并以上一条命令的参数为其参数
!! 		执行上一条命令
Ctrl+r 	然后输入若干字符，开始向上搜索包含该字符的命令，继续按Ctrl+r，搜索上一条匹配的命令
Ctrl+s 	与Ctrl+r类似,只是正向检索
Ctrl+a 	移动到当前行的开头
Ctrl+e 	移动到当前行的结尾
Esc+b 	移动到当前单词的开头
Esc+f 	移动到当前单词的结尾
Ctrl+u  删除（剪切）命令行中光标所在处之前的所有字符（不包括自身） （Ctrl+u, Ctrl+k)同样适用于Matlab命令行）
Ctrl+k 	删除（剪切）命令行中光标所在处之后的所有字符（包括自身）
Alt+t 	交换当前与以前单词的位置
Alt+c 	把当前词汇变成首字符大写
Ctrl+s 	挂起当前shell
Ctrl+q 	重新启用挂起的shell

Ctrl + 1/2: 修改文件夹视图为图标或者列表模式
Ctrl + Alt + L: 锁屏，

Alt + F2: 打开运行应用的对话框
Alt + F7: 计划移动窗体选项，你可以使用键盘上的方向键来移动窗口
Alt + F8: 使用键盘上的方向键来更改当前窗口大小
Alt + Up/Down Arrow: 移到父一级目录
Alt + Home: 直接移到你的主目录
Alt + Shift + Tab: 类似 Alt+Tab 进行窗口切换，使用反向顺序
Win+E + 1(数字): 选择左边工作栏中

Ctrl + Alt + F1: 切换到首个虚拟终端
Ctrl + Alt + F7: 切换到当前登录会话



MobaXterm
复制                   Ctrl+Insert
粘贴                   Shift+Insert (设置为 邮件，原来的右键变为: Ctrl+右键)
Ctrl+Shift+F: Find in terminal
    Ctrl+Shift+F3: Find next
Ctrl+Shift+U: Duplicate current tab
修改：Close current: Ctrl+W
隐藏/显示侧边栏：       Ctrl+Shift+B

Toggle fullscreen/Maximize terminal: F11



# VS
Ctrl+-          函数跳转后回退


# Navicate
http://www.cnblogs.com/zx-admin/p/6343346.html
F6  命令列界面
CTRL+H  历史日志
CTRL+Q  新建查询
CTRL+G  设置位置文件夹
CTRL+F  查找字段


Listary Pro v5.0.2581中文破解版(附注册码)
Ctrl+Ctrl

