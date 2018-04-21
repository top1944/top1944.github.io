http://community.bwbot.org/topic/191/ubuntu-%E5%AE%89%E8%A3%85vnc-%E6%9C%8D%E5%8A%A1

ubuntu 安装VNC 服务

 
在用Ubuntu的时候经常需要远程桌面连接，最常用的软件就是VNC。VNC是一个开放的协议，实现的客户端有很多。但是比较各个实现之后，目前最好的就是x11vnc。这个程序不仅不收费，是开源的，而且还支持opengl程序。比如rviz之类的程序也可以正常打开了。

下面介绍一下安装方法。下面是以Ubuntu 14.04为例子，如果是16.04及以后版本要做服务配置文件要做对应修改。

安装x11vnc

sudo apt-get install x11vnc -y

设置访问密码

sudo x11vnc -storepasswd /etc/x11vnc.pass 

创建服务文件

在/etc/init 下创建一个x11vnc.conf的文件，文件内容如下

description "xiaoqiang vnc server"

start on runlevel [2345]

stop on runlevel [06]

script

    exec /usr/bin/x11vnc -auth guess -capslock -forever -loop -noxdamage -repeat -rfbauth /etc/x11vnc.pass -rfbport 5900 -shared

end script

启动服务

sudo service x11vnc start

访问服务

下载一个vnc客户端,比如从这里下载

https://www.realvnc.com/en/connect/download/viewer/

打开客户端

输入目标IP，连接后输入密码，之后就可以正常连接了。

对于16.04版本和更新版本的Ubuntu，可以按照这个文件的方法进行配置

https://github.com/longhr/ubuntu1604hub/blob/master/ubuntu1604VNC.sh

注意安装完成之后在不插显示器使用rviz时还是会报错。这时后插上hdmi转vga的转接头（不接显示器，只是转接头）就可以打开正常使用了。如果想要调整分辨率可以像正常电脑设置分辨率一样，在设置里面进行调整