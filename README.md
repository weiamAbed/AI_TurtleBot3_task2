# AI_TurtleBot3_task2
This repository is for task 2 of the AI track of my summer training at Smart-Methods

In this repository, I will be going through these main topics to be able to controll TURTLEBOT3_MODEL=waffle_pi ( or "burger" or "waffle" ) simulation in Rviz and Gazebo simultaneously using : "W  A  S  D  X

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

# Save Map:

    Open a new terminal
       $ rosrun map_server map_saver -f ~/map
