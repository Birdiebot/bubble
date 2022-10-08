<div align="center">
<img src=".github/cover.png"/>
<div>
    <a href=""><img src="https://img.shields.io/badge/Bubble-v1.0%20Developer%20Preview-blue" alt="version" /></a>
    <a href="https://hub.docker.com/repository/docker/birdiebot/bubble-aarch64v8"><img src="https://img.shields.io/docker/pulls/birdiebot/bubble-aarch64v8?logo=docker" alt="Docker Pulls"></a>
    <a href="https://www.gnu.org/licenses/agpl-3.0.en.html"><img src="https://img.shields.io/badge/license-GNU AGPL3.0-green" alt="license" /></a>
    <a href="https://birdiebot.github.io/bubble_documentation/"><img src="https://img.shields.io/badge/Documentation-completely-success" alt="documentation" /></a>
</div>
</div>

English | [简体中文](.github/README_zhCN.md)


Bubble is a ROS2-based open-source software stack made by the Birdiebot Team founded by the Mechanics and Science Innovation Base in Shanghai University of Engineering Science. Bubble provides a series of solution to the RMU related visual tasks.

Bubble documentation is maintained on the [Bubble Documentation Page](https://birdiebot.github.io/bubble_documentation/), follow the link for details.

# Getting start
Step-by-step execution and configuration walk-through could be found [here](https://birdiebot.github.io/bubble_documentation/%E5%BF%AB%E9%80%9F%E5%BC%80%E5%A7%8B.html)。
## Build Bubble
```bash
# Install vcs tools
sudo apt-get install python3-vcstool
mkdir src

# Load source code
vcs import src < bubble.repos

# Build source code
colcon build --symlink-install
```
## Pre-building Docker Containers
```bash
# Allow external applications to connect to the host's display
xhost +

# Run the Bubble Docker container
docker run -it --rm --net=host --runtime nvidia \
    -e DISPLAY=$DISPLAY -v /tmp/.X11-unix/:/tmp/.X11-unix \
    --device=/dev/bus/usb/ --device=/dev/ttyTHS0 \
    -v /home/nvidia/Desktop/bubble:/home/bubble \
    birdiebot/bubble-aarch64v8:v1.0-l4t-r32.7.1 /bin/bash

# Run project
ros2 launch bubble_bringup infantry_launch.py
```
## Parameter Configuration
```bash
# Using infantry role as example here
# For detailed information, please check the bubble_bringup repo
# Modifying the configuration file
gedit ./src/bubble_bringup/config/infantry_param.yaml
gedit ./src/bubble_bringup/launch/infantry_launch.py

# Run project
. install/setup.sh
ros2 launch bubble_bringup infantry_launch.py
```

# Why Bubble
Bubble uses a modular design. Each module is maintained with independent repositories and thus new features could be adapted swiftly into our ecosystem.

[Here](https://birdiebot.github.io/bubble_documentation/getting_started/%E6%A8%A1%E5%9D%97%E8%BF%90%E8%A1%8C%E6%95%88%E6%9E%9C%E5%AE%9E%E4%BE%8B.html) is the demonstartion of Bubble in action.

|repos name | link | notes|
|---|---| --- |
|bubble_core|[bubble_core repo](https://github.com/Birdiebot/bubble_core) | Used for RMU communication protocol between MCU and onbord computer, contents of the protocol is documented in [birdiebot communication protocol manual](https://birdiebot.github.io/bubble_documentation/guide/%E6%9C%A8%E9%B8%A2%E9%80%9A%E8%AE%AF%E5%8D%8F%E8%AE%AE.html) |
|bubble_camera|[bubble_camera repo](https://github.com/Birdiebot/bubble_camera)| Maintains ROS packages for different cameras we used. `main` for common USB camera, `hikrobot_camera` for Hikrobot Industrial camera, and `gxusb_camera` for Daheng Industrial camera |
|bubble_interface|[bubble_interface repo](https://github.com/Birdiebot/bubble_interface)|Bubble inter-package message type definition|
|bubble_detector|[bubble_detector repo](https://github.com/Birdiebot/bubble_detector)|Visual module, `visual` uses traditional CV algorithms for armor detection, `visual_SJTU` package is a customized intergration of Shanghai Jiaotong University sentinel auto-aiming system with improved YOLOv5 network for armor detection, `visual_rune` package is for RMUC2019-2022 rune detection|
|bubble_contrib|[bubble_contrib repo](https://github.com/Birdiebot/bubble_contrib)|Package for RMU tasks. The `aiming` package for autoaiming (both armors and runes), and the `decesion` package for robot behavior contol using finite state machines (FSM)|
|bubble_resouces|[bubble_resouces repo](https://github.com/Birdiebot/bubble_resources)|Resource files that may be needed in the project, including ROS Bag data for testing purpose|
|bubble_navigation|[bubble_navigation repo](https://github.com/Birdiebot/bubble_navigation)|Robot URDF|
|bubble_bringup|[bubble_bringup repo](https://github.com/Birdiebot/bubble_bringup)|Launch files and configuration of each robot role|

 
# About us
Birdiebot is a school-level tech-innovation team oprated under the office of Academic Affairs in Shanghai University of Engineering Science. Supported by the Mechanics Innovation Base of Student Science and Technology Innovation Center, Birdiebot is committed to conduct technology innovation activities in robotics related affiars. We hope our work will encourage and promote new engineers for the robotics industry in China.

## Contributing
Everyone is welcomed to join the Bubble project to further imporve this ecosystem for the RoboMaster competition. We have some future work plans and ideas listed [here](https://birdiebot.github.io/bubble_documentation/resources/%E7%9B%B8%E5%85%B3%E9%A1%B9%E7%9B%AE.html).

## Contact
Questions could be raised through Issues page or in the RoboMaster forum. For Bubble related topics, you can also reach us at algorithm@birdiebot.top. 
We are also open for forum and demonstration sessions with Robomaster participants, either online or offline. Feel free to contact us at robomaster@birdiebot.top.

# License
Projects that Bubble's referenced or based on could be found [here](https://birdiebot.github.io/bubble_documentation/resources/%E7%9B%B8%E5%85%B3%E9%A1%B9%E7%9B%AE.html).

The Bubble project is licensed under the [GNU AGPL3.0 License](https://www.gnu.org/licenses/agpl-3.0.en.html).

Copyright of Shanghai University of Engineering Science Birdiebot Team. All rights reserved.
