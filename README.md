<!--
 * @Author: Ligcox
 * @Date: 2022-05-23 20:12:11
 * @FilePath: /bubble/README.md
 * @LastEditors: Ligcox
 * @LastEditTime: 2022-08-20 21:28:19
 * License: GNU General Public License v3.0. See LICENSE file in root directory.
 * Copyright (c) 2022 Birdiebot R&D Department
 * Shanghai University Of Engineering Science. All Rights Reserved
-->

English | [简体中文](.github/README_zhCN.md)

Bubble is an open source framework for the visual algorithm of Wood Kite Birdiebot, a mechanical innovation base of Shanghai University of Engineering Science and Technology Student Science Innovation Center. Bubble is developed based on ROS2, and the framework provides a series of tasks related to RMU related visual algorithms.



You can contact us at algorithm@birdiebot.top.


# Getting start
## build Bubble
```bash
sudo apt-get install python3-vcstool
mkdir src
vcs import src < bubble.repos
colcon build --symlink-install
```
## Parameter Configuration

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

# Why Bubble
Different parts of the Bubble are maintained in different warehouses, so you have the flexibility to combine different feature packs in the warehouse. A detailed description of the feature pack can be found in the repository's ReadMe file or Bubble documentation.

 
# About us
Birdiebot is a school-level science and technology innovation team organized by the office of Academic Affairs in Shanghai University of Engineering Science. With the support of the Mechanics Innovation Base under Student Science and Technology Innovation Center, Birdiebot is committed to carry out science and technology innovation activities in robot competitions, robot ecology, engineering culture and other fields. To cultivate young, outstanding engineers for China’s intelligent manufacturing industry.

## Contact
For Bubble bugs and feature requests please visit the Github Issues page. RoboMaster teams are welcome to communicate with us online and offline. Teams are welcome to contact us at robomaster@birdiebot.top.



## license

This project is licensed under the GNU3.0 license.

Copyright 2021 Shanghai University of Engineering Science and Technology Student Science and Technology Center Mechanical Innovation Base Muyuan Birdiebot Team
