


https://blog.csdn.net/Nicholas_Wong/article/details/77687949
pip3 install -i https://pypi.tuna.tsinghua.edu.cn/simple tensorflow-gpu


找不到libcublas.so.9.0
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/local/cuda/lib64/

bash Anaconda3-4.2.0-Linux-x86_64.sh

pip install tensorflow==1.5.0


import tensorflow as tf
tf.__version__
查询tensorflow安装路径为:
tf.__path__

一. 安装pip
sudo apt-get install python-pip python-dev
二. 安装tensorflow
pip install tensorflow （python2.7的版本，支持CPU）
pip3 install tensorflow （python3.x的版本，支持CPU）
三、验证tensorflow是否安装成功
　　1.在终端输入命令： python
　　2.进入python命令下，测试tensorflow：
　　　　import tensorflow as tf
　　　　sess = tf.Session()
　　　　hello=tf.constant('Hello,Tensorflow!')
　　　　print(sess.run(hello))
　　3.回车，若在终端下显示 Hello,Tensorflow! 则表示安装tensorflow成功。


tf.sub()更改为tf.subtract()
tf.mul()更改为tf.multiply()
tf.types.float32更改为tf.float32
tf.pact()更改为tf.stact()


exit code 137 (interrupted by signal 9: SIGKILL)
內存不足




***models***
更新pip，再安装jupyter
wget https://pypi.python.org/packages/11/b6/abcb525026a4be042b486df43905d6893fb04f05aac21c32c638e939e447/pip-9.0.1.tar.gz#md5=35f01da33009719497f01a4ba69d63c9
tar -xzvf pip-9.0.1.tar.gz
cd pip-9.0.1
sudo python3 setup.py install (一定要确定是用python3安装，不然更新的是python2的pip版本)
pip -V

https://blog.csdn.net/yaoqi_isee/article/details/75645269
sudo pip install -r requirements.txt
Cython
pillow
lxml
jupyter
matplotlib

object_detection/protos/anchor_generator.proto:11:3: Expected "required", "optional", or "repeated".
object_detection/protos/anchor_generator.proto:11:32: Missing field number.
升级protoc(wget https://github.com/google/protobuf/releases/download/v3.6.0/protobuf-all-3.6.0.tar.gz) 
wget https://github.com/google/protobuf/releases/download/v3.3.0/protoc-3.3.0-linux-x86_64.zip
/home/dong/software/protoc-3.3.0-linux-x86_64/bin/protoc object_detection/protos/*.proto --python_out=.
替换系统中的protobuf:https://www.cnblogs.com/zhonghuasong/p/7903486.html

使用pth文件，在 site-packages 文件中创建 .pth文件，将模块的路径写进去，一行一个路径
export PYTHONPATH=/usr/local/lib/python3.4/dist-packages/tensorflow/models:/usr/local/lib/python3.4/dist-packages/tensorflow/models/slim

python object_detection/builders/model_builder_test.py

jupyter-notebook









