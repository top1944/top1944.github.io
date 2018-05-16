# simulator

http://book.duckietown.org/master/duckiebook

https://github.com/duckietown

https://github.com/duckietown/simulator

# Duckietown Simulator
## 1 Installation

You will need to pull two separate github repos. Please ignore the instructions in the respective repos. This installation guide will walk you through the installation of both.

Pull the simulator client (doesn't matter where you put it):

cd ~/dev/ # for example, or cd ~/Documents

~~~
mkdir ~/duckietown

cd ~/duckietown

git clone https://github.com/duckietown/gym-duckietown.git
~~~

Install the simulator client globally on your PC:

sudo apt-get install python-pip

cd ~/duckietown/gym-duckietown

sudo pip2 install -e .

Pull the simulator server into your duckietown catkin workspace:

mkdir ~/duckietown/catkin_ws

mkdir ~/duckietown/catkin_ws/src

cd ~/duckietown/catkin_ws/src

git clone https://github.com/duckietown/duckietown-sim-server.git



Install dependencies for the sim-server

#TODO - do the students need any other deps?

If you've never evr run catkin_make after installing duckietown, you should do this now.

#TODO instructions on how to run catkin_make in duckietown

Test your Gazebo installation

cd /home/top/duckietown

git clone https://github.com/duckietown/Software

cd /home/top/duckietown/Software
source environment.sh
gazebo

This last command should start Gazebo and after some 10 seconds or so you should see an empty Gazebo simulator 3D environment.

#TODO add image

$ cd ~/catkin_ws
$ cd src
$ catkin_init_workspace
$ cd ..
$ mkdir build
$ cd build
$ cmake ../src -DCMAKE_INSTALL_PREFIX=../install -DCATKIN_DEVEL_PREFIX=../devel
$ make


# gym-gazebo

https://github.com/duckietown/gym-gazebo
