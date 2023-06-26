




texstudio:
配置External PDF Viewer
"D:/software/pdf/Acrobat/Acrobat.exe"  "?am.pdf"
?: extended filename options
显示高级选项
?am : complete absolute filename enclosed in double-quotes

# acrobat

## Ubuntu acrobat安装
匿名登录acrobat: 
```buildoutcfg
ftp ftp.adobe.com
```
用户名：anonymous
```buildoutcfg
wget http://ardownload.adobe.com/pub/adobe/reader/unix/9.x/9.5.5/enu/AdbeRdr9.5.5-1_i486linux_enu.bin
```

[参考](https://blog.csdn.net/lyfwill/article/details/90484456)



## 文档无法保存。读取本文档时出现问题(110)
A: 合并任意一个文件(建立一个空pdf文档)


编辑——首选项——辅助工具，右边忽略页面提示，前面两个对勾去掉（前提是去掉勾之前是：单页连续，适合宽度），首选项里面的页面设置不用管。这样设置后，不管打开什么文档都是想要的显示模式。

插件部署（Bookmarks.api）：
https://github.com/binghe/acrobat-actions/releases/tag/v2.0
把编译生成的插件（.api）放到Adobe Acrobat或Reader安装目录下的Plug-ins文件夹中，然后打开Acrobat或Reader即可，程序会自动加载插件。
2：让所有书签 首字母都大写

菜单“文件》属性》初始视图”中设置了隐藏菜单栏。

让adobe reader 工具栏 菜单栏自动隐藏，不需要每次都按F8F9
先找到程序安装目录，然后再进入AcroApp\CHS文件夹，默认路径应该是“C:\Program Files (x86)\Adobe\Acrobat 2015\Acrobat\AcroApp\CHS”；
建个新文件夹，名字任意，比如“XX”；
找到以下三个文件：
AppCenter.aapp（工具Tab），
Home.aapp（主页Tab），
Viewer.aapp（右边的工具栏）；
将这三个文件移动到“XX”文件夹；


pycharm

默认打开是自动换行：
Setting -> Editor -> soft-wrap -> 添加 ;*