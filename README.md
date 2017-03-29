# install-tensorflow
introduce how to install tensorflow for CentOS/Windows

# 1.install tensorflow for CentOS
CentOS version : 7.2_64bit <br>
python version : 2.7.5

1、确保你的Python版本在2.7以上，可以使用`python -V`查看可以当前Python版本，
![python](http://img.blog.csdn.net/20170312220051947?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvRXpyZWFsX0tpbmc=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

如果版本过低，可以使用`yum install -U python`升级Python

2、使用`yum install python-pip`安装pip，通过yum在线安装的pip版本可能是8.1.2，再使用`pip install -U pip`对pip进行升级，升级后应该是9.0.1，使用`pip -V`查看
![pip](http://img.blog.csdn.net/20170312220213662?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvRXpyZWFsX0tpbmc=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

3、重点来了，之前看了些资料，说用`pip install -U tensorflow`直接安装tensorflow，但是执行这条指令之后，会一直报错，查了些资料，也没能解决。
所以决定直接把whl文件download下来安装，cpu版本的tensorflow地址为：https://pypi.python.org/pypi/tensorflow/1.0.1， 打开之后可以看到：
![pip-url](http://img.blog.csdn.net/20170312221837724?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvRXpyZWFsX0tpbmc=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)
可以看到2.7版本python对应的是箭头所指的位置，根据你的系统、Python版本选择相应的文件，点击之后会启动下载。

PS：如果你的网络打开上述网址或者下载很慢，可以使用国内的镜像站：https://pypi.tuna.tsinghua.edu.cn/simple/tensorflow/ ，然后打开页面查找`CTRL+F`，输入`tensorflow-1.0.1-cp27-cp27mu-manylinux1_x86_64.whl`，点击高亮的部分就能下载了
![清华镜像](http://img.blog.csdn.net/20170312223411146?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvRXpyZWFsX0tpbmc=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

4、cd到上述whl文件所在的目录，执行`pip install tensorflow-1.0.1-cp27-cp27mu-manylinux1_x86_64.whl -i https://mirrors.tuna.tsinghua.edu.cn/pypi/web/simple/`

后面的参数`-i https://mirrors.tuna.tsinghua.edu.cn/pypi/web/simple/`是为了从国内镜像站获取文件，如果使用默认下载地址，会非常非常慢。稍等片刻，因为需要安装升级一些依赖包。最后会出现：
![success](http://img.blog.csdn.net/20170312224904989?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvRXpyZWFsX0tpbmc=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

<hr>

到这里，安装基本完成了，接下来验证一下。
执行`python`：
![python](http://img.blog.csdn.net/20170312231103382?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvRXpyZWFsX0tpbmc=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

依次执行：

```
>>>import tensorflow as tf
>>>tf.__version__
>>>tf.__path__
```
获得如下结果：
![验证](http://img.blog.csdn.net/20170312231428091?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvRXpyZWFsX0tpbmc=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

**bingo**~TensorFlow的运行环境已经搭建成功。


# 2.install tensorflow for Windows
Windows version : 10 <br>
python version : 3.5.3

主要思路其实和在Linux上安装过程大致相同，如下：
`python -> pip -> tensorflow-xxx.whl -> 搞定~`
1、首先要注意的是，现阶段最新的发布版本**TensorFlow1.0.1**只能支持python3.5.x的版本，没错是“**只能**”，3.4以下的版本不支持很好理解，但是3.6也不支持，就是这么任性。
从链接https://www.python.org/ftp/python/3.5.3/python-3.5.3-amd64.exe （官网的）下载3.5.3版本的python，并安装。
在第一个界面注意给添加环境变量打勾：
![python](http://img.blog.csdn.net/20170322233313432?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvRXpyZWFsX0tpbmc=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

2、安装好之后，应该已经顺带安装了pip。打开PowerShell（或者命令提示符--`win+r`，输入`cmd`）。
输入`python.exe -V`查看python版本是否正确：
![python](http://img.blog.csdn.net/20170322233846476?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvRXpyZWFsX0tpbmc=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

再输入`pip.exe -V`查看pip版本：
![pip](http://img.blog.csdn.net/20170322233941263?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvRXpyZWFsX0tpbmc=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

3、去github的tensorflow项目—https://github.com/tensorflow/tensorflow 下载最新release版本，翻到下面可以看到：
![这里写图片描述](http://img.blog.csdn.net/20170322234503453?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvRXpyZWFsX0tpbmc=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)
箭头所指的就是可在windows运行的CPU版本了，点击“Python 3.5 64-bit”，即可开始下载，得到名为“tensorflow-1.0.1-cp35-cp35m-win_amd64.whl”的whl格式文件。用PowerShell进入到文件所在目录。

4、执行`pip.exe install .\tensorflow-1.0.1-cp35-cp35m-win_amd64.whl`，安装就开始了。稍等片刻：
![success](http://img.blog.csdn.net/20170322235432059?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvRXpyZWFsX0tpbmc=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)
看到最后的'Successfully installed ...'，就代表安装完成了。

<hr>

安装过程已经搞定，接下来就验证一下。
执行`python.exe`，依次输入并获得输出即代表安装成功了。
![验证](http://img.blog.csdn.net/20170322235912269?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvRXpyZWFsX0tpbmc=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/SouthEast)

bingo~
