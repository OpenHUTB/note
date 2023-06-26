


# conda
```buildoutcfg
conda create -n sture python=3.6
conda activate sture
conda deactivate
```
```buildoutcfg
conda install --yes --file requirements.txtv
```

# 虚拟环境
导出：
```buildoutcfg
pip freeze >requirements.txt
```
安装：
```buildoutcfg
pip install -r requirements.txt
```

## 环境移植（未测试）
查看自己conda管理有几种python环境：
```commandline
conda info --envs
```

切换到对应的python环境：
```commandline
conda activate brain_model
```

安装conda-pack包
```commandline
pip install conda-pack
```

进行python环境打包（conda-pack）：
```commandline
conda pack -n brain_model -o py366.tar.gz
```


# 部署
使用pycharm专业版的的deployment功能和服务器进行文件同步，将`rsync`的路径添加到 Path 路径下。
```shell
C:\Users\Administrator\Documents\MobaXterm\slash\bin
```

## pip
直接将Python环境复制到新的目录，出现错误
```text
Fatal error in launcher: Unable to create process using '"d:\dong\matlab\python\python.exe"  "D:\matlab\python\Scripts\pip.exe" ': ???????????
```
解决办法：
```shell
python -m pip install --upgrade pip
```

## 脚本转换

```shell
pip install jupyter
jupyter nbconvert --to python *.ipynb
```



# 问题
Q: 安装库的时候出现：
```buildoutcfg
PackagesNotFoundError: The following packages are not available from current channels
``` 
原因是在anaconda默认的网站中没有自己想要的包，更改配置文件，首先找到.condarc文件（一般在用户文件夹下），将其改为
```buildoutcfg
channels:
  - https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/pytorch/win-64/
  - defaults
show_channel_urls: true
channel_alias: https://mirrors.tuna.tsinghua.edu.cn/anaconda
default_channels:
  - https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/main
  - https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free
  - https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/r
  - https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/pro
  - https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/msys2
custom_channels:
  conda-forge: https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
  msys2: https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
  bioconda: https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
  menpo: https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
  pytorch: https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
  simpleitk: https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud
ssl_verify: true
```
如果没有.condarc文件，就创建：
```buildoutcfg
conda config --add channels r
```






# 国内镜像
阿里云 http://mirrors.aliyun.com/pypi/simple
清华大学 https://pypi.tuna.tsinghua.edu.cn/simple
中国科技大学 https://pypi.mirrors.ustc.edu.cn/simple
豆瓣(douban) http://pypi.douban.com/simple


# Pycharm 
## 破解
[破解方法](https://www.cnblogs.com/Dengv5/p/16418279.html) 

## 索引文件位置
当工程特别大时，索引文件特别大。Windows下目录的位置为：
C:\Users\Administrator\.PyCharm2019.3\system\caches

Pycharm - Turn off 'Python version 3.5 does not support variable annotations' error message
重新添加Python解释器。
 I fixed the issue by removing my project interpreter and re-adding it to Pycharm.
Ubuntu did an update which changed my Python 3 version from 3.6 to 3.5, but Pycharm didn't realize it was changed. Updating the interpreter directory from /usr/bin/python3 to /usr/bin/python3.6 fixed things.

ubuntu 18.04搜狗输入发不能用（有效，修改pycharm.sh无效的情况下）：
单击help菜单，找到Edit Custom VM Options...选项
弹出的设置文件底部添加下面一行
-Dauto.disable.input.methods=false


External file changes sync may be slow: The current inotify7 watch limit is too low
1.修改/etc/sysctl.conf, 在最后添加如下内容:
	fs.inotify.max_user_watches = 524288
2.保存后执行以下命令:
	sudo sysctl -p --system
3.重启IDE.

源码编译(https://www.jb51.net/article/152486.htm)：
wget https://www.python.org/ftp/python/3.5.2/Python-3.5.2.tgz
./configure --with-ssl --prefix=/usr/local/python3.5.2
sudo apt-get install build-essential python-dev python-setuptools python-pip python-smbus libncursesw5-dev libgdbm-dev libc6-dev zlib1g-dev libsqlite3-dev tk-dev libssl-dev openssl libffi-dev
make
sudo make install
sudo ln -s /usr/local/python3/bin/python3.7 /usr/bin/python3
sudo ln -s /usr/local/python3/bin/pip3.7 /usr/bin/pip3



Pytroch
conda install numpy ninja pyyaml mkl mkl-include setuptools cmake cffi typing_extensions future six requests dataclasses
YAML文档：YAML Ain't a Markup Language"（YAML不是一种标记语言），以数据做为中心
mkl：Math library for Intel and compatible processors
cffi：用于从Python调用C++代码的CFFI模块
typing_extensions: Backported and Experimental Type Hints for Python 3.5+ (类型注解(type hints))
future: 当一个新的语言特性首次出现在发行版中时候, 如果该新特性与以前旧版本python不兼容, 则该特性将会被默认禁用. 如果想启用这个新特性, 则必须使用 "from __future__import *" 语句进行导入.


查看虚拟环境：conda-env list
conda activate pytorch
使用git clone下来的工程中带有submodule时，初始的时候，submodule的内容并不会自动下载下来的，此时，只需执行如下命令：
git submodule init
git submodule update
这里执行
git submodule sync
git submodule update --init --recursive

export CMAKE_PREFIX_PATH=${CONDA_PREFIX:-"$(dirname $(which conda))/../"}
python setup.py build --cmake-only
ccmake build




pycharm, latex
https://blog.csdn.net/lly1122334/article/details/106423920

pycharm2019.3 的配置文件位于~/.Pycharm2019.3/config/pycharm.vmoption

Pycharm
Expected: %s to exist.



PIL(Python Image Library)

将.pynb转化为.py
jupyter nbconvert --to script *.ipynb

nohup /home/d/anaconda2/envs/deepMOT/bin/python -u /data2/whd/workspace/DMAN_MOT_0_0.2/calculateSimilarity.py > python_output.txt 2>&1 & 
nohup matlab -nodisplay -r DMAN_demo.m > matlab_output.txt 2>&1 & 

python 导入tkinter失败
切换到中科大源就成功了 sudo apt install python3-tk

python键盘、鼠标自动化
pip install pyautogui
教程：https://blog.csdn.net/ibiao/article/details/77859997

目录有空格：
import subprocess
subprocess.Popen("D:\software\Adobe Acrobat X\Acrobat\Acrobat.exe")


pip安装软件
指定–no-cache-dir确保安装不缓存



windows的python扩展包：https://www.lfd.uci.edu/~gohlke/pythonlibs/#numpy

pip install -U scikit-image


conda info -e 环境信息
conda create -n test python=2.7 创建环境test，并指定python版本，此例为2.7
source activate test 激活环境
source deactivate test 关闭环境
conda remove --name test --all 删除环境

conda install 修改源
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/


修改pip为国内源
mkdir ~/.pip 
vim ~/.pip/pip.conf
[global]
index-url = https://pypi.tuna.tsinghua.edu.cn/simple/

win10换成清华源
地址栏%appdata%
新建pip文件夹，文件夹里新建：pip.ini
[global]
timeout = 6000
index-url = https://pypi.tuna.tsinghua.edu.cn/simple
trusted-host = pypi.tuna.tsinghua.edu.cn

conda config --show-sources #查看当前使用源
恢复默认源：
conda config --remove-key channels

conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/main
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/r
conda config --set show_channel_urls yes
conda config --set show_channel_urls yes


TypeError: Population must be a sequence or set.  For dicts, use list(d).
return random.sample(self.buffer, self.num_experiences)
return random.sample(list(self.buffer), self.num_experiences)

打出matplot的配置文件路径
import matplotlib
matplotlib.matplotlib_fname()
'/usr/local/lib/python3.4/dist-packages/matplotlib/mpl-data/matplotlibrc'

解决matplotlib不显示问题
sudo apt-get install python3-tk

AttributeError: 'module' object has no attribute 'urlretrieve'
import urllib.request
data = urllib.request.urlretrieve("http://...")

pip install -r requirements.txt
APScheduler==2.1.2
通过使用== >= <= > <来指定版本，不写则安装最新版


sudo pip3 install matplotlib
sudo pip3 install opencv-python

OpenCV
sudo apt-get install build-essential 
sudo apt-get install cmake git libgtk2.0-dev pkg-config libavcodec-dev libavformat-dev libswscale-dev
下载 ippicv_linux_20151201失败   https://blog.csdn.net/huangkangying/article/details/53406370
wget https://raw.githubusercontent.com/Itseez/opencv_3rdparty/81a676001ca8075ada498583e4166079e5744668/ippicv/ippicv_linux_20151201.tgz
进入opencv目录
ipp_file=../ippicv_linux_20151201.tgz             &&
ipp_hash=$(md5sum $ipp_file | cut -d" " -f1)      &&
ipp_dir=3rdparty/ippicv/downloads/linux-$ipp_hash &&
mkdir -p $ipp_dir &&
cp $ipp_file $ipp_dir

wget https://codeload.github.com/opencv/opencv/zip/3.2.0
unzip 3.2.0 && cd 3.2.0
还需要进入cmake文件夹
cmake -D CMAKE_BUILD_TYPE=Release -D CMAKE_INSTALL_PREFIX=/usr/local PYTHON3_EXECUTABLE=/usr/bin/python3 PYTHON_INCLUDE_DIR=/usr/include/python3.4 PYTHON_LIBRARY=/usr/lib/x86_64-linux-gnu/libpython3.4m.so PYTHON3_NUMPY_INCLUDE_DIRS=/usr/local/lib/python3.4/dist-packages/numpy/core/include ..
make -j1
sudo make install
python3.5
>>> import cv2
>>> cv2.__version__


AttributError: type object 'NewBase' has no attribute 'is_abstract'
sudo pip3 install six --upgrade --target="/usr/lib/python3/dist-packages"

pip install -i https://pypi.tuna.tsinghua.edu.cn/simple gevent
sudo pip3 --default-timeout=100 install -i http://pypi.douban.com/simple --trusted-host pypi.douban.com tensorflow-gpu=1.4.0

导入相对路径下的.py文件
sys.path.append('../tools/')

定时任务：
https://www.liaoxuefeng.com/article/00137760323922531a8582c08814fb09e9930cede45e3cc000
https://segmentfault.com/a/1190000003688320


python3.5默认安装路径：
C:\Users\haidong.wang\AppData\Local\Programs\Python\Python35

######################################################################################################
pycharm激活:
2019.3
从百度网盘中：pycharm/破解补丁中下载文件，
 “Help” -> “Edit Custom VM Options …”，最后一行加上：
 -javaagent:D:\software\PyCharm 2019.3.4\bin\jetbrains-agent.jar
 再次启动，输入激活码：
3AGXEJXFK9-eyJsaWNlbnNlSWQiOiIzQUdYRUpYRks5IiwibGljZW5zZWVOYW1lIjoiaHR0cHM6Ly96aGlsZS5pbyIsImFzc2lnbmVlTmFtZSI6IiIsImFzc2lnbmVlRW1haWwiOiIiLCJsaWNlbnNlUmVzdHJpY3Rpb24iOiIiLCJjaGVja0NvbmN1cnJlbnRVc2UiOmZhbHNlLCJwcm9kdWN0cyI6W3siY29kZSI6IklJIiwiZmFsbGJhY2tEYXRlIjoiMjA4OS0wNy0wNyIsInBhaWRVcFRvIjoiMjA4OS0wNy0wNyJ9LHsiY29kZSI6IkFDIiwiZmFsbGJhY2tEYXRlIjoiMjA4OS0wNy0wNyIsInBhaWRVcFRvIjoiMjA4OS0wNy0wNyJ9LHsiY29kZSI6IkRQTiIsImZhbGxiYWNrRGF0ZSI6IjIwODktMDctMDciLCJwYWlkVXBUbyI6IjIwODktMDctMDcifSx7ImNvZGUiOiJQUyIsImZhbGxiYWNrRGF0ZSI6IjIwODktMDctMDciLCJwYWlkVXBUbyI6IjIwODktMDctMDcifSx7ImNvZGUiOiJHTyIsImZhbGxiYWNrRGF0ZSI6IjIwODktMDctMDciLCJwYWlkVXBUbyI6IjIwODktMDctMDcifSx7ImNvZGUiOiJETSIsImZhbGxiYWNrRGF0ZSI6IjIwODktMDctMDciLCJwYWlkVXBUbyI6IjIwODktMDctMDcifSx7ImNvZGUiOiJDTCIsImZhbGxiYWNrRGF0ZSI6IjIwODktMDctMDciLCJwYWlkVXBUbyI6IjIwODktMDctMDcifSx7ImNvZGUiOiJSUzAiLCJmYWxsYmFja0RhdGUiOiIyMDg5LTA3LTA3IiwicGFpZFVwVG8iOiIyMDg5LTA3LTA3In0seyJjb2RlIjoiUkMiLCJmYWxsYmFja0RhdGUiOiIyMDg5LTA3LTA3IiwicGFpZFVwVG8iOiIyMDg5LTA3LTA3In0seyJjb2RlIjoiUkQiLCJmYWxsYmFja0RhdGUiOiIyMDg5LTA3LTA3IiwicGFpZFVwVG8iOiIyMDg5LTA3LTA3In0seyJjb2RlIjoiUEMiLCJmYWxsYmFja0RhdGUiOiIyMDg5LTA3LTA3IiwicGFpZFVwVG8iOiIyMDg5LTA3LTA3In0seyJjb2RlIjoiUk0iLCJmYWxsYmFja0RhdGUiOiIyMDg5LTA3LTA3IiwicGFpZFVwVG8iOiIyMDg5LTA3LTA3In0seyJjb2RlIjoiV1MiLCJmYWxsYmFja0RhdGUiOiIyMDg5LTA3LTA3IiwicGFpZFVwVG8iOiIyMDg5LTA3LTA3In0seyJjb2RlIjoiREIiLCJmYWxsYmFja0RhdGUiOiIyMDg5LTA3LTA3IiwicGFpZFVwVG8iOiIyMDg5LTA3LTA3In0seyJjb2RlIjoiREMiLCJmYWxsYmFja0RhdGUiOiIyMDg5LTA3LTA3IiwicGFpZFVwVG8iOiIyMDg5LTA3LTA3In0seyJjb2RlIjoiUlNVIiwiZmFsbGJhY2tEYXRlIjoiMjA4OS0wNy0wNyIsInBhaWRVcFRvIjoiMjA4OS0wNy0wNyJ9XSwiaGFzaCI6IjEyNzk2ODc3LzAiLCJncmFjZVBlcmlvZERheXMiOjcsImF1dG9Qcm9sb25nYXRlZCI6ZmFsc2UsImlzQXV0b1Byb2xvbmdhdGVkIjpmYWxzZX0=-WGTHs6XpDhr+uumvbwQPOdlxWnQwgnGaL4eRnlpGKApEEkJyYvNEuPWBSrQkPmVpim/8Sab6HV04Dw3IzkJT0yTc29sPEXBf69+7y6Jv718FaJu4MWfsAk/ZGtNIUOczUQ0iGKKnSSsfQ/3UoMv0q/yJcfvj+me5Zd/gfaisCCMUaGjB/lWIPpEPzblDtVJbRexB1MALrLCEoDv3ujcPAZ7xWb54DiZwjYhQvQ+CvpNNF2jeTku7lbm5v+BoDsdeRq7YBt9ANLUKPr2DahcaZ4gctpHZXhG96IyKx232jYq9jQrFDbQMtVr3E+GsCekMEWSD//dLT+HuZdc1sAIYrw==-MIIElTCCAn2gAwIBAgIBCTANBgkqhkiG9w0BAQsFADAYMRYwFAYDVQQDDA1KZXRQcm9maWxlIENBMB4XDTE4MTEwMTEyMjk0NloXDTIwMTEwMjEyMjk0NlowaDELMAkGA1UEBhMCQ1oxDjAMBgNVBAgMBU51c2xlMQ8wDQYDVQQHDAZQcmFndWUxGTAXBgNVBAoMEEpldEJyYWlucyBzLnIuby4xHTAbBgNVBAMMFHByb2QzeS1mcm9tLTIwMTgxMTAxMIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEA5ndaik1GD0nyTdqkZgURQZGW+RGxCdBITPXIwpjhhaD0SXGa4XSZBEBoiPdY6XV6pOfUJeyfi9dXsY4MmT0D+sKoST3rSw96xaf9FXPvOjn4prMTdj3Ji3CyQrGWeQU2nzYqFrp1QYNLAbaViHRKuJrYHI6GCvqCbJe0LQ8qqUiVMA9wG/PQwScpNmTF9Kp2Iej+Z5OUxF33zzm+vg/nYV31HLF7fJUAplI/1nM+ZG8K+AXWgYKChtknl3sW9PCQa3a3imPL9GVToUNxc0wcuTil8mqveWcSQCHYxsIaUajWLpFzoO2AhK4mfYBSStAqEjoXRTuj17mo8Q6M2SHOcwIDAQABo4GZMIGWMAkGA1UdEwQCMAAwHQYDVR0OBBYEFGEpG9oZGcfLMGNBkY7SgHiMGgTcMEgGA1UdIwRBMD+AFKOetkhnQhI2Qb1t4Lm0oFKLl/GzoRykGjAYMRYwFAYDVQQDDA1KZXRQcm9maWxlIENBggkA0myxg7KDeeEwEwYDVR0lBAwwCgYIKwYBBQUHAwEwCwYDVR0PBAQDAgWgMA0GCSqGSIb3DQEBCwUAA4ICAQBonMu8oa3vmNAa4RQP8gPGlX3SQaA3WCRUAj6Zrlk8AesKV1YSkh5D2l+yUk6njysgzfr1bIR5xF8eup5xXc4/G7NtVYRSMvrd6rfQcHOyK5UFJLm+8utmyMIDrZOzLQuTsT8NxFpbCVCfV5wNRu4rChrCuArYVGaKbmp9ymkw1PU6+HoO5i2wU3ikTmRv8IRjrlSStyNzXpnPTwt7bja19ousk56r40SmlmC04GdDHErr0ei2UbjUua5kw71Qn9g02tL9fERI2sSRjQrvPbn9INwRWl5+k05mlKekbtbu2ev2woJFZK4WEXAd/GaAdeZZdumv8T2idDFL7cAirJwcrbfpawPeXr52oKTPnXfi0l5+g9Gnt/wfiXCrPElX6ycTR6iL3GC2VR4jTz6YatT4Ntz59/THOT7NJQhr6AyLkhhJCdkzE2cob/KouVp4ivV7Q3Fc6HX7eepHAAF/DpxwgOrg9smX6coXLgfp0b1RU2u/tUNID04rpNxTMueTtrT8WSskqvaJd3RH8r7cnRj6Y2hltkja82HlpDURDxDTRvv+krbwMr26SB/40BjpMUrDRCeKuiBahC0DCoU/4+ze1l94wVUhdkCfL0GpJrMSCDEK+XEurU18Hb7WT+ThXbkdl6VpFdHsRvqAnhR2g4b+Qzgidmuky5NUZVfEaZqV/g==

0.0.0.0 account.jetbrains.com

Deployment已经设置了远程服务，Pycharm也已经取消自动保存，确保Ctrl+S可以触发，可是依旧不能自动同步到远程服务器。捣鼓了半天发现在Delployment的mapping标签里有一个小框框
设置为默认服务器

找不到python库和.so
设置Pycharm环境变量
在菜单Run configurations 中，手动设置Environment variables，添加LD_LIBRARY_PATH的内容

Ctrl+0,            Python Console,  reset, y 清空变量
Esc               回到編輯器


External Document
Module Name: torch
URL: https://pytorch.org/docs/stable/{module.basename}.html#{element.qname}

##############################################################################################################
Dockerfile
FROM nvidia/cuda:8.0-cudnn6-devel-ubuntu16.04
MAINTAINER Tyan <tyan.liu.git@gmail.com>


# Install basic dependencies
RUN apt-get update && apt-get install -y --no-install-recommends \
        build-essential \
        cmake \
        git \
        wget \
        libopencv-dev \
        libsnappy-dev \
        python-dev \
        python-pip \
        tzdata \
        vim


# Install anaconda for python 3.6
RUN wget --quiet https://repo.continuum.io/archive/Anaconda3-5.0.1-Linux-x86_64.sh -O ~/anaconda.sh && \
    /bin/bash ~/anaconda.sh -b -p /opt/conda && \
    rm ~/anaconda.sh && \
    echo "export PATH=/opt/conda/bin:$PATH" >> ~/.bashrc


# Set timezone
RUN ln -sf /usr/share/zoneinfo/Asia/Shanghai /etc/localtime


# Set locale
ENV LANG C.UTF-8 LC_ALL=C.UTF-8


# Initialize workspace
RUN mkdir /workspace
WORKDIR /workspace
##############################################################################################################