# Robotiq

## Status

As of 2021-05-28, it would appear this repository is ***unmaintained***.

Robotiq is not maintaining the packages in this repository and the last active maintainer ([jproberge](https://github.com/jproberge)) does not appear to be active any more.

The ROS-Industrial consortia are not involved: for historical reasons, the `robotiq` repository is hosted on the `ros-industrial` Github organisation, but there is no direct link with any of the other repositories there.

Please direct support requests to [dof.robotiq.com](https://dof.robotiq.com/). The tracker here is not monitored by Robotiq employees.


## ROS Distro Support

|         | Indigo | Jade | Kinetic | Melodic |
|:-------:|:------:|:----:|:-------:|:-------:|
| Branch  | [`indigo-devel`](https://github.com/ros-industrial/robotiq/tree/indigo-devel) | [`jade-devel`](https://github.com/ros-industrial/robotiq/tree/jade-devel) | [`kinetic-devel`](https://github.com/ros-industrial/robotiq/tree/kinetic-devel) | [`kinetic-devel`](https://github.com/ros-industrial/robotiq/tree/kinetic-devel) |)
| Status  |  supported | not supported |  supported |  supported |
| Version | [version](http://repositories.ros.org/status_page/ros_indigo_default.html?q=robotiq) | [version](http://repositories.ros.org/status_page/ros_jade_default.html?q=robotiq) | [version](http://repositories.ros.org/status_page/ros_kinetic_default.html?q=robotiq) | [version](http://repositories.ros.org/status_page/ros_melodic_default.html?q=robotiq) |

## Travis - Continuous Integration

Status: [![Build Status](https://travis-ci.com/ros-industrial/robotiq.svg?branch=kinetic-devel)](https://travis-ci.com/ros-industrial/robotiq)

## ROS Buildfarm

There are no up-to-date releases of these packages available from the ROS buildfarm.

[![support level: community](https://img.shields.io/badge/support%20level-community-lightgray.svg)](http://rosindustrial.org/news/2016/10/7/better-supporting-a-growing-ros-industrial-software-platform)

Robotiq meta-package.  See the [ROS wiki][] page for more information. 

## License

[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)
[![License](https://img.shields.io/badge/License-BSD%203--Clause-blue.svg)](https://opensource.org/licenses/BSD-3-Clause)

## Contents

This repo holds source code for all versions > groovy. For those versions <= groovy see: [SVN repo][]

[ROS wiki]: http://ros.org/wiki/robotiq
[SVN repo]: https://code.google.com/p/swri-ros-pkg/source/browse
## For xacro debug
`check_urdf <(xacro robotiq_hand.xacro)`
## Usage
1. Install the Robotiq ros services control pkg:
    ```bash
    cd workspace/src

    git clone https://github.com/davidmartinez13/robotiq_3f_ros_pkg.git

    cd ..

    catkin build robotiq_3f_ros_pkg
    ```
2. To spawn the robotiq dummy gripper in gazebo run: 

    ```bash
    roslaunch robotiq_3f_gripper_articulated_gazebo robotiq_gripper_empty_world.launch
    ```
- To spawn the robotiq gripper in gazebo run: 

    ```bash
    roslaunch robotiq_3f_gripper_articulated_gazebo robotiq_gripper_empty_world_macro.launch
    ```

    - Test the control with the provided python script:
        ```bash
        cd /robotiq/robotiq_3f_gripper_control/nodes/

        python2 Robotiq3FGripperSimpleController.py
        ```
        - The following commands are available from the python script:
    
            r: Reset

            a: Activate

            c: Close

            o: Open

            b: Basic mode

            p: Pinch mode

            w: Wide mode

            s: Scissor mode

            (0-255): Go to that position

            f: Faster

            l: Slower

            i: Increase force

            d: Decrease force
    - Or, control the gripper with ros services:
        
        - If in sim, then launch the listener for sim:
            ```
            roslaunch robotiq_3f_driver listener_sim.launch
            ```
        - If not on sim, launch the listener:
            ```
            roslaunch robotiq_3f_driver listener.launch ip_address:=192.168.1.11
            ```
            Both ways the ROS services and gripper will be activated.\
            Try sending some commands as:

            ```
            rosservice call /robotiq_3f_gripper/activate
            rosservice call /robotiq_3f_gripper/set_mode wide
            rosservice call /robotiq_3f_gripper/set_position 200
            rosservice call /robotiq_3f_gripper/set_position 150
            rosservice call /robotiq_3f_gripper/set_position 0
            ```
3. to spawn robotiq3f moveit with franka panda (not yet fully implemented):\
    ```bash
    roslaunch robotiq_3f_rviz_moveit_panda panda_robotiq3f_moveit.launch
    ```