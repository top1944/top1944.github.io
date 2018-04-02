##  xp安装python

相关软件下载链接：https://pan.baidu.com/s/1hOezW7uRUPVcrE6wXlYZSA 密码：9rr2

1. 安装python3.4  
XP只支持到python3.4，3.5以后不支持。  

 Microsoft's extended support phase for Windows XP ended on 2014-04-08, which predates the release of Python 3.5.0 (2015-09-13), therefore Python 3.5 does not support XP. (You just barely got in under the wire on 3.4, as 3.4.0 was released on 2014-03-17.)

2. 安装pywin32 兼容python3.4版本

   http://360jq.jb51.net:81/201601/tools/pywin32_3.4(jb51.net).rar

3. PyInstaller-3.0.tar 兼容python3.4版本  
  ~~~
  cd D:PyInstaller-3.0  
  python setup.py install  
  ~~~

4. 安装PyQt-5.4.1 兼容python3.4版本

  For windows the executable (both 32 bit and 64 bit) should be available on the website

  https://sourceforge.net/projects/pyqt/files/PyQt5/PyQt-5.4.1/

  https://sourceforge.net/projects/pyqt/files/PyQt5/PyQt-5.4.1/PyQt5-5.4.1-gpl-Py3.4-Qt5.4.1-x32.exe/download

  https://download.csdn.net/download/boliu123/9990462

5. 安装xlrd

  ~~~
  pip install xlrd
  ~~~

6. 打包成exe

  ~~~
  Pyinstaller -F -w 需要打包的文件.py
  ~~~
