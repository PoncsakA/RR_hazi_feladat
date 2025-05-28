# RR_hazi_feladat

A repository for the GPS waypoint based navigation project.

##  Administrative information

Semester: 2024/25/2\
Subject: Robotic Systems Laboratory \
Subject code: BMEGEMINMRL\
Project: GPS waypoint navigation\
Members:
- Poncsák Ákos / RSXIRP
- Veres Kristóf / N7CARQ

## Project requirements

We were tasked to create a robot which is capable of following a path defined by GPS coordinates.\
We also had to create a gazebo world in which this robot was meant to move.

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
