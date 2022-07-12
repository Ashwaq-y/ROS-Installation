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


# Installing ROS2 on jetson nano
First we need to flash Ubuntu 20.04 [(download it from here)](https://github.com/Discombobulated88/Xubuntu-20.04-L4T-32.3.1/releases/download/v1.0/Xubuntu-20.04-l4t-r32.3.1.tar.tbz2) to SD using [Balena Etcher](https://www.balena.io/etcher/) program.
```
1- extract the balena etcher program
2- extract the Ubuntu image using the following command: tar -xvjf Xubuntu-20.04-l4t-r32.3.1.tar.tbz2
then flash it to the SD card using balena etcher
```
Then after inserting the sdd card to jetson nano and start it, it will show an ubuntu interface it will some basic set up. 
Install ROS2 using the following comand in the terminal:

### Set locale
```
locale  # check for UTF-8

sudo apt update && sudo apt install locales

sudo locale-gen en_US en_US.UTF-8

sudo update-locale LC_ALL=en_US.UTF-8 LANG=en_US.UTF-8

export LANG=en_US.UTF-8

locale  # verify settings
```

### Set up sources
```
apt-cache policy | grep universe
```
The output should be like this:
```
500 http://us.archive.ubuntu.com/ubuntu focal/universe amd64 Packages
    release v=20.04,o=Ubuntu,a=focal,n=focal,l=Ubuntu,c=universe,b=amd64
```
If not use the following command:
```
sudo apt install software-properties-common
sudo add-apt-repository universe
```

```
sudo apt update && sudo apt install curl gnupg2 lsb-release
sudo curl -sSL https://raw.githubusercontent.com/ros/rosdistro/master/ros.key  -o /usr/share/keyrings/ros-archive-keyring.gpg

echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/ros-archive-keyring.gpg] http://packages.ros.org/ros2/ubuntu $(source /etc/os-release && echo $UBUNTU_CODENAME) main" | sudo tee /etc/apt/sources.list.d/ros2.list > /dev/null
```

### Install ROS 2 packages
```
sudo apt update

sudo apt upgrade

sudo apt install ros-foxy-desktop
```

### Environment setup
```
source /opt/ros/foxy/setup.bash
```


References:

[ROS Neotic](http://wiki.ros.org/noetic/Installation/Ubuntu)

[ROS2](https://docs.ros.org/en/foxy/Installation/Ubuntu-Install-Debians.html#id5)










