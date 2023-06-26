


vim --startuptime tmp.txt
发现2157.463  2128.285: setup clipboard 时间很长
如果加了启动参数-X后，没有了上面两项或者上面两项耗费的时间少，那就说明是下面的这个原因了
vim在启动时会去连接X Server以便它能使用剪切板（clipboard）和窗口标题
只需要在配置文件~/.vimrc中加入下面一行：
set clipboard=exclude:.*
即可在保留X11 Forward功能的同时，加快vim启动速度。


sudo apt-get install vim-gnome
vim --version | grep xterm_clipboard

curl -sLf https://spacevim.org/install.sh | bash
-s --silent
-L --Location
	如果移动了，会重定向到新的链接
-f --fail
	阻止显示服务器返回的错误

每行显示行号
/etc/vim/vimrc中添加：set nu

在2~50行首添加#号注释
:2,50 s/^/#/g
s/old/new/g	用old替换new，替换当前行的所有匹配

:2,50 s/^#//g  在2~50行首删除#号

取消注释：
Ctrl + v 进入块选择模式，选中你要删除的行首的注释符号，注意# 要选中两个，选好之后按d即可删除,ESC退出。


vim8安装
sudo add-apt-repository ppa:jonathonf/vim
sudo apt update
sudo apt install vim

python IDE
https://blog.csdn.net/alanzjl/article/details/49383943


/home/cidi/.vim/bundle/nerdtree/plugin/NERD_tree.vim 73
72行去掉！成为：  	 if nerdtree#runningWindows()



自动补全：ctrl-N

使用16进制模式编辑文件
:%!xxd      参数%指当前所编辑的文件 
:%!xxd -r       将十六进制还原为二进制

无插件Vim编程
http://blog.csdn.net/wrwerew/article/details/43054065
 
VIM配置
curl https://j.mp/spf13-vim3 -L > spf13-vim.sh && sh spf13-vim.sh
ls -lha ~ | grep vim
za    展开折叠
zo      展开折叠
zc      折叠
set mouse=a    鼠标左键有用；set mouse=c 鼠标左键无用
:PluginInstall  查看安装了哪些插件
"set nofoldenable"， 保存文件，再用vim打开代码文件，折叠功能消失
windows安装
Installing Chocolatey
cmd
@"%SystemRoot%\System32\WindowsPowerShell\v1.0\powershell.exe" -NoProfile -InputFormat None -ExecutionPolicy Bypass -Command "iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))" && SET "PATH=%PATH%;%ALLUSERSPROFILE%\chocolatey\bin"
install spf13-vim
choco install spf13-vim

PIV
在任意php内建函数上操作<Shift-k>，可以查看该函数的manual
vundle（插件管理）
ctrlp（快速文件查找）
surround（管理结对符）
nerdcommenter（快速注释）
:map    查看快捷键
,cc     注释
,cu     取消注释
syntastic（语法检查）
numbers.vim（更好的行数）
NeoComplete（自动补全），
ctrl+n 来提示补全代码段
Tabularize
tagbar（标签导航）
EasyMotion（任意跳转）
snipmate（代码模版）
NERDTree  文件导览
ctr+h 光标focus左侧树形目录，ctrl+l 光标focus右侧文件显示窗口

ctags
进入源代码根目录ctags -R *
从根目录下打开要浏览的源文件
跳转：Ctrl+]
返回：Ctrl+t




编辑
全部复制：按esc后，然后ggyG

每行的行首都添加一个字符串：%s/^/要插入的字符串 
每行的行尾都添加一个字符串：%s/$/要插入的字符串
:% s/^/\/\//g     在全部内容的行首添加//号注释
:2,50 s/^/\/\//g  在2~50行首添加//号注释
:2,50 s/^\/\///g  在2~50行首删除//号
解释： 
% 代表针对被编辑文件的每一行进行后续操作 
$ 代表一行的结尾处 
^ 代表一行的开头处
+            移动到下一行开头
-            移动到上一行开头

dw，这是在此之前我用的对做的也几乎是唯一掌握的一个操作技巧。从光标当前的位置开始删除，直到删到单词最后。
D    从当前位置删除到行尾 ("d$" 的缩写)
daw，算是1的属性扩充版，这个命令可以直接删除光标所在的一个单词。为了方便记忆，可以记忆为deletea word缩写。
bdw，这也是一个复合命令。B可以让光标回退到单词开头的位置，而dw则是第1个描述过的命令。
另外再有就是删除一个字符，操作为x。


：n，$s/vivian/sky/g 替换第 n 行开始到最后一行中每一行所有 vivian 为 sky 

:% s/^/\/\//g     在全部内容的行首添加//号注释
:2,50 s/^/\/\//g  在2~50行首添加//号注释          :2056,2078 s/^/;/g
:2,50 s/^\/\///g  在2~50行首删除//号                  :2056,2078 s/^;//g
替换空行：
:1,$s/^$\n//g
每行的行首都添加一个字符串：%s/^/要插入的字符串
每行的行尾都添加一个字符串：%s/$/要插入的字符串
解释：
% 代表针对被编辑文件的每一行进行后续操作
$ 代表一行的结尾处
^ 代表一行的开头处


i：在当前字符的左边插入
a      //在当前光标位置的右边添加文本
A     //在当前行的末尾位置添加文本
I：在当前行首插入
O     //在当前行的上面新建一行
o     //在当前行的下面新建一行
R    //替换(覆盖)当前光标位置及后面的若干文本
J    //合并光标所在行及下一行为一行(依然在命令模式)

x //删除当前字符
nx //删除从光标开始的n个字符
dd //删除当前行
ndd //向下删除当前行在内的n行
u //撤销上一步操作
U //撤销对当前行的所有操作
多行删除 ，：1,10d
删除所有内容：
方法1:    按ggdG
方法2:       :%d

选择
全选：ggVG （gg：光标移动到首行；V：进入Visual模式；G：光标移动到最后一行。
v：按字符选择。V：按行选择
  对于选中的文本进行如下按键：
d   ------ 剪切操作
y   -------复制操作
p   -------粘贴操作
^  --------选中当前行，光标位置到行首（或者使用键盘的HOME键）
$  --------选中当前行，光标位置到行尾（或者使用键盘的END键）




?atool     //向光标上搜索atool字符串
N         //向上搜索前一个搜索动作


导航
滚屏
Ctrl+f            往前滚动一整屏
Ctrl+b            往后滚动一整屏
Ctrl+d            往前滚动半屏
Ctrl+u            往后滚动半屏
Ctrl+e            往后滚动一行        
Ctrl+y            往前滚动一行

用z调整光标
z<Enter>        将光标所在行移动到屏幕顶端
z.              将光标所在行移动到屏幕中间
z-              将光标所在行移动到屏幕低端

在屏幕中移动
H            移动到屏幕顶端的行
M            移动到屏幕中央的行
L            移动到屏幕底端的行
nH           移动到屏幕顶端往下的第n行
nL           移动到屏幕顶端往上的第n行

在当前行移动
^            移动到当前行的第一个非空格处
n|           移动到当前行的第n列

根据文本块移动
（            移动到当前句子开头
）            移动到下一个句子开头
{            移动到当前这一段开头   
}            移动到下一段开头
[[           移动到当前这一节的开头
]]           移动到下一节的开头

根据行号来移动
Ctrl+g            显示当前行信息
nG                转至第n行
G                 转至文本末尾
gg　　　　　　　　   移至文本开头

空格键 向右、Backspace  向左、Enter  移动到下一行首、-  移动到上一行首


w 跳到下一个单词的开始
e 跳到单词的结束
b 向后跳
w：光标以单词向前移动 nw：光标向前移动n个单词 光标到单词的第一个字母上
b：与w相反 3b, 3w
n+        //向下跳n行
n-         //向上跳n行
nG        //跳到行号为n的行
G           //跳至文件的底部
$ → 到本行行尾
0 → 数字零，到行头
. → (小数点) 可以重复上一次的命令
100idesu [ESC]
% : 匹配括号移动
fa → 到下一个为a的字符处，你也可以fs到下一个为s的字符。

:set nonu    //取消显示行号

nyy   //将当前行向下n行复制到缓冲区
yw    //复制从光标开始到词尾的字符
nyw   //复制从光标开始的n个单词
y^      //复制从光标到行首的内容。
y$      //复制从光标到行尾的内容。

:s/old/new/g         //用new替换行中所有的old
:%s/old/new/g      //用new替换当前文件里所有的old
s: search 在扩展模式下完成查找替换操作
　　格式：s/要查找的内容/替换为的内容/修饰符
g: 全局替换；默认情况下，每一行只替换第一次出现

:e otherfilename    //编辑文件名为otherfilename的文件。
set fileformat=unix   //将文件修改为unix格式，如win下面的文本文件在linux下会出现^M

w 跳到下一个单词的开始
e 跳到单词的结束
b 向后跳

【gf】  – 打开光标处所指的文件 （这个命令在打到#include头文件时挺好用的，当然，仅限于有路径的）
ctrl+^  对应gf跳回来

在命令模式下，首先执行  gg
这里是跳至文件首行
再执行：dG
这样就清空了整个文件！

:e  重新加载

切分窗口
:vs 垂直分
:sp 水平分
ctrl+w  [hjkl] 切换窗口





超强vim配置文件                  https://github.com/ma6174/vim       
http://www.cnblogs.com/ma6174/archive/2011/12/10/2283393.html
http://blog.csdn.net/bokee/article/details/6633193

Latex: https://tex.stackexchange.com/questions/339/latex-editors-ides

配置文件~/.vimrc
vi ~/.vimrc
set number
set nu


Vim的插件（plugin）: Vim命令行下运行"set rtp“命令查看; 安装在~/.vim

显示帮助文档: help keycodes

sp, vs

撤销 u
恢复刚才的撤销操作      ctrl+r
复制当前行，粘贴        yy; p
选择复制：              v进入可视模式,选择文本按 "+y ,到粘贴的地方按 p

y     在使用v模式选定了某一块的时候，复制选定块到缓冲区用 
yy    复制整行（nyy或者yny ，复制n行，n为数字）； 
y^    复制当前到行头的内容； 
y$    复制当前到行尾的内容； 
yw    复制一个word （nyw或者ynw，复制n个word，n为数字）； 
yG    复制至档尾（nyG或者ynG，复制到第n行，例如1yG或者y1G，复制到档尾）

移动当前行向上或向下：dd 然后在合适的地方 p 或者 P


代码配置文件的快捷键：
sp         水平分割窗口
vs         垂直分割
ctrl+w     快速窗口切换
F6         按pep8格式对代码格式优化
F5         一键执行代码


运行TlistToggle命令就可以打开Taglist窗口，再次运行TlistToggle则关闭


默认打开显示行号：vi ~/.vimrc
set number
在Vim中选择时不包括行号：
:set mouse=a
自动缩近：
set ts=4
set number

set tabstop=4
set softtabstop=4
set shiftwidth=4
set autoindent
set cindent
set expandtab



 :sp 另外一个文件的路径及文件名


Question
E464: Ambiguous use of user-defined command
:$      G.
:help E464

Q：鼠标右键复制不出来
:set mouse-=a

Q: 打开文件不自动换行
:set wrap
