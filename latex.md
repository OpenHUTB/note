

# 文档
[用户手册](https://htmlpreview.github.io/?https://github.com/texstudio-org/texstudio/master/utilities/manual/usermanual_en.html)


# Pandoc
将markdown文件导出为pdf
```shell
pandoc D:\dong\note\google.md --pdf-engine=xelatex -o google.pdf
```
注意：包含外文字符（中文）需要加上`--pdf-engine=xelatex`。

# arxiv
[注意事项](https://blog.sciencenet.cn/blog-562867-1085842.html)

Q: determine the encoding of your source and add a \usepackage[encoding name]{inputenc} or 2) add the \UseRawInputEncoding as the first line of your source file.

在\document后面添加：
```buildoutcfg
\usepackage[utf8]{inputenc}
```
如果有中文字符（比如中文逗号（，），编译就会报错。



## 需要保留.bbl文件

# 脚本
[参考](https://github.com/texstudio-org/texstudio/wiki/Scripts)

# Lyx
所见即所得
[下载](https://www.lyx.org/Download)

# 安装字体
# Microsoft YaHei
1.从windows的 `C:\Windows\Fonts` 目录中拷贝 `msyh.ttf` （普通）和 `msyhbd.ttf ` （加粗）到 Linux 中的 `/usr/share/fonts/win` 目录（没有就新建）中；

2.建立可缩放字形文件的索引信息（mkfontscale: create an index of scalable font files），更新字体缓存（build font information cache files）。
```shell script
cd /usr/share/fonts/win
mkfontscale
fc-cache
```
3.查看本机器所安装的中文字体
```shell script
fc-list | grep msyh
```

# 命令

## TEX 宏命令
参考[链接](https://tex.stackexchange.com/questions/78101/when-and-why-should-i-use-tex-ts-program-and-tex-encoding) 。

## \par
强制换段

压缩过大的eps文件
```
convert tracking_result.jpg eps3:tracking_result.eps
```


#自定义

## 参考文献
命令行生成.bst文件[说明](https://kingdomhe.wordpress.com/2017/12/02/%E5%A6%82%E4%BD%95%E8%87%AA%E5%AE%9A%E4%B9%89-bibtex-%E7%9A%84%E5%8F%82%E8%80%83%E6%96%87%E7%8C%AE%E6%A0%BC%E5%BC%8F-bst-%E6%96%87%E4%BB%B6-how-to-generate-a-customized-bst-file/) 。

引用处的引用标记方式。 如果目标方式是 方括 [1] 上角标， 则选择 Numerical as in standard LaTeX。 


## 修改参考文献
设计`Bibtex`风格，修改参考文献说明，即修改.bst文件。

[语法说明教材](https://blog.sina.com.cn/s/blog_6cf921f301018psq.html)

官方说明位于：
```bat
texlive\2016\texmf-dist\doc\bibtex\base\btxhak.pdf
```


## 命令
带圈圈数字
\usepackage{tikz}
\newcommand*{\circled}[1]{\lower.7ex\hbox{\tikz\draw (0pt, 0pt)%
    circle (.5em) node {\makebox[1em][c]{\small #1}};}}
使用：
\circled{1}

## 宏
Macros --> Edit macros --> Add
```buildoutcfg
name: Red
LaTex Content: \textcolor{red}{%|}
```
默认快捷键为Shift+F1，可以再区Options->Config TeXstudio -> Shortcuts -> Menus -> Macros 中去改变默认快捷键

# 快捷键
[参考](https://courses.edx.org/courses/course-v1:IITBombayX+LaTeX101x+1T2021/ea8d82b5d10849188679815198e196ba/)
Alt+Delete: 删除当前单词
            或者\textcolor{red}只剩下red
            
Ctrl+D      Select line

Ctrl+L      Select line

Ctrl+K      Delete line 

Alt+K       Delete till the end of line

Ctrl+Alt+Shift  Copy Block (text)

## LaTex
| 快捷键               | 含义                             |
| --------            | :-----                          | 
| Ctrl+E              |  \begin{env} ... \end{env}      | 
| Ctrl+Shift+I        |  \item                          |
| Ctrl+B              |  Bold                           |
| Ctrl+Enter          |  New line \\\\                  |

## PDF
| 快捷键        | 含义    |
| --------     | :----- | 
| Ctrl+ click (in pdf)          |  Go to source     |
| F7          |  Go to Go to pdf     |  


# 技巧
## 实时预览
[参考](https://www.icode9.com/content-4-1189580.html)


# Texstudio
[源码编译](https://github.com/texstudio-org/texstudio/wiki/Compiling)
```buildoutcfg
apt-get install qtbase5-dev qt5-default qt5-qmake libqt5svg5-dev qtdeclarative5-dev qttools5-dev libqt5svg5-dev libpoppler-qt5-dev libpoppler-cpp-dev pkg-config zlib1g-dev git
(sudo apt-get install libpoppler-qt5-dev libpoppler-cpp-dev)
git clone https://github.com/texstudio-org/texstudio.git
cd texstudio
qmake
make -j 8
```
安装qtcreate
```buildoutcfg
sudo apt install qtcreator
```
打开texstudio.pro工程文件


# 其他

ktikz编译过程
mkdir build
cd build
qmake ../qtikz.pro
make
make install
如果报告缺少了poppler-qt4.h，则安装libpoppler-qt4-dev即可。


s.t.全称subject to，意思是使得...满足...（约束条件）


花体字母有不同的几种写法
$\mathcal{R}$   调出的是欧拉书(eucal)写体，而不是通常地计算机现代书写体
$\mathbb{R}$
$\mathscr{R}$


latex保存时自动进行编译
.tex所在目录或者用户主目录新建latexmkrc文件
$pdf_mode = 1;
$pdflatex = "xelatex -file-line-error --shell-escape -src-specials -synctex=1 -interaction=nonstopmode %O %S;cp %D %R.pdf";
$recorder = 1;
#$pdf_previewer = "SumatraPDF -reuse-instance -inverse-search -a %O %S";
$pdf_previewer = "open -a %S";
#连续编译模式
$preview_continuous_mode = 1;
$pdf_update_method = 0;
$clean_ext = "synctex.gz acn acr alg aux bbl bcf blg brf fdb_latexmk glg glo gls idx ilg ind ist lof log lot out run.xml toc dvi";
$bibtex_use = 2;
$out_dir = "temp";
#指定生成PDF文件的文件名，可以与LaTeX主文件名不一致
#$jobname = "Book";

编译监控
latexmk main.tex


中间点
Windows-----【Alt+0183】，按住Alt键，在数字区域打0183

texstudio实时刷新
latexmk -pvc -pdf -silent bare_jrnl.tex
latexmk -pvc -pdf -silent

matlab, python, cpp, java
matlab-word
      -latex(ppt)

bib文件中包含&符号


用 ^ 来表示上标，用 _ 来表示下标，如果上标的内容多于一个字符，注意用 { } 把上标括起来
\frac{numerator}{denominator} \sqrt{expression_r_r_r}表示开平方，
\sqrt[n]{expression_r_r_r} 表示开 n 次方.


使用的编译器
latex：用.eps，用png格式图片会报错
PdfLaTeX：用png格式，用eps会报错

jpg/png转eps
bmeps -c fig1.png fig1.epss


sudo apt-get install texlive        (sudo apt-get install texlive-full)
sudo apt-get install texmaker



//1.xetex集成了中文字体的环境，使得中文文档的生成变得很容易
sudo apt-get install texlive-xetex texlive-latex-recommended
//2.查看安装的tex版本
tex --version
//3.编写Hello Latex
vi test.tex
\documentclass{article}
\begin{document}
Hello LaTex!
\end{document}
//4.生成pdf
xelatex test.tex
//5.中文字体
fc-list :lang=zh
// 根据短提示，搜索安装包叫什么
sudo apt-cache search libhpdf
