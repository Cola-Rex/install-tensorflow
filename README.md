# install-tensorflow
introduce how to install tensorflow for CentOS/Windows

## install tensorflow for CentOS
CentOS version : 7.2_64bit
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
