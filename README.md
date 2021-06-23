# AI_TurtleBot3_task2
This repository is for task 2 of the AI track of my summer training at Smart-Methods

In this repository, I will be going through these main topics to be able to controll and move the TURTLEBOT3_MODEL=waffle_pi (or "burger" or "waffle") simulation in Rviz and Gazebo simultaneously using : "W  A  S  D  X" here is the offical link of TurtleBot3 "https://emanual.robotis.com/docs/en/platform/turtlebot3/quick-start/#pc-setup": 

- Install Dependent ROS 1 Packages ( make sure to match your ROS edition, MINE IS MELODIC)
- Install TurtleBot3 Packages
- Set TurtleBot3 Model Name (waffle_pi / burger / waffle)
- Install Gazebo Simulation Package
- Launch Simulation World (waffle_pi / burger / waffle)
- Operate TurtleBot3
- Launch Simulation World
- Run SLAM Node
- Run Teleoperation Node
- Save Map

---------------------------------------------------------------------------------------------
# Basic setup ( make sure you already have ROS and Ubuntu 18.04 installed and running)
Install Dependent ROS 1 Packages:

    $ sudo apt-get install ros-melodic-joy ros-melodic-teleop-twist-joy \
    ros-melodic-teleop-twist-keyboard ros-melodic-laser-proc \
    ros-melodic-rgbd-launch ros-melodic-depthimage-to-laserscan \
    ros-melodic-rosserial-arduino ros-melodic-rosserial-python \
    ros-melodic-rosserial-server ros-melodic-rosserial-client \
    ros-melodic-rosserial-msgs ros-melodic-amcl ros-melodic-map-server \
    ros-melodic-move-base ros-melodic-urdf ros-melodic-xacro \
    ros-melodic-compressed-image-transport ros-melodic-rqt* \
    ros-melodic-gmapping ros-melodic-navigation ros-melodic-interactive-markers

Install TurtleBot3 Packages:

    $ sudo apt-get install ros-melodic-dynamixel-sdk
    $ sudo apt-get install ros-melodic-turtlebot3-msgs
    $ sudo apt-get install ros-melodic-turtlebot3

Set TurtleBot3 Model Name (waffle_pi):

    $ echo "export TURTLEBOT3_MODEL=waffle_pi" >> ~/.bashrc

-----------------------------------------------------------
# Gazebo

Install Simulation Package: 

    $ cd ~/catkin_ws/src/
    $ git clone -b melodic-devel https://github.com/ROBOTIS-GIT/turtlebot3_simulations.git
    $ cd ~/catkin_ws && catkin_make

Launch Simulation World (waffle_pi):

    Open a new terminal:

       $ export TURTLEBOT3_MODEL=waffle_pi
       $ roslaunch turtlebot3_gazebo turtlebot3_world.launch

Operate TurtleBot3:

    $ roslaunch turtlebot3_teleop turtlebot3_teleop_key.launch

![weiam Gazebo tb3](https://user-images.githubusercontent.com/63375443/123156753-53aae100-d472-11eb-8cad-1c516b567791.png)

------------------------------------------------------------------------------------------
# SLAM

Launch Simulation World:

	Open a new terminal:
  
     $ export TURTLEBOT3_MODEL=waffle_pi
     $ roslaunch turtlebot3_gazebo turtlebot3_world.launch

Run SLAM Node:

    Open a new terminal:
    
       $ export TURTLEBOT3_MODEL=waffle_pi
       $ roslaunch turtlebot3_slam turtlebot3_slam.launch slam_methods:=gmapping

Run Teleoperation Node:

    Open a new terminal:
    
       $ export TURTLEBOT3_MODEL=waffle_pi
       $ roslaunch turtlebot3_teleop turtlebot3_teleop_key.launch
       
       
![weiam Teleoperation](https://user-images.githubusercontent.com/63375443/123156502-0b8bbe80-d472-11eb-8650-3bc311b03831.png)

![weiam TB3](https://user-images.githubusercontent.com/63375443/123156333-d5e6d580-d471-11eb-85e0-2c0476ea5348.png)


# Save Map:

    Open a new terminal
       $ rosrun map_server map_saver -f ~/map
       
![weiam MAP](https://user-images.githubusercontent.com/63375443/123156070-8a342c00-d471-11eb-95a7-8f04b90ebbc2.png)
