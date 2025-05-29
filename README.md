# RR_hazi_feladat

A repository for the GPS waypoint based navigation project.

## Table of Contents
1. [Administrative information](#administrative-information)
1. [Demonstration video](#demonstration-video)
1. [Project requirements](#project-requirements)
1. [Required packages](#required-packages)
1. [Installation](#installation)
1. [Launch command](#launch-command)
1. [Further development ideas](#further-development-ideas)
## Administrative information

Semester: 2024/25/2\
Subject: Robotic Systems Laboratory \
Subject code: BMEGEMINMRL\
Project: GPS waypoint navigation\
Members:
- Poncsák Ákos / RSXIRP
- Veres Kristóf / N7CARQ

## Demonstration video

IDE MÉG A YOUTUBEOT BE KELL ÁGYAZNI

## Project requirements

We were tasked to create a robot which is capable of following a path defined by GPS coordinates.\
We also had to create a gazebo world in which this robot was meant to move.

## Packages
This robot was developed to work with [ROS2 Jazzy](https://docs.ros.org/en/jazzy/Installation/Ubuntu-Install-Debs.html), on [Ubuntu 24.04 LTS](https://ubuntu.com/blog/tag/ubuntu-24-04-lts).

[Gazebo Harmonic](https://gazebosim.org/docs/harmonic/install_ubuntu/) is used as the simulation environment. To make them work together, we also need an integration package for ROS2:
```
sudo apt install ros-jazzy-ros-gz
```
Link:
- [ros-jazzy-ros-gz](https://github.com/gazebosim/ros_gz)

For urdf support and for some added convenience, we need the following packages:
```
sudo apt install ros-jazzy-urdf ros-jazzy-urdf-launch
```
Links:
- [ros-jazzy-urdf](https://github.com/ros/urdf)
- [ros-jazzy-urdf-launch](https://github.com/ros/urdf_launch)

It isn't strictly required, but it is recommended to install the [teleop twist keyboard](https://github.com/ros-teleop/teleop_twist_keyboard) if you want to control the robot manually:
```
sudo apt install ros-jazzy-teleop-twist-keyboard
```

To bridge parameters between ROS2 and Gazebo, we'll need the [ros-gz-bridge](https://github.com/gazebosim/ros_gz/tree/ros2/ros_gz_bridge):
```
sudo apt install ros-jazzy-ros-gz-bridge
```

We used the [trajectory server](https://github.com/MOGI-ROS/mogi_trajectory_server) provided during the course, however it is not needed to install it separately, because we have it in our repo as well.
```
git clone https://github.com/MOGI-ROS/mogi_trajectory_server
```

For [IMU visualization](https://github.com/CCNYRoboticsLab/imu_tools/tree/jazzy/rviz_imu_plugin) in RViz, we need another plugin:
```
sudo apt install ros-jazzy-rviz-imu-plugin 
```

For sensor fusion, install the [localization package](https://docs.ros.org/en/melodic/api/robot_localization/html/index.html):
```
sudo apt install ros-jazzy-robot-localization
```

For RViz map visualization, install [another package](https://github.com/nobleo/rviz_satellite):
```
sudo apt install ros-jazzy-rviz-satellite
```

For easy orientation conversions, install [tf-transformations](https://github.com/DLu/tf_transformations/tree/main/):
```
sudo apt install ros-jazzy-tf-transformations
```


## Installation

1. Clone the repository
    ```
    git clone git@github.com:PoncsakA/RR_hazi_feladat.git
    ```
2. Cd into the repository and build the packages
    ```
    cd RR_hazi_feladat
    colcon build
    ```
3. Source the installation for ros2 to be aware of the installed packages
    ```
    source install/setup.bash
    ```

## Launch command
Launch the world and spawn the robot:
```
ros2 launch hw_gazebo spawn_robot.launch.py world:=d_epulet.sdf rviz_config:=gps.rviz x:=0.0 y:=0.0 yaw:=0.0
```
You can control the robot yourself with the teleop keyboard:
```
ros2 run teleop_twist_keyboard teleop_twist_keyboard
```
Or you can start the gps waypoint navigation controller:
```
ros2 run hw_nav_py gps_waypoint_follower
```
## Further development ideas
The waypoint controller currently only follows a hardcoded path. In rviz, there's the option to publish a point (altough it uses cartesian coordinates, so we'd need to convert it to lat/lon).
Using this, it is possible, to make the waypoint following robot more interactive.
