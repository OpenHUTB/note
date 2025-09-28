
## 发布
文件`.github/workflows/compileandrelease.yml`中添加：
```shell
- name: Release
uses: softprops/action-gh-release@v1
if: startsWith(github.ref, 'refs/tags/')
with:
  files: PFC.pdf
env:
  GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
```
准备发布时候执行命令：
```shell
git tag v1.4
git push origin v1.4
```

* Action执行时候时如果出现：`GitHub error 403 undefined #400`

解决：在存储库设置中，转到`Actions -> General` 允许 Github 工作流的读写权限并保存更改。 如果您的存储库来自组织，您将需要执行额外的步骤，转到组织`settings -> Actions -> General`。

## 组织
添加write权限但不能直接push的权限：
项目`Setting`->`Branches`->`Add classic branch protection rule`，
Branch name pattern设置为要保护的分支（比如master），选中`Require a pull request before merging`。

## 开源课程

统计每个用户修改代码的行数：

右键选择`Git Bash Here`：
```shell
git log --format='%aN' | sort -u | while read name; do echo -en "$name\t"; git log --author="$name" --pretty=tformat: --numstat | awk '{ add += $1; subs += $2; loc += $1 + $2 } END { printf "added lines: %s, removed lines: %s, total lines: %s \n", add, subs, loc }' -; done
```

只显示修改函数（没有提示信息）：
```shell
git log --format='%aN' | sort -u | while read name; do echo -en "$name,"; git log --author="$name" --pretty=tformat: --numstat | awk '{ add += $1; subs += $2; loc += $1 + $2 } END { printf "%s \n", loc }' -; done > scores.csv
```


## Action
报错："/usr/src/entrypoint.sh": permission denied: unknown.
```shell
chmod +x entrypoint.sh
```
Windows
```shell
git update-index --chmod=+x script.sh
```

## Pull Request
在 Pull Request 页面的链接（比如`https://github.com/Tiryoh/actions-mkdocs/pull/224` ）后增加`.patch`即可获得patch 文件。


## 其他
项目标签:
https://shields.io/#/

其他人在github上提交代码(Pull Request)
https://blog.csdn.net/qq_33429968/article/details/62219783

git pull
fatal: No remote repository specified.  Please, specify either a URL or a
remote name from which new revisions should be fetched.
解决：.git/config中增加：
[remote "AI"]
	url = https://github.com/donghaiwang/AI.git

本地分支修改提交到github中：
git push origin HEAD -u


151.101.229.194 github.global.ssl.fastly.net  
52.74.223.119 github.com


全栈工程师：https://github.com/phodal/toolbox
地图leaflet

# 模板
向carla社区提交pull request的描述模板：
```text

<!--

Thanks for sending a pull request! Please make sure you click the link above to
view the contribution guidelines, then fill out the blanks below.
Please, make sure if your contribution is for UE4 version of CARLA you merge against ue4-dev branch. 
if it is for UE5 version of CARLA you merge agaisnt ue5-dev branch

Checklist:

  - [ ] Your branch is up-to-date with the `ue4-dev/ue5-dev` branch and tested with latest changes
  - [ ] Extended the README / documentation, if necessary
  - [ ] Code compiles correctly
  - [ ] All tests passing with `make check` (only Linux and ue4-dev)
  - [ ] If relevant, update CHANGELOG.md with your changes

-->

#### Description

<!-- Please explain the changes you made here as detailed as possible. -->

Fixes typo.
 <!-- If fixes an issue, please add here the issue number. -->

#### Where has this been tested?

  * **Platform(s):** Windows 10
  * **Python version(s):** 3.6
  * **Unreal Engine version(s):** 4.26



```