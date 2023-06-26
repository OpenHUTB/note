


拼写检查（https://www.cnblogs.com/tsingke/p/6127494.html）
https://languagetool.org/download/


sudo apt-get install texlive-full
sudo apt-get install texstudio
\usepackage[utf8]{ctex}

viso
alt+F9，可直接打开设置对话框，去掉相应勾选即可。
取消对齐和粘贴
删除白边： 设计-> 大小 -> 适应绘图

bibtex格式导出没有日期
修改导出：
Edit -> Output Styles -> Open Style Manager -> BibTex Export -> Edit
-> Bibliography -> Conference Proceedings -> year={Year Published}
Year of Conference
Save

@inproceedings{|`RN`Record Number,|
@inproceedings{|Label,|

&符号错误
变为 \&
然后删除.bbl文件，重新编译

删了.bbl可能需要重启TexStudio
否则参考文献全变成?
需要重启TexStudio


bmp转pes
bmeps -c time.png time.eps

.tex
.bib 参考文献
.cls 规定正文格式
.bst 规定参考文献格式
.sty 模板宏包

参考文献
\bibliography{ieee}		-> ieee不要后缀名.bib
C:\CTEX\MiKTeX\miktex\bin\bibtex.exe ieee	(Ctrl+Shift+B)

> latex yourfile
> echo yourfile|bibtex your_ref
> latex yourfile
> latex yourfile

# texstudio

* 没有卸载重新安装texstudio的.deb文件报错
```shell script
dpkg-deb: 错误: 粘贴 subprocess was killed by signal (断开的管道)
```
解决办法：强制覆盖原来已经安装的文件：
```shell script
sudo dpkg -i --force-overwrite texstudio_4.2.2-1+3.1_amd64.deb
```