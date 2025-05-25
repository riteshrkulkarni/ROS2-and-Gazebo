# ROS2-and-Gazebo
This repository contains a ROS2 package for simulating an ArduPilot Iris drone in Gazebo Classic. The setup is built using ROS2 Humble and is integrated with SLAM for autonomous navigation and mapping.
# Requirements
1.UBUNTU 22.04 LTS </br>
2. ROS-Humble </br>
3.Gazebo Garden </br>
4.Ardupilot </br>

# UBUNTU 22.04 LTS
1. Install and setup in Virtual box or dual boot. </br>
https://ubuntu.com/download/desktop </br>

# ROS2-Humble 
1. Referred from https://docs.ros.org/en/humble/Installation/Ubuntu-Install-Debians.html </br>
2. Steps to install and setup </br>
  i) set locale </br>
   ```
   locale
   sudo apt update && sudo apt install locales
   sudo locale-gen en_US en_US.UTF-8
   sudo update-locale LC_ALL=en_US.UTF-8 LANG=en_US.UTF-8
   export LANG=en_US.UTF-8
3. Add the ROS2 apt repository</br>
   First ensure that the https://help.ubuntu.com/community/Repositories/Ubuntu (Ubuntu universe repository) is enabled. </br>
   ```
   sudo apt update && sudo apt install curl -y
   sudo curl -sSL https://raw.githubusercontent.com/ros/rosdistro/master/ros.key -o /usr/share/keyrings/ros-archive-keyring.gpg

4. Now add the ROS 2 GPG key with apt. </br>
  ```
sudo apt update && sudo apt install curl -y
sudo curl -sSL https://raw.githubusercontent.com/ros/rosdistro/master/ros.key -o /usr/share/keyrings/ros-archive-keyring.gpg
  ```

5. Then add the repository to your sources list.
```
      echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/ros-archive-keyring.gpg] http://packages.ros.org/ros2/ubuntu $(. /etc/os-release && echo $UBUNTU_CODENAME) main" | sudo tee       /etc/apt/sources.list.d/ros2.list > /dev/null
```

6.Install Development tools and ROS tools. </br>
  install common packages</br>
  ```
sudo apt update && sudo apt install -y \
  python3-flake8-docstrings \
  python3-pip \
  python3-pytest-cov \
  ros-dev-tools
```
Install packages according to your Ubuntu version.</br>
```
sudo apt install -y \
python3-flake8-blind-except \
python3-flake8-builtins \
python3-flake8-class-newline \
python3-flake8-comprehensions \
python3-flake8-deprecated \
python3-flake8-import-order \
python3-flake8-quotes \
python3-pytest-repeat \
python3-pytest-rerunfailures
```

# Get ROS2 Node
Create a workspace and clone all repos: </br>
```
mkdir -p ~/ros2_humble/src
cd ~/ros2_humble
vcs import --input https://raw.githubusercontent.com/ros2/ros2/humble/ros2.repos src
```
# Install dependencies using rosdep
ROS 2 packages are built on frequently updated Ubuntu systems. It is always recommended that you ensure your system is up to date before installing new packages. </br?
```
sudo apt upgrade
```
```
sudo rosdep init
rosdep update
rosdep install --from-paths src --ignore-src -y --skip-keys "fastcdr rti-connext-dds-6.0.1 urdfdom_headers"
```
Note: If you’re using a distribution that is based on Ubuntu (like Linux Mint) but does not identify itself as such, you’ll get an error message like Unsupported OS [mint]. In this case append --os=ubuntu:jammy to the above command. </br>

# Build the code in the Workspace
If you have already installed ROS 2 another way (either via debs or the binary distribution), make sure that you run the below commands in a fresh environment that does not have those other installations sourced. Also ensure that you do not have source /opt/ros/${ROS_DISTRO}/setup.bash in your .bashrc. You can make sure that ROS 2 is not sourced with the command printenv | grep -i ROS. The output should be empty. </br>
More info on working with a ROS workspace can be found in http://docs.ros.org/en/humble/Tutorials/Beginner-Client-Libraries/Colcon-Tutorial.html  </br>
```
cd ~/ros2_humble/
colcon build --symlink-install
```
Note: if you are having trouble compiling all examples and this is preventing you from completing a successful build, you can use COLCON_IGNORE in the same manner as CATKIN_IGNORE to ignore the subtree or remove the folder from the workspace. Take for instance: you would like to avoid installing the large OpenCV library. Well then simply run touch COLCON_IGNORE in the cam2image demo directory to leave it out of the build process. </br>

# Environment Setup
# Source the setup script
Set up your environment by sourcing the following file </br>
```
. ~/ros2_humble/install/local_setup.bash
```

# Gazebo Garden




