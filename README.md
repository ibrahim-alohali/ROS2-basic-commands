# ROS2-basic-commands

# ROS2 Turtlesim Task

This project demonstrates basic usage and manipulation of the `turtlesim` package in ROS2 (Humble) on Ubuntu 22.04.  
It covers installation, running the simulator, sending commands to the turtle, and drawing simple shapes via the command line.

---

## Table of Contents

- [Prerequisites](#prerequisites)
- [Setup](#setup)
- [Running turtlesim](#running-turtlesim)
- [Basic Turtle Control](#basic-turtle-control)
- [Drawing Shapes](#drawing-shapes)
    - [Circle](#circle)
    - [Square (Manual)](#square-manual)
- [Troubleshooting](#troubleshooting)
- [References](#references)
- [Files Included](#files-included)

---

## Prerequisites

- Ubuntu 22.04 (recommended, or compatible)
- ROS2 Humble installed
- Internet access
- VirtualBox (if using a VM)
- Basic Linux command line skills

---

## Setup

**Install ROS2 Humble Desktop:**
```
sudo apt update
sudo apt install software-properties-common
sudo add-apt-repository universe
sudo apt update && sudo apt install curl
sudo curl -sSL https://raw.githubusercontent.com/ros/rosdistro/master/ros.key -o /usr/share/keyrings/ros-archive-keyring.gpg
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/ros-archive-keyring.gpg] http://packages.ros.org/ros2/ubuntu $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/ros2.list > /dev/null
sudo apt update
sudo apt install ros-humble-desktop
Install turtlesim:
sudo apt install ros-humble-turtlesim
Source ROS2 in every terminal before running ROS2 commands:
source /opt/ros/humble/setup.bash
```
## Running turtlesim
```
Start turtlesim node:
ros2 run turtlesim turtlesim_node
```
## Basic Turtle Control
Reset the simulation (clears the window):
```
ros2 service call /reset std_srvs/srv/Empty
```
Move turtle to center, facing right (x=5.5, y=5.5, theta=0):
```
ros2 service call /turtle1/teleport_absolute turtlesim/srv/TeleportAbsolute "x: 5.5
y: 5.5
theta: 0.0"
```
Set pen color, width, and state:
```
ros2 service call /turtle1/set_pen turtlesim/srv/SetPen "r: 255
g: 0
b: 0
width: 2
off: 0"
```
Move forward (single step):
```
ros2 topic pub -1 /turtle1/cmd_vel geometry_msgs/msg/Twist "{linear: {x: 2.0, y: 0.0, z: 0.0}, angular: {x: 0.0, y: 0.0, z: 0.0}}"
```
Rotate in place (single step):
```
ros2 topic pub -1 /turtle1/cmd_vel geometry_msgs/msg/Twist "{linear: {x: 0.0, y: 0.0, z: 0.0}, angular: {x: 0.0, y: 0.0, z: 2.0}}"
```
## Drawing Shapes
# Circle
Start a continuous circular motion (Ctrl+C to stop):
```
ros2 topic pub /turtle1/cmd_vel geometry_msgs/msg/Twist "{linear: {x: 1.5, y: 0.0, z: 0.0}, angular: {x: 0.0, y: 0.0, z: 1.5}}"
```
# Triangle (Manual)
1. Move forward (side of square):
```
ros2 topic pub -1 /turtle1/cmd_vel geometry_msgs/msg/Twist "{linear: {x: 2.0, y: 0.0, z: 0.0}, angular: {x: 0.0, y: 0.0, z: 0.0}}"
```
2. Turn 90° left:
```
ros2 topic pub -1 /turtle1/cmd_vel geometry_msgs/msg/Twist "{linear: {x: 0.0, y: 0.0, z: 0.0}, angular: {x: 0.0, y: 0.0, z: 2.0}}"
```

