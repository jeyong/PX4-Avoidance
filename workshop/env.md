# 개발환경
## 동작 확인한 버전
 * PX4 Firmware
   * v1.11.1 ~ 1.11.2
   * commit : e0f6c220
 * Avoidance
   * 2020. 11. 3.
   * commit : 8a957267

## 설치
 * Ubuntu 18.04
   * [다운로드](https://releases.ubuntu.com/18.04/)
 * PX4 설치
```
> git clone https://github.com/PX4/PX4-Autopilot
> cd PX4-Autopilot/Tools/setup
> ./ubuntu.sh
```

 * ROS 설치 ([melodic](http://wiki.ros.org/melodic/Installation/Ubuntu))
```
> sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'
> sudo apt-key adv --keyserver 'hkp://keyserver.ubuntu.com:80' --recv-key C1CF6E31E6BADE8868B172B4F42ED6FBAB17C654
> sudo apt update
> sudo apt install ros-melodic-desktop-full
> echo "source /opt/ros/melodic/setup.bash" >> ~/.bashrc
> source ~/.bashrc
> sudo apt install python-rosdep python-rosinstall python-rosinstall-generator python-wstool build-essential
> sudo apt install python-rosdep
> sudo rosdep init
> rosdep update
```

 * Avoidance 설치
```bash
> sudo apt install python-catkin-tools
> mkdir -p ~/catkin_ws/src
> sudo apt install ros-melodic-mavros ros-melodic-mavros-extras
> wget https://raw.githubusercontent.com/mavlink/mavros/master/mavros/scripts/install_geographiclib_datasets.sh
> chmod +x install_geographiclib_datasets.sh
> sudo ./install_geographiclib_datasets.sh
> sudo apt install libpcl1 ros-melodic-octomap-*
> cd ~/catkin_ws/src
> git clone https://github.com/PX4/avoidance.git
> catkin build -w ~/catkin_ws
> echo "source ~/catkin_ws/devel/setup.bash" >> ~/.bashrc
> source ~/.bashrc

# Gazebo Build
> cd ~
> git clone https://github.com/PX4/Firmware.git --recursive
> cd ~/Firmware
> ./Tools/setup/ubuntu.sh --no-sim-tools --no-nuttx
> sudo apt install gstreamer1.0-plugins-bad gstreamer1.0-plugins-base gstreamer1.0-plugins-good gstreamer1.0-plugins-ugly libgstreamer-plugins-base1.0-dev
> export QT_X11_NO_MITSHM=1
> make px4_sitl_default gazebo
> . ~/Firmware/Tools/setup_gazebo.bash ~/Firmware ~/Firmware/build/px4_sitl_default
> export ROS_PACKAGE_PATH=${ROS_PACKAGE_PATH}:~/Firmware
> echo "export GAZEBO_MODEL_PATH=${GAZEBO_MODEL_PATH}:~/catkin_ws/src/avoidance/avoidance/sim/models:~/catkin_ws/src/avoidance/avoidance/sim/worlds" >> ~/.bashrc
> sudo apt install ros-melodic-stereo-image-proc ros-melodic-image-view
> roslaunch local_planner local_planner_stereo.launch
```

 * Visual Studio Code
```
$ sudo apt-get install curl
$ sudo sh -c 'curl https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > /etc/apt/trusted.gpg.d/microsoft.gpg'
$ sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/vscode stable main" > /etc/apt/sources.list.d/vscode.list'
$ sudo apt update
$ sudo apt install code

```
 * Chrome
```
> wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | sudo apt-key add -
> sudo sh -c 'echo "deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main" >> /etc/apt/sources.list.d/google.list'
> sudo apt-get update
> sudo apt-get install google-chrome-stable
> sudo rm -rf /etc/apt/sources.list.d/google.list
```
