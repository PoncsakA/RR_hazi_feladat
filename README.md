# RR_hazi_feladat

A repository for the GPS waypoint based navigation project.

##  Administrative informations

Semester: 2024/25/2\
Subject: Robotic Systems Laboratory \
Subject code: BMEGEMINMRL\
Project: GPS waypoint navigation\
Members: 
- Poncsák Ákos
- Veres Kristóf

## Requirements

These are the system requirements for our project

| Requirement ID          | Description |
| ----------- | ----------- |
| 1           | The System shall be able to see waypoints |
| 2           | The System shall be able to follow wayponts |
| 3           | The System shall be able to correct its heading |

## Launch command

ros2 launch hw_gazebo spawn_robot.launch.py world:=d_epulet.sdf rviz_config:=gps.rviz x:=0.0 y:=0.0 yaw:=0.0