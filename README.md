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
- To spawn the robotiq dummy gripper in gazebo run: 

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