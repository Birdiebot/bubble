<!--
 * @Author: Ligcox
 * @Date: 2022-05-23 20:12:11
 * @FilePath: /Bubble/README.md
 * @LastEditors: Ligcox
 * @LastEditTime: 2022-06-12 21:11:15
 * License: GNU General Public License v3.0. See LICENSE file in root directory.
 * Copyright (c) 2022 Birdiebot R&D Department
 * Shanghai University Of Engineering Science. All Rights Reserved
-->
# 概述
Bubble是一个上海工程技术大学学生科创中心机械创新基地木鸢birdiebot视觉算法开源框架。Bubble基于ROS2开发，框架提供了一系列RMU相关视觉算法相关任务。  

你可以通过algorithm@birdiebot.top与我们联系。


# 开始使用
## 构建的Bubble
```bash
sudo apt-get install python3-vcstool
mkdir src
vcs import src < Bubble.repos
colcon build --symlink-install
```
## 配置相关参数
```bahs
# As infantry example
# More detail see Bubble_bringup repo
# Modifying configuration file
gedit ./src/Bubble_bringup/config/infantry_param.yaml
gedit ./src/Bubble_bringup/launch/infantry_launch.py

# Run project
. install/setup.sh
ros2 launch Bubble_bringup infantry_launch.py
```

# 内容
Bubble的不同部分在不同的仓库中进行维护，你可以灵活的组合仓库中不同的功能包。功能包的详细说明可以参见仓库的readme文件或Bubble文档。
|仓库名称 | 地址| 说明|
|---|---| --- |
|Bubble_code| todo | 适用于RoboMaster竞赛上下位机通讯协议 |
|Bubble_camera|todo| 维护了不同相机的ROS包，其中main分支维护了普通usb相机，hikrobot_camera分支维护了海康机器人工业相机，gxusb_camera维护了大恒图像工业相机 |
|Bubble_interface|todo|框架功能包间消息类型定义|
|Bubble_detector|todo|视觉识别器，visual功能包使用传统视觉识别装甲板，visual_SJTU对上海交通大学哨兵自瞄系统二次开发，使用基于改进YOLOv5的神经网络识别装甲板，rune功能包识别RMUC2019-2022能量机关|
|Bubble_contrib|todo|实现了RoboMaster竞赛中的各项任务。aiming功能包维护了瞄准(自动瞄准及能量机关击打)相关内容，desion功能包使用有限状态机(FSM)控制机器人执行 |
|Bubble_resouces|todo|测试ROS BAG及项目中可能需要的资源文件|

# 关于我们
木鸢Birdiebot战队是上海工程技术大学教务处组织的校级学生科创团体，依托上海工程技术大学学生科创中心机械创新基地，以RoboMaster机甲大师赛为平台，致力于在机器人赛事、机器人生态、以及工程文化等多领域开展学生科创活动，培育中国智造卓越的青年工程师。
## 作者
框架设计 @ligcox  
能量机关、预测 @harrywen

## 联系我们
你可以通过github issues页面提出问题，，我们欢迎RoboMaster参赛队伍与我们开展线上与线下的各种交流活动，欢迎各个参赛队伍通过robomaster@birdiebot.top与我们取得联系。



## 许可证
这个项目是根据GNU3.0许可证获得许可的。
版权所有上海工程技术大学学生科创中心机械创新基地木鸢birdiebot战队