

![欢迎](http://en.robotis.com/img/sub/pruduct_logo_TB3.png?ver=20180202 "欢迎！")  

官网下载：  
≆ 讲义资料 https://github.com/ROBOTIS-GIT/ros_seminar    
≆ 参考资料 https://github.com/ROBOTIS-GIT/ros_book  
≆ 源代码资料 https://github.com/ROBOTIS-GIT/ros_tutorials  
ROS机器人编程中文版CSDN下载：   
http://download.csdn.net/download/kkllkxf/9676552  
教程：
http://turtlebot3.robotis.com  

## 安装
在控制TurtleBot3机器人的用户PC（在这里我们称为远程PC）上安装：    
~~~
sudo apt-get install ros-kinetic-joy ros-kinetic-teleop-twist-joy ros-kinetic-teleop-twist-keyboard ros-kinetic-laser-proc ros-kinetic-rgbd-launch ros-kinetic-depthimage-to-laserscan ros-kinetic-rosserial-arduino ros-kinetic-rosserial-python ros-kinetic-rosserial-server ros-kinetic-rosserial-client ros-kinetic-rosserial-msgs ros-kinetic-amcl ros-kinetic-map-server ros-kinetic-move-base ros-kinetic-urdf ros-kinetic-xacro ros-kinetic-compressed-image-transport ros-kinetic-rqt-image-view ros-kinetic-gmapping ros-kinetic-navigation  
~~~
用如下命令下载相应存储库中的源代码。（例：ros_tutorials功能包）  
~~~
cd ~/catkin_ws/src/
git clone https://github.com/ROBOTIS-GIT/ros_tutorials.git
git clone https://github.com/ROBOTIS-GIT/turtlebot3.git
git clone https://github.com/ROBOTIS-GIT/turtlebot3_msgs.git
git clone https://github.com/ROBOTIS-GIT/turtlebot3_simulations.git
cd ~/catkin_ws && catkin_make
~~~
在TurtleBot3机器人自带的PC上安装：省略  
因为我们没有使用实际机器人，在此自进行仿真。    

# 使用RViz 仿真 TurtleBot3
即使您没有TurtleBot3的硬件，您也可以遥控TurtleBot3，还可以测试SLAM和导航，因此是非常有用的方法。具体方法是使用turtlebot3_simulations元功能包。要在这个元功能包中使用虚拟仿真，首先需要安装turtlebot3_fake功能包。  
运行虚拟机器人  
要运行虚拟机器人，请按如下所示运行turtlebot3_fake功能包的turtlebot3_fake.launch文件。  
~~~
export TURTLEBOT3_MODEL=burger  
roslaunch turtlebot3_fake turtlebot3_fake.launch
~~~
它运行turtlebot3_fake_node节点和robot_state_publisher节点。其中，
turtlebot3_fake_node节点从turtlebot3_description功能包导入TurtleBot3的三维模
型，并发布实际机器人发布的话题。robot_state_publisher节点则通过接收机器人的
两个车轮的旋转值，以TF形式发布两个车轮及各关节的三维位置和方向信息。但是，
由于在RViz中无法使用传感器信息，所以需要使用包含物理引擎的3D仿真器Gazebo。
下一节将介绍Gazebo，在本节中，我们只介绍在简单的运动和移动过程中可以确认的
Odometry和TF。

下一步操作是运行RViz并在左侧显示窗口中将 [Global Options] →
[fixed frame]更改为“/odom”，然后按下显示窗口左下方的添加按钮，再点击
“RobotModel”来添加机器人模型，但是由于我们已经从turtlebot3_fake.launch文
件中加载了TurtleBot3的3D模型，所以您会在画面中央看到TurtleBot3的3D模型，如图
所示。

## 遥控
接下来，我们来运行这个虚拟机器人。运行turtlebot3_teleop功能包中的
turtlebot3_teleop_key.launch文件，该文件允许用键盘操纵机器人。
~~~
roslaunch turtlebot3_teleop turtlebot3_teleop_key.launch
~~~
运行turtlebot3_teleop_key.launch文件将启动turtlebot3_teleop_keyboard节
点。turtlebot3_fake_node节点接收由turtlebot3_teleop_keyboard节点通过/cmd_
vel话题发送的平移速度和旋转速度，并将其作为驱动命令，并用此命令驱动虚拟机器
人。在执行turtlebot3_teleop_key.launch文件的终端窗口中，让我们直接使用下面的
键运行机器人。  
■ w 键：前进(+0.01, 单位=m/sec)
■ x 键：后退(-0.01, 单位=m/sec)
■ a 键：逆时针方向旋转(+0.1, 单位=rad/sec)
■ d 键：顺时针方向旋转(-0.1, 单位=rad/sec)
■ 空格或者s键：初始化平移速度及旋转速度
■ Ctrl + C：退出
###  Odometry和TF
我们已经尝试了虚拟机器人的驱动，下面让我们查看其他话题值。例如，如图所示，turtlebot3_fake_node节点会接收速度命令以生成测位（odometry）信息并将其以话题形式发布，还可以发布joint states或tf，从而在RViz中查看TurtleBot3的移动
情况。




# Dependencies

Gzweb is a graphical interface which communicates with gzserver. To use
 gzserver, install either [Gazebo](http://gazebosim.org/install) or [DRCSim](http://gazebosim.org/tutorials?tut=drcsim_install&cat=drcsim).

 1. Make sure your system has the right NodeJS version (0.10.x). While this is
 not the latest version, it is the version that ships with Ubuntu Trusty.

    >**Note:** For Ubuntu Precise or older distributions, the NodeJS version that comes with it may not work with gzweb. In that case, set up your system to grab and install the latest NodeJS debs:

    ~~~~
    dpkg -l nodejs
    ~~~

    >If the above command returns a version < 0.10 or couldn't find the nodejs package use:

    ~~~
    curl -sL https://deb.nodesource.com/setup | sudo bash -
    ~~~

    >We will install the nodejs package in the following step.

 1. Next, install the dependencies from a terminal:

    ~~~
    sudo apt-get install libjansson-dev nodejs npm libboost-dev imagemagick libtinyxml-dev mercurial cmake build-essential
    ~~~


# Clone the repository and build

 1. Clone the repository into a directory in your home folder:

    ~~~
    cd ~; hg clone https://bitbucket.org/osrf/gzweb
    ~~~

 1. Enter the Gzweb repository and switch to a release branch:

    ~~~
    cd ~/gzweb
    # Note for Gazebo versions < 7, please use the gzweb_1.2.0 branch
    hg up gzweb_1.3.0
    ~~~

 1. The first time you build, you'll need to gather all the Gazebo models in the right directory and prepare them for the web. Before running the deploy script, you'll need to source the Gazebo setup.sh file:

    >If you installed gazebo via deb packages:

    ~~~
    source /usr/share/gazebo/setup.sh
    ~~~

    >If you did a source install then:

    ~~~
    source <YOUR_GAZEBO_PATH>/share/gazebo/setup.sh
    ~~~

 1. If you have drcsim then source:

    ~~~
    source /usr/share/drcsim/setup.sh
    ~~~

 1. Run the deploy script, this downloads models from the web and may take a couple of minutes.

    ~~~
    ./deploy.sh -m
    ~~~

    >Note: the `-m` flag tells the deploy script to grab models from the model database and any other models in your Gazebo paths. For all subsequent builds, the `-m` flag will not be needed. The process will also try to generate thumbnails, see note on thumbnails below.

## Options

* To skip downloading models from the model database and grab only local models in your Gazebo model path, do:

        ./deploy.sh -m local

* To generate thumbnails manually, run the script with the `-t` flag, i.e.:

        ./deploy.sh -t

    >Note: This spins up a gzserver with a camera for capturing screenshots of models. So make sure there is rendering support and no background gzerver process running (or set a different `GAZEBO_MASTER_URI` in the terminal).

* If you'll use gzweb on mobile devices, you can create coarse versions of all models, which are lighter to load (50% of original quality). If generated, these meshes will automatically be used on mobile devices. If you've already ran `./deploy.sh -m`, run just:

        ./deploy.sh -c

    Or you can run both flags at the same time to generate coarse versions as you create the database:

        ./deploy.sh -m -c

* You also have the option to pick specific models and how much percent to coarsen, running:

        ./coarse_meshes.sh [percent] [path]

    Here, `[percent]` is the edges ratio with respect to the original mesh (0 to 100), and `[path]` is the path of the models. For example:

        ./coarse_meshes.sh 20 http/client/assets/bowl/

# Running gzserver, gzweb server, and WebGL client

1. Start gazebo or gzserver first:

    ~~~
    gzserver
    ~~~

1. On another terminal, from your gzweb directory, start the http and websocket servers:

    ~~~
    ./start_gzweb.sh
    ~~~

1. Open a browser (Chrome works well) that has WebGL and websocket support and point it to the ip address and port where the http server is started, by default it's on port 8080, e.g.

    ~~~
    http://localhost:8080
    ~~~

    > You can use the `-p` option to choose an arbitrary port, for example: `./start_gzweb.sh -p 1234`

1. To stop Gzweb server, from your gzweb directory, run:

    ~~~
    ./stop_gzweb.sh
    ~~~

# Troubleshooting

 * **Q: When installing node package modules, I see errors along the lines of:**

        npm ERR! Error: failed to fetch from registry: node-gyp

    A: Try setting the npm registry first then install the modules again.

        npm config set registry http://registry.npmjs.org/

 * **Q: When installing websocket, I see errors along the lines of:**

        sh: 1: node: not found
        npm ERR! error installing websocket@1.0.8
        npm WARN This failure might be due to the use of legacy binary "node"

    **Or along the lines of:**

        /usr/bin/env: node: No such file or directory
        There are node-gyp build errors, exiting.

    A: In Debian systems, the binary file "node" has been renamed to "nodejs" to avoid a name conflict. Try adding a symlink to the correct name:

        sudo ln -s /usr/bin/nodejs /usr/bin/node

    You may also find that your repository is too old and you should just install recent versions of node and npm directly.

 * **Q: When running `./deploy.sh`, it is missing a file in `gz3d/build`:**

    A: You will need to install Grunt and run it appropriately, as described in the [development](http://gazebosim.org/tutorials?tut=gzweb_development) section.

 * **Q: When running `./deploy.sh`, I see errors along the lines of:**

        gyp ERR! configure error

    A: There might be a conflict between the gyp version installed and the gyp version in node-gyp. Try removing gyp:

        sudo apt-get remove gyp

 * **Q: When running `./deploy.sh`, I have problems finding GTS, like this:**

        ~/gzweb/tools/gzcoarse.cc:18:17: fatal error: gts.h : no such file or directory, #include <gts.h>

    A: It seems that your Gazebo installation didn't install GTS headers. Try installing them manually:

        sudo apt-get install libgts-dev
