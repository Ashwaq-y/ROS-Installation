# ROS-Installiation
In this repository I will show the steps of installing ROS on Ubuntu 20.04 and installing ROS on jetson nano.
## Installing ROS Noetic on Ubunto
Using Ubunto 20.04 on virtual machine VirtualBox, we can Install ROS by entering the following commands in the terminal:
### Setup source.list
```
sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'
```
### Setup Keys
```
sudo apt install curl # if you haven't already installed curl

curl -s https://raw.githubusercontent.com/ros/rosdistro/master/ros.asc | sudo apt-key add -
```
### Instalition
```
sudo apt update

sudo apt install ros-noetic-desktop-full
```
### Enviroment Setup
```
echo "source /opt/ros/noetic/setup.bash" >> ~/.bashrc
```
 ### To check that ROS has been installed correctly
 ```
 roscore
 ```
 and the result should be as follow
 
![Picture4](https://user-images.githubusercontent.com/108296165/177630581-709dc432-40c5-469b-b910-be3f84edfa80.png)
