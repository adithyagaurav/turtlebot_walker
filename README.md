# TurtleBot Walker

A ROS 2 package developed for turtlebot to depict walker behavior of a robotics vacuum cleaner. The basic functionality of the robot is that it will explore it's enviroment and avoid any obstacle. In case the robot is in a distance to an obstacle which is less than a threshold, it will rotate until path ahead of it cleared. This is a iterative behavior, hence robot goes back to moving forward once path is cleared.

[![License](https://img.shields.io/badge/License-BSD_3--Clause-blue.svg)](https://opensource.org/licenses/BSD-3-Clause)

## Overview
Turtlebot walker is based on Roomba robot which is a vacuum cleaner robot. It can move in unexplored environment once in operation. The robot uses its laser scan to detect any obstacles it might encounter. The robot changes its path if an obstacle is encountered and resumes to moving forward once obstacle is cleared.

For this project, this behavior was implemented and simulated in a Gazebo environment. The robot interacts with its enivornment with the help of ROS2 middleware. The robot subscribes to '''/scan''' topic and publishes the velocity command to the '''/cmd_vel''' 

### Dependencies
* Ubuntu 20.04
* ROS 2 Foxy
* Turtlebot3 package for ROS 2 [![installation instructions](https://ros2-industrial-workshop.readthedocs.io/en/latest/_source/navigation/ROS2-Turtlebot.html)]
* Gazebo [![installation instructions](http://classic.gazebosim.org/tutorials?tut=ros2_installing&cat=connect_ros)]

### Build instructions
'''
mkdir -p ~/ros2_ws/src
cd ~/ros2_ws/src
'''

* Clone the repository
'''
git clone ------
'''

* Build the workspace
'''
cd ~/ros2_ws
colcon build --packages-select -----
'''

* Set turtbot3 variable for model
'''
echo  "export TURTLEBOT3_MODEL=waffle_pi" >> ~/.bashrc
'''

### Run Instructions

* Without ROS Bag record
'''
. install/setup.bash
ros2 launch turtlebot_walker launch_walker.launch.py
'''

* With ROS Bag record
'''
. install/setup.bash
ros2 launch turtlbot_walker launch_walker.launch.py record:=True
'''

* Inspect the ROS bag with following command
'''
ros2 bag info <path_to_rosbag_record_file>
'''
* To play with ROS bag, close gazebo and exit the launch file. 
- Open a new terminal
'''
cd ~/ros2_ws
. install/setup.bash
ros2 run turtlebot3_gazebo turtlebot3_world.launch.py
'''

- Open another new terminal
'''
cd ~/ros2_ws
. install/setup.bash
ros2 bag play <path_to_rosbag_record_file>
'''

* Executing this, Turtlebot3 would start replaying the behavior exhibited during ROS bag recording