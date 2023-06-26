


# gitee
## gitee私有项目迁移到github
[参考链接](https://blog.csdn.net/qq598535550/article/details/87870931) 
```commandline
https://nongfugengxia:donghaiwang.1@gitee.com/nongfugengxia/dong.git
```


# 问题
## 头指针分离于 baf67ff
```commandline
# 强制将 master 分支指向当前头指针的位置
$ git branch -f master HEAD
# 检出 master 分支
$ git checkout master
```


## 连接github失败
取消全局代理：Failed to connect to github.com port 443: Timed out
```shell
git config --global --unset http.proxy
git config --global --unset https.proxy
```

## 撤销

### 撤销上一次push
查看你要回到的那个版本
```shell
git log
```
退到/进到 指定commit_id
```shell
git reset --hard commit_id
```
将本地的修改提交到远程
```shell
git push origin HEAD --force
```


### 撤销所有的已经add的文件  
```shell
git reset HEAD .
```
git reset HEAD 如果后面什么都不跟的话，就是上一次add 里面的全部撤销了 

### 撤销某个文件或文件夹
```shell
git reset HEAD -filename
```

## 将git commit的默认编辑器从nano转为vim
```shell
git config --global core.editor "vim"
```

## 清除提交记录
[彻底清除git所有历史提交记录使其为“新”库](https://www.jianshu.com/p/e2b3d04542cb) 
```shell
git checkout --orphan latest_branch
git add .
git commit -m "init"
git branch -D master
 git branch -m master
 git push -f origin master
```


# 自动化
## 自动push
shell脚本中实现自动push 更新，如果有更新，执行git  add,git commit,git push 等操作，没有则不操作。
```shell
cd ${repo_path}
if [ -n "$(git status -s)" ];then
    git add .
    git commit -m "update file"
    git push origin master
fi
```

# 命令

重新设置远端地址
git remote set-url origin https://gitee.com/dong_666/dong.git

## 搜索
只搜索指定语言，后面加上
```shell
language:MATLAB
```


## git拉取子目录
```buildoutcfg
git init
git remote add -f origin <url>
git config core.sparsecheckout true   #开启sparse clone
echo "mot/sture/TKP/*" >> .git/info/sparse-checkout   # 设置需要pull的目录，*表示所有，!表示匹配相反的 ".git/info/sparse-checkout" 是配置文件，通过该命令将配置写入里面
git pull origin master  ## “origin” 对应 step2 自定义 的名称  每次执行需要完整的代码， 仅仅执行“git pull” 不行
```




win10下git免密码：
https://github.com/donghaiwang/tracking.git
https://donghaiwang:donghaiwang.1@github.com/donghaiwang/tracking.git

显示当前项目的git配置
git config --list
git config --local remote.origin.url   (--sytem, --global)

git rm -r --cached . 	不删除本地文件
git rm -r --f .       	删除本地文件

先commit本地修改，然后pull，编辑冲突文件（解决冲突），然后在commit，最后git push这两次commit


回到指定commit id（短的）
git reset --hard e06c55
git branch --contains e06c55

git 提交时出现GNU nano编辑器：
Ctrl+O:		保存
Ctrl+X:		退出
然后再提交

执行git remote add origin git@github.com:djqiang/gitdemo.git报错：
fatal: remote origin already exists.
git remote rm origin
git remote add origin git@github.com:djqiang/gitdemo.git 就不会报错了！


每次push都需要输入用户名密码的问题
在个人配置目录下有一个 .gitconfig 的文件（建议使用文件搜索功能），里面会有你先前配好的name 和email，只需在下面加2行 
[credential] 
    helper = store

git reset --hard
（已提交，未推送） git reset --hard origin/master
（已推送）git reset --hard HEAD^
git push -f


保持全绿（assume-unchanged)
用小乌龟pull下远端的改动到本地(No Commit, No Fast Forward)
对比差别再进行提交(提交这个合并信息)

--assume-unchanged 假定开发人员不会更改文件。此标记旨在为无变化文件夹（如 SDK）改善性能。
--skip-worktree 用于命 GIT 不再染指特定文件——即便开发人员可能更改它——的情形。例如，如果主源码库上游承载某些即将投入生产的配置文件而你不希望意外的提交影响到那些文件，--skip-worktree 正是你的菜。
取消本地忽略
git update-index --no-assume-unchanged .idea/workspace.xml


git支持很多种工作流程，我们采用的一般是这样，远程创建一个主分支，本地每人创建功能分支，日常工作流程如下：
去自己的工作分支
$ git checkout work
工作
....
提交工作分支的修改
$ git commit -a


回到主分支
$ git checkout master
获取远程最新的修改，此时不会产生冲突
$ git pull
回到工作分支
$ git checkout work
用rebase合并主干的修改，如果有冲突在此时解决
$ git rebase master
回到主分支
$ git checkout master
合并工作分支的修改，此时不会产生冲突。
$ git merge work
提交到远程主干
$ git push

这样做的好处是，远程主干上的历史永远是线性的。每个人在本地分支解决冲突，不会在主干上产生冲突。

可以把在 C3 里产生的变化补丁在 C4 的基础上重新打一遍。在 Git 里，这种操作叫做衍合（rebase）。有了 rebase 命令，就可以把在一个分支里提交的改变移到另一个分支里重放一遍。



win10出现返回403
搜索栏中搜索“凭据”，点开凭据管理器，在“windows凭据”中删除和github相关的凭据，然后重新操作。


撤销git add
git reset HEAD .idea/datasystem-server.iml
1. 用git log 查看 commit日志
2. 找到需要回退的那次commit的 哈希值，git reset --hard commit_id 

冲突标记<<<<<<< （7个<）与=======之间的内容是我的修改，=======与>>>>>>>之间的内容是别人的修改。

pull操作实际上包含了fetch+merge操作
error: you need to resolve your current index first
放弃操作： （git reset --merge）
Team -> Reset -> Master(local)




Eclipse:
https://jingyan.baidu.com/article/bad08e1e9882ed09c8512187.html
将普通项目转成PHP项目：
.buildpath 增加<buildpathentry kind="con" path="org.eclipse.php.core.LANGUAGE"/>
打开workspace下面的.projcet文件在修改，再F5
<?xml version="1.0" encoding="UTF-8"?>
<projectDescription>
    <name>datasystem-server</name>
    <comment></comment>
    <projects>
    </projects>
    <buildSpec>
        <buildCommand>
            <name>org.python.pydev.PyDevBuilder</name>
            <arguments>
            </arguments>
        </buildCommand>
        <buildCommand>
            <name>org.eclipse.wst.common.project.facet.core.builder</name>
            <arguments>
            </arguments>
        </buildCommand>
        <buildCommand>
            <name>org.eclipse.wst.validation.validationbuilder</name>
            <arguments>
            </arguments>
        </buildCommand>
        <buildCommand>
            <name>org.eclipse.dltk.core.scriptbuilder</name>
            <arguments>
            </arguments>
        </buildCommand>
    </buildSpec>
    <natures>
        <nature>org.eclipse.php.core.PHPNature</nature>
        <nature>org.eclipse.wst.common.project.facet.core.nature</nature>
        <nature>org.python.pydev.pythonNature</nature>
    </natures>
</projectDescription>

同步远程代码：项目右键->Team->Advanced->Synchronized->wanghaidong
切换分之前stash保存现场：Team->Stashes->Stash changes
恢复现场：Team->Advanced->Synchronized->refs/stash
合并主分支：Team->Advanced->Synchronized->master



Ph: wanghaidong wanghaidong
PHRABRICATOR
authentication->VCS Password设置密码    wanghaidong

git config --global user.name "wanghaidong"
git config --global user.email "haidong.wang@hobot.cc"
git config -l

在/home/fastdb/ap2/datasystem-server目录下执行git status
datasys-server目录下初始时的文件：.arcconfig  build.sh    .git/       .gitignore  rdbuild.sh  tools/      www/  

查看远程分支：先进入cd  ./datasystem-server/
git branch -va
创建分支：git branch wanghaidong
把本地分支推送到远程分支：git push origin wanghaidong
切换到wanghaidong分支（当前分支有*）：git checkout wanghaidong

查看修改的文件：git status
添加所有修改的文件：git add .
git add ../conf/sdk.php (Untracked files:)
git commit -m 'test sdk upload'




git remote -v
git clone -b web http://phint.horizon-robotics.com/diffusion/LABEL/label.git




https://github-ranking.com/

stackoverflow上Java相关回答整理翻译
https://github.com/giantray/stackoverflow-java-top-qa


git clone http://phint.horizon-robotics.com/diffusion/DB/distributeddb.git
git init
 (git add .)
git commit -am 'first commit' 
git remote add master http://phint.horizon-robotics.com/diffusion/DB/distributeddb.git
git push master master

git status


代码review
arc diff
test plan填写2017.1.1就可以提交了??????????


arc diff --create


Q:
Usage Exception: No changes found. (Did you specify the wrong commit range?)
A:
git reset --hard

合并本地和master代码：
git merge origin/master

查看远程origin分支：git remote show origin

git log --pretty=oneline
 
让这个文件回到最近一次git commit或git add时的状态
git checkout -- readme.txt

git merge dev       合并指定分支到当前分支

git log --graph --pretty=oneline --abbrev-commit

git merge --no-ff -m "merge with no-ff" dev     合并能查看到历史分支

git stash 保留工作现场；       git stash list （查看有哪些工作现场）
git stash pop （恢复并删除现场）


8100




git  fetch origin master:wanghaidong
 


http://www.cnblogs.com/eedc/p/6168430.html
git remote add origin http://ph.horizon-robotics.com/diffusion/DATASYSTEMIISERVER/datasystem-server.git
git pull --rebase origin wanghaidong:wanghaidong


拉取远程分支到本地分支或者创建本地新分支
git clone http://ph.horizon-robotics.com/diffusion/DATASYSTEMIISERVER/datasystem-server.git
git fetch origin wanghaidong:wanghaidong
cp -r datasys/ /home/wanghaidong/AP2/git/sdk/datasystem-server/www

arc diff HEAD^
http://ph.horizon-robotics.com/D3993



提交到指定分支
git push origin wanghaidong:wanghaidong
git pull origin wanghaidong:wanghaidong




关联本地和远程分支
git branch --set-upstream-to=origin/wanghaidong wanghaidong
//         $level = $permission->getProjectLevel();

省略用户名密码pull
git config --global credential.helper store
git pull /git push (这里需要输入用户名和密码，以后就不用啦)

放弃本地所有修改：git checkout .

# TortoiseGit
## 进行回滚
[版本回退](https://blog.51cto.com/u_13478207/3338212) 
