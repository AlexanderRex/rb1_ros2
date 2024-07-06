
# RB1 ROS2 Description Package

## Introduction
Welcome to the `rb1_ros2_description` package. This ROS2 package provides a detailed robot model description for Robotnik's RB-1 mobile base.

## Installation Instructions

### Installing the Package
Clone this package into the `src` folder of your ROS2 workspace:
```bash
git clone https://github.com/AlexanderRex/rb1_ros2.git
```
Navigate to your ROS2 workspace and build the package:
```bash
cd ros2_ws
colcon build --packages-select rb1_ros2_description
```
Don’t forget to source your workspace:
```bash
source install/setup.bash
```

## Getting Started
To launch the simulation, use the following command:
```bash
ros2 launch rb1_ros2_description rb1_ros2_xacro.launch.py
```
## Teleoperation usng ros2 control diff_drive

The ROS2 Control command line tools display the correct controllers to be active and the hardware interfaces to be claimed.

Use this command to check avaliable interfaces
```bash
ros2 control list_hardware_interfaces
```
Use this command to check avaliable controllers
```bash
ros2 control list_controllers
```
To test drive controller use this command

```
ros2 topic pub --rate 10 /diffbot_base_controller/cmd_vel_unstamped geometry_msgs/msg/Twist "{linear: {x: 0.0, y: 0, z: 0.0}, angular: {x0.0,y: 0.0, z: 0.2}}"
```

## Moving the Robot's Lifting Unit
To operate the robot's lifting unit, publish commands to the appropriate topics:

Lift the platform:
```bash
ros2 topic pub /position_controller/commands std_msgs/msg/Float64MultiArray "{data: [0.03]}" -1
```
Lower the platform:
```bash
ros2 topic pub /position_controller/commands std_msgs/msg/Float64MultiArray "{data: [0.0]}" -1
```
