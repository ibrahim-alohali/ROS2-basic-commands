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
```bash
sudo apt update
sudo apt install software-properties-common
sudo add-apt-repository universe
sudo apt update && sudo apt install curl
sudo curl -sSL https://raw.githubusercontent.com/ros/rosdistro/master/ros.key -o /usr/share/keyrings/ros-archive-keyring.gpg
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/ros-archive-keyring.gpg] http://packages.ros.org/ros2/ubuntu $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/ros2.list > /dev/null
sudo apt update
sudo apt install ros-humble-desktop
