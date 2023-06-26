






docker system prune -a


根目录过大： https://cloud.tencent.com/info/a7b91c6f5e8f97f9ac03c51ad6fbe288.html
/etc/init.d/docker stop
cp -r /var/lib/docker /data/whd/docker
ln -s /data/whd/docker /var/lib/docker
/etc/init.d/docker start
rm -r /var/lib/docker


环境变量
export PYTHONPATH=/usr/local/caffe2_build:${PYTHONPATH}
export LD_LIBRARY_PATH=/usr/local/caffe2_build/lib:${LD_LIBRARY_PATH}

依赖包不满足
sudo apt-get --fix-broken install
sudo apt-get remove docker-ce   

１．安装docker-ce
1)由于apt官方库里的docker版本可能比较旧，所以先卸载可能存在的旧版本：
$ sudo apt-get remove docker docker-engine docker-ce docker.io

2)更新apt包索引：
$ sudo apt-get update

3)安装以下包以使apt可以通过HTTPS使用存储库（repository）：
$ sudo apt-get install -y apt-transport-https ca-certificates curl software-properties-common

4)添加Docker国内源的GPG密钥：
$ curl -fsSL https://mirrors.ustc.edu.cn/docker-ce/linux/ubuntu/gpg | sudo apt-key add -

5)使用下面的命令来设置stable存储库：
$ sudo add-apt-repository "deb [arch=amd64] https://mirrors.ustc.edu.cn/docker-ce/linux/ubuntu $(lsb_release -cs) stable"

6)更新 apt 软件包缓存，并安装 docker-ce
$ sudo apt-get update
***$ sudo apt-get install docker-ce

7)启动docker CE(设置开机自启动并启动 Docker-ce（安装成功后默认已设置并启动，可忽略）
$ sudo systemctl enable docker
$ sudo systemctl start docker

8)测试安装是否正确
$ sudo docker run hello-world
如果出现以下信息，说明安装成功：
Unable to find image 'hello-world:latest' locally
latest: Pulling from library/hello-world
ca4f61b1923c: Pull complete 
Digest: sha256:445b2fe9afea8b4aa0b2f27fe49dd6ad130dfe7a8fd0832be5de99625dad47cd
Status: Downloaded newer image for hello-world:latest

Hello from Docker!
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
    (amd64)
 3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
 4. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal.

To try something more ambitious, you can run an Ubuntu container with:
 $ docker run -it ubuntu bash

Share images, automate workflows, and more with a free Docker ID:
 https://cloud.docker.com/

For more examples and ideas, visit:
 https://docs.docker.com/engine/userguide/


２．安装nvidia-docker
1)If you have nvidia-docker 1.0 installed: we need to remove it and all existing GPU containers
$ docker volume ls -q -f driver=nvidia-docker | xargs -r -I{} -n1 docker ps -q -a -f volume={} | xargs -r docker rm -f
sudo apt-get purge -y nvidia-docker

2)Add the package repositories
$ curl -s -L https://nvidia.github.io/nvidia-docker/gpgkey | \
  sudo apt-key add -
distribution=$(. /etc/os-release;echo $ID$VERSION_ID)
curl -s -L https://nvidia.github.io/nvidia-docker/$distribution/nvidia-docker.list | \
  sudo tee /etc/apt/sources.list.d/nvidia-docker.list
sudo apt-get update

3)Install nvidia-docker2 and reload the Docker daemon configuration
***$ sudo apt-get install -y nvidia-docker2
$ sudo pkill -SIGHUP dockerd

4)测试nvidia-smi命令  Test nvidia-smi with the latest official CUDA image
$ docker run --runtime=nvidia --rm nvidia/cuda nvidia-smi

３．安装带cuda9的ubuntu16.04的镜像
1)拉取镜像（镜像参考地址：https://hub.docker.com/r/nvidia/cuda/）
$ sudo docker pull nvidia/cuda:9.1-cudnn7-runtime-ubuntu16.04

2)启动镜像，生成容器（将本地磁盘/media/cidi-gpu/data映射到了容器上的/disk位置，并以hqq来命名此容器）
$ sudo nvidia-docker run -it --name base -v /media/cidi-gpu/data:/disk nvidia/cuda:9.0-cudnn7-runtime-ubuntu16.04 bash

3)启动容器
$ sudo docker start base
$ sudo docker attach base

４．docker配置ssh
1)修改root密码
$ passwd

2)安装Openssh
$ apt-get update
$ apt-get install openssh-server

3)修改配置文件
$ apt-get install vim
$ vi /etc/ssh/sshd_config
自己成功：
PermitRootLogin without-password 改为 PermitRootLogin yes
#PasswordAuthentication yes 改为 PasswordAuthentication yes
去掉#注释，将四个选项启用：
RSAAuthentication yes #启用 RSA 认证
PubkeyAuthentication yes #启用公钥私钥配对认证方式
AuthorizedKeysFile .ssh/authorized_keys #公钥文件路径（和上面生成的文件同）
PermitRootLogin yes #root能使用ssh登录

4)重启ssh服务：
$ service ssh restart

5)退出容器并保存更改，关闭宿主机防火墙
$ exit
$ sudo ufw disable

6)使用 docker commit 命令来提交更新后的副本
$ sudo docker commit -m 'install openssh' -a 'Docker Newbee' hqq  cidi:ssh
#其中，-m 来指定提交的说明信息，跟我们使用的版本控制工具一样；-a 可以指定更新的用户信息；之后是用来创建镜像的容器的ID；最后指定目标镜像的仓库名和 tag 信息。创建成功后会返回这个镜像的 ID 信息。
docker commit -m 'detectron:ssh success' 387ba5ba17a1 detectron/ssh

7)将新的镜像启动，并将docker服务器的50001端口映射到容器的22端口上
sudo nvidia-docker run --name cidi-ssh -v /media/cidi-gpu/data:/disk -d -p 50001:22 cidi:ssh /usr/sbin/sshd -D

8)启动容器
$ ssh root@localhost -p 50001

9)查看容器的ip
$ apt-get update
$ apt install net-tools # ifconfig
$ ifconfig　　　　　　#记住当前ip

10)更改docker服务器iptables规则
$ sudo iptables -t nat -L -n  #查看iptables
$ sudo iptables -t nat -D POSTROUTING 2 #删除iptables,2表示172.17.0.0/16在Chain POSTROUTING中所在行数，不包括表头，起始位置为１
$ sudo iptables -t nat -A POSTROUTING -s 172.17.0.0/16 ! -d 172.16.33.0/24 -j MASQUERADE ＃172.16.33.0/24为服务器所在网段．此条iptables规则通过对内外网流量的分离实现区别的NAT对待，就可以既保证Docker容器正常上网，也可以被内网其他主机访问

11)在自己的电脑上，添加路由规则
$ sudo route add -net 172.16.33.0/24 enp3s0 #如果自己的电脑和服务器的ip不在同一网段，则通过自己电脑的网卡enp3s0来添加服务器所在路由网段
$ sudo ip route add 172.17.0.0/16 via 172.16.33.63 #通过服务器ip将容器所在网段添加进路由
$ ping 172.17.0.2  #172.17.0.2为9)中的容器ip，测试是否能ping通
$ ssh root@172.17.0.2  #ssh远程连接服务器的容器，密码为容器root密码


失败****************************************************************************************************
docker inspect 7c2b998a3aa9 | grep Ports
修改docker容器端口映射
1) 停止容器
2) 停止docker服务(systemctl stop docker)
3) 修改这个容器的hostconfig.json文件中的端口
/var/lib/docker/containers/7c2b998a3aa9* #这里是CONTAINER ID
vi hostconfig.json  
如果之前没有端口映射, 应该有这样的一段:
"PortBindings":{}
增加一个映射, 这样写:
"PortBindings":{"22/tcp":[{"HostIp":"","HostPort":"4321"}]}
前一个数字是容器端口, 后一个是宿主机端口. 
而修改现有端口映射更简单, 把端口号改掉就行.

vi config.v2.json  （启动容器时会重置这个文件？？？）
"ExposePorts":{"22/tcp":{}},
"Ports":{"22/tcp":[{"HostIp":"","HostPort":"4321"}]},
4) 启动docker服务
systemctl start docker
5) 启动容器

****************************************************************************************************
保存docker镜像  https://www.cnblogs.com/boshen-hzb/p/6373549.html
脱离容器保持运行，使用ctl+p ，q快捷键
切换为国内镜像：curl -sSL https://get.daocloud.io/daotools/set_mirror.sh | sh -s http://ef017c13.m.daocloud.io
（1）保存到本地
docker save -o /data/whd/docker_image/detectron_init.tar 74a1c8f0d3fb

ssh登录：
（3）mkdir -p /var/run/sshd
vim /etc/pam.d/sshd
找到 session    required     pam_loginuid.so 这一行，将它注释掉
（4）ssh-keygen -t rsa -P ''
将公钥放到/root/.ssh/authorized_key中

docker commit -m 'detectron:ssh success' 387ba5ba17a1 detectron/ssh

启动容器
nvidia-docker run --name detectron_ssh -it -v /data/whd:/data/whd -p 50001:22 detectron/init /bin/bash
进入容器后需要启动ssh服务： service ssh start

ssh -p 50001 root@192.168.100.66

（2）上传到docker注册中心
docker login		(donghaiwang	dong)
docker tag 74a1c8f0d3fb donghaiwang/detectron:init		（第三个为image ID，donghaiwang/detectron为仓库名（donghaiwang为自己的docker hub的用户名），init为tag）
docker push donghaiwang/detectron







****************************************************************************************************
docker run --runtime=nvidia --rm nvidia/cuda:9.0-base nvidia-smi
https://blog.csdn.net/baimafujinji/article/details/89784555

非root用户使用Docker
sudo groupadd docker
sudo gpasswd -a ${USER} docker
sudo systemctl restart docker
当前用户退出系统重新登陆(logout)
docker ps

从宿主机拷贝文件到容器中：docker cp ./demo_2.5.bag apollo_release:/apollo/data/bag/




docker-compose 是用来做docker 的多容器控制
docker-compose 你可以把所有繁复的 docker 操作全都一条命令，自动化的完成。

LXC 只是 Docker 的底层技术之一，而 Docker 已经在此之上发展出了一个生态系统

查看有哪些镜像：
docker images

docker中默认存放镜像和容器的目录是：/var/lib/docker/

win10:
https://blog.csdn.net/shi1451042748/article/details/52996046

查看容器的详细信息：sudo docker ps -a
sudo docker attach e22797f1efb9
sudo nvidia-docker run -it ufoym/deepo bash

sudo docker inspect e22797f1efb9 |  grep IP
从宿主拷贝文件到容器中
sudo docker cp /home/cidi/dong/opencv-2.4.13.6.zip e22797f1efb9:/home/cuda/

docker pull 下来的镜像文件存放的位置
存放在 /var/lib/docker


https://wenku.baidu.com/view/f991456f4431b90d6d85c70f.html?from=search


一个容器一个进程


sudo apt-get install docker.io

docker pull ubuntu:14.04




http://www.linuxidc.com/Linux/2016-12/138490.htm

docker pull ubuntu

docker run -t -i ubuntu /bin/bash

docker run --rm -ti ubuntu /bin/bash
-rm：一旦运行的进程退出就删除容器






https://hub.docker.com/


软链接：
service docker stop
mv /var/lib/docker /data2/whd/software/data/docker
ln -s /data2/whd/software/data/docker /var/lib/docker


sudo docker ps -a

4.
sudo docker build . -t niso2-cxz869
5.
sudo docker run niso2-cxz869

python /bin/cxz869.py  -question 1  -expr \"-0.391425605225\" -n 10 -x \"0.403292890818 -0.540684174163 -0.318409874648 -1.5663508137 -0.450752810364 0.236562487856 0.435959716342 -0.515604901422 0.631719468718 -0.881094831686\"
Exit status: exited with code 127 stderr: /bin/bash: python: command not found





