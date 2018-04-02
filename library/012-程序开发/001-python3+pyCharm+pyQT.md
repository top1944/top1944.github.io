
## 安装pyCharm
教程：https://www.cnblogs.com/muziyunxuan/p/7985265.html  
显示表格：http://blog.csdn.net/zhulove86/article/details/52599738  
PyQt教程：http://www.cnblogs.com/archisama/p/5442071.html  

## py2exe
https://www.cnblogs.com/hanson1/articles/7101578.html

python setup.py py2exe


## pyinstaller生成exe文件

PyInstaller requires two Python modules in a Windows system. It requires either the PyWin32 or pypiwin32 Python extension for Windows. If you install PyInstaller using pip, and PyWin32 is not already installed, pypiwin32 is automatically installed. PyInstaller also requires the pefile package.

The pip-Win package is recommended, but not required.

py2exe太过陈旧缺少维护操作不便，推荐PyInstaller项目 www.pyinstaller.org可用一句命令打包：

pyinstaller -F -w -i manage.ico app.py

-F：打包为单文件

-w：Windows程序，不显示命令行窗口

-i：是程序图标，app.py是你要打包的py文件

另外需要pywin32。安装方法：先跑pip install pywin32再跑pip install pyinstaller即可，多么简单。



1.打开命令提示符：win+r，输入cmd，回车

<img src="https://pic1.zhimg.com/50/v2-bb432dd1287157791a1b29a51086d22c_hd.jpg">

2.直接写 pip install Pyinstaller，回车

<img src="https://pic3.zhimg.com/50/v2-7129c752248a34a0a2c3eab4c1ae4906_hd.jpg">

3.等待即可，然后你会看到Successfuly installed Pyinstaller-3.3（2017.10.3）4.可以通过直接输入Pyinstaller检测是否安装成功

<img src="https://pic1.zhimg.com/50/v2-30064c00762b57d61d9883a2aadb54d7_hd.jpg" data-rawwidth="993" data-rawheight="519" class="origin_image zh-lightbox-thumb" width="993" data-original="https://pic1.zhimg.com/v2-30064c00762b57d61d9883a2aadb54d7_r.jpg">


2、在命令行中切换到要打包的程序所在目录,直接输入下面的指令即可
pyinstaller -F -w -c xxx.py

https://pyinstaller.readthedocs.io/en/latest/usage.html

### lib not found: api-ms-win-crt-heap-l1-1-0.dll dependency of c:\python\python.exe

Just had this problem myself. The problem is that pyinstaller is not fully compatible Windows 10. The only solution currently is to download the Windows 10 SDK (a 2GB download).

https://developer.microsoft.com/en-us/windows/downloads/windows-10-sdk


https://stackoverflow.com/questions/39687975/pyinstaller-lib-not-found


## py生成win32文件
打包出来的EXE 在win7上都能跑，就是放到XP上会提示“不是有效的WIN32程序”


原因是pyinstaller高版本不支持XP了，打包的程序不能在XP上跑，需要使用pyinstaller3.2.1  
看看自己已装的是哪个版  
~~~
pip list
~~~
删掉高版
~~~
pip uninstall PyInstaller
pip install PyInstaller-3.2.1
~~~
然后去下载个pyinstaller3.2.1  
https://github.com/pyinstaller/pyinstaller/releases/download/v3.2.1/PyInstaller-3.2.1.tar.gz
然后放到script 里解压，再进入解压后的文件进行安装
~~~
python setup.py install  
~~~
不能用pip，不然又给你从网上下了个高版本  
然后再打包就可以了
