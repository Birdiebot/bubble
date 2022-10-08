
<div align="center">
<img src="cover.png"/>
<div>
    <a href=""><img src="https://img.shields.io/badge/Bubble-v1.0%20Developer%20Preview-blue" alt="version" /></a>
    <a href="https://hub.docker.com/repository/docker/birdiebot/bubble-aarch64v8"><img src="https://img.shields.io/docker/pulls/birdiebot/bubble-aarch64v8?logo=docker" alt="Docker Pulls"></a>
    <a href="https://www.gnu.org/licenses/agpl-3.0.en.html"><img src="https://img.shields.io/badge/license-GNU3.0-green" alt="license" /></a>
    <a href="https://birdiebot.github.io/bubble_documentation/"><img src="https://img.shields.io/badge/Documentation-completely-success" alt="documentation" /></a>
</div>
</div>

[English](../README.md) | 简体中文

Bubble是一个上海工程技术大学学生科创中心机械创新基地木鸢birdiebot战队维护视觉算法开源软件栈。Bubble基于ROS2开发，Bubble提供了一系列RMU相关视觉算法相关任务。  

Bubble的文档维护在[Bubble文档页](https://birdiebot.github.io/bubble_documentation/)，您可以找到Bubble的设计文档和详细信息。

# 开始使用
## 构建Bubble
```bash
# Install vcs tools
sudo apt-get install python3-vcstool
mkdir src

# Load source code
vcs import src < bubble.repos

# Build source code
colcon build --symlink-install
```
## 通过预构建Docker容器
```bash
# Allows external applications to connect to the host's display
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
## 配置相关参数
```bash
# As infantry example
# More detail see bubble_bringup repo
# Modifying configuration file
gedit ./src/bubble_bringup/config/infantry_param.yaml
gedit ./src/bubble_bringup/launch/infantry_launch.py

# Run project
. install/setup.sh
ros2 launch bubble_bringup infantry_launch.py
```

详细的使用和配置信息，您可以参阅[快速开始](https://birdiebot.github.io/bubble_documentation/%E5%BF%AB%E9%80%9F%E5%BC%80%E5%A7%8B.html)。

# Bubble功能包
Bubble的不同部分在不同的仓库中进行维护，你可以灵活的组合仓库中不同的功能包。我们在[这里](https://birdiebot.github.io/bubble_documentation/getting_started/%E6%A8%A1%E5%9D%97%E8%BF%90%E8%A1%8C%E6%95%88%E6%9E%9C%E5%AE%9E%E4%BE%8B.html)展示了Bubble目前实现的效果。

功能包的详细说明可以参见功能包仓库的README文件和[Bubble设计文档](https://birdiebot.github.io/bubble_documentation/design/bubble%E6%A8%A1%E5%9D%97.html)。

|仓库名称 | 地址| 说明|
|---|---| --- |
|bubble_core|[bubble_core仓库地址](https://github.com/Birdiebot/bubble_core) | 适用于RoboMaster竞赛上下位机通讯协议，协议内容被维护在[通讯协议手册](https://birdiebot.github.io/bubble_documentation/guide/%E6%9C%A8%E9%B8%A2%E9%80%9A%E8%AE%AF%E5%8D%8F%E8%AE%AE.html)中 |
|bubble_camera|[bubble_camera仓库地址](https://github.com/Birdiebot/bubble_camera)| 维护了不同相机的ROS包，其中`main`分支维护了普通usb相机，`hikrobot_camera`分支维护了海康机器人工业相机，`gxusb_camera`维护了大恒图像工业相机 |
|bubble_interface|[bubble_interface仓库地址](https://github.com/Birdiebot/bubble_interface)|框架功能包间消息类型定义|
|bubble_detector|[bubble_detector仓库地址](https://github.com/Birdiebot/bubble_detector)|视觉识别器，`visual`功能包使用传统视觉识别装甲板，`visual_SJTU`对上海交通大学哨兵自瞄系统二次开发，使用基于改进YOLOv5的神经网络识别装甲板，`rune`功能包识别RMUC2019-2022能量机关|
|bubble_contrib|[bubble_contrib仓库地址](https://github.com/Birdiebot/bubble_contrib)|实现了RoboMaster竞赛中的各项任务。`aiming`功能包维护了瞄准(自动瞄准及能量机关击打)相关内容，`decesion`功能包使用有限状态机(FSM)控制机器人执行 |
|bubble_resouces|[bubble_resouces仓库地址](https://github.com/Birdiebot/bubble_resources)|测试ROS BAG及项目中可能需要的资源文件|
|bubble_navigation|[bubble_navigation仓库地址](https://github.com/Birdiebot/bubble_navigation)|机器人模型发布相关文件|
|bubble_bringup|[bubble_bringup仓库地址](https://github.com/Birdiebot/bubble_bringup)|机器人顶层bringup launch文件|



# 关于我们
木鸢Birdiebot战队是上海工程技术大学教务处组织的校级学生科创团体，依托上海工程技术大学学生科创中心机械创新基地，以RoboMaster机甲大师赛为平台，致力于在机器人赛事、机器人生态、以及工程文化等多领域开展学生科创活动，培育中国智造卓越的青年工程师。

## 参与Bubble项目
我们欢迎您与我们一起参与和维护Bubble项目，一同构建RoboMaster视觉算法软件生态。关于Bubble项目未来的维护，我们有一些初期的想法，您可以通过[这里](https://birdiebot.github.io/bubble_documentation/project/%E9%A1%B9%E7%9B%AE%E6%B2%BB%E7%90%86.html)参与到bubble项目的维护和治理中。

## 联系我们
你可以通过github issues页面、RoboMaster论坛提出问题。关于视觉算法交流、Bubble项目治理，您可以通过algorithm@birdiebot.top联系我们。同时我们也欢迎RoboMaster参赛队伍与我们开展线上与线下的各种形式交流活动，您可以通过robomaster@birdiebot.top与我们取得联系。


# 许可证信息
Bubble参考和使用的其他项目您可以在[这里](https://birdiebot.github.io/bubble_documentation/resources/%E7%9B%B8%E5%85%B3%E9%A1%B9%E7%9B%AE.html)找到。

Bubble项目是根据GNU AGPL3.0许可证获得许可的。

上海工程技术大学学生科创中心机械创新基地木鸢birdiebot战队版权所有。
