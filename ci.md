持续集成

# 流程

本地 --> gitee --(钩子触发)> Jenkins -> 反馈结果（写入到该项目的data/ci目录下、邮箱、企业微信发消息） --> 再次开发

# 安装

## gitlab
[安装教程](https://segmentfault.com/a/1190000019019854) 

启动
```shell
# 通过docker run中加入环境变量,取名为gitlab
sudo docker run --detach \
  --hostname gitlab.example.com \
  --publish 8443:443 --publish 8888:80 --publish 10022:22 \
  --name gitlab \
  --restart always \
  --volume /var/lib/docker/volumes/gitlab-data/etc:/etc/gitlab \
  --volume /var/lib/docker/volumes/gitlab-data/log:/var/log/gitlab \
  --volume /var/lib/docker/volumes/gitlab-data/data:/var/opt/gitlab \
  --shm-size 256m \
  gitlab/gitlab-ce:11.6.4-ce.0
```

查看所有容器
```shell
docker ps -a
```
停止指定容器
```shell
docker stop bdd0255d798e
```
删除指定容器
```shell
docker rm bdd0255d798e
```

### 访问
访问 `http://172.21.121.130/` ，管理员账号 `root`，初始化密码为 `dong.1`。

```shell
git clone http://172.21.121.130/root/dong.git
```

### 问题
* push时，不允许回滚
项目 -> Settings -> Repository -> Protected Branches -> Unprotect



## jenkins Docker 安装
不是最新的docker
sudo apt install docker.io

[参考](https://blog.csdn.net/wkh___/article/details/106883566) 

```shell
sudo docker run -d --restart=unless-stopped --name jenkins_954L -u root \
-v $(which docker):/usr/bin/docker \
-v /var/run/docker.sock:/var/run/docker.sock \
-v /usr/local/dockerinfo/jenkins:/var/jenkins_home \
-v /home/ubuntu/software/matlab_2022a_linux:/var/matlab_2022a_linux \
-p 28080:8080 -p 50000:50000 jenkins/jenkins:lts
```
-v 前面为宿主机的目录 : 后面为容器的目录


增加Matlab的映射目录
```shell
vi /var/lib/docker/containers/f57dbb457b75954648712aedb06bb5a82ed14fb1384ac20f89f27c5829a92d3f/hostconfig.json
```
还需要修改 config.v2.json
```shell
/data2/whd/software/matlab_2018a:/var/matlab_2018a
```
然后重启

进入正在运行的容器
```shell
sudo docker exec -it b80a7fc55ff6 /bin/bash
```



访问：http://172.21.121.130:28080/

### 解锁Jenkins
进入容器：
```shell
docker exec -it jenkins_954L bash
```
将内容复制到网页上
```shell
cat /var/jenkins_home/secrets/initialAdminPassword
0fd6c30574ae4ff4b9d2f41e919bc1e5
```

### 安装推荐插件
* 问题：提示离线

原因：默认访问谷歌
[解决办法](http://172.21.121.130:28080/pluginManager/advanced)
```shell
http://172.21.121.130:28080/pluginManager/advanced
https://mirrors.tuna.tsinghua.edu.cn/jenkins/updates/update-center.json
```

重启容器
```shell
docker restart b80a7fc55ff6
```

nongfugengxia  dong
http://115.157.195.198:28080/



## matlab 配置
[matlab插件配置步骤](http://www.51ufo.cn/%E8%BF%90%E7%BB%B4/2020/06/08/Jenkins%E8%BF%9E%E6%8E%A5gitlab%E6%8F%90%E7%A4%BAreturned-status-code-128%E8%A7%A3%E5%86%B3%E5%8A%9E%E6%B3%95.html)




demo运行


jenkins时间用的不是/etc/localtime
cat /etc/timezone 发现两者不一致
修改容器时区：
echo  'Asia/Shanghai' > /etc/timezone
同步宿主和docker的时间(无效)：
docker cp /etc/localtime f57dbb457b75:/etc/

重启Jenkins
http://115.157.195.198:28080/restart


## 创建项目

### 流程
在创建工程时候，Use alternative credential中 Credential 需要选择已经配置好的GitLab API token。

构建触发器
选择`Build when a change is pushed to GitLab. GitLab webhook URL: http://172.21.121.130:28080/project/dong`


### 问题
#### Jenkins连接gitlab报错：returned status code 128

1. 创建个人访问令牌
```shell
QuTwzRd9GKU_vqTRMwem
```

[解决](https://blog.csdn.net/tt75281920/article/details/105434989) 

注意：gitlab host URL 要选择：http://172.21.121.130，而不是项目地址

#### Private token不生效，报错：Client error: HTTP 401 Unauthorized

[解决](https://blog.csdn.net/merrily01/article/details/87072137) 




# 资源
在[链接](https://github.com/marketplace?query=matlab) 中，搜索想要的actions脚本。


[进行发布](https://github.com/softprops/action-gh-release) 。


