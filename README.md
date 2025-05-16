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

# ROS-Humble 
1. Referred from https://docs.ros.org/en/humble/Installation/Ubuntu-Install-Debians.html </br>
2. Steps to install and setup </br>
  i) set locale </br>
    ```
          locale
     sudo apt update && sudo apt install locales
        sudo locale-gen en_US en_US.UTF-8
          sudo update-locale LC_ALL=en_US.UTF-8 LANG=en_US.UTF-8
            export LANG=en_US.UTF-8```
