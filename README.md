# setup_and_launch
This repo will contain launch and configuration files for launching the class simulators.

# Installing ROS
To begin, install the version of ROS supported by your version of Ubuntu. Currently Ubuntu 16.04 uses ROS Kinetic and 18.04 uses ROS Melodic.

[ROS Melodic Install Instructions](http://wiki.ros.org/melodic/Installation/Ubuntu)

[ROS Kinetic Install Instructions](http://wiki.ros.org/kinetic/Installation/Ubuntu)

# Required packages
The sim requires the install of a variety of pre-build ros packages. This can be done by running:

**ROS Melodic**

`sudo apt install ros-melodic-amcl ros-melodic-map-server ros-melodic-gmapping ros-melodic-navigation`

**ROS Kinetic**

`sudo apt install ros-kinetic-amcl ros-kinetic-map-server ros-kinetic-gmapping ros-kinetic-navigation`

# Installing Google Test
Google Test is a unit testing framework required for the packages within the .rosinstall files. Google Test is included with the full desktop installation of ROS. If you have already installed ROS follow the steps below to setup Google Test.

```console
sudo apt-get install cmake libgtest-dev
cd /usr/src/gtest
sudo cmake CMakeLists.txt
sudo make
sudo cp *.a /usr/lib
```

# Launching the sim
Prior to launching the sim, you must export the turtlebot3 model:

`export TURTLEBOT3_MODEL='waffle'`

To run a launch file, execute the following command

`roslaunch turtlebot_launch <desired launch file>.launch`

There are two launch we have been using:
*  turtlebot3_fakenode.launch: Runs a robot capable of being teleoperated without Gazebo
*  turtlebot3_gazebo.launch: Runs a robot with sensor feedback from the Gazebo simulator

Project 2 has two launch files you should look at:
*  proj2.launch: Launches the turtlebot running with a simple unicycle model
*  proj2_quad.launch: Launches a quadrotor running with a simple unicycle model

Project 3 has four launch files to consider
*  "proj3.launch": This is the default launch file
    *  Upon launch, you can control the robot using the RVIZ "2D Nav Goal" at the top of the RVIZ window
*  "proj3_randGoal.launch": This code executes a random goal. Once the goal is achieved, then another random goal is generated.
*  "multi_g2g.launch": This is very similar to the "proj3_randGoal.launch", but now multiple robots are going to random goals
*  "multi_topology.launch": This has the robots move randomly over a graph topology.

# Installing Gazebo
To run the launch files, you must first install Gazebo

**ROS Melodic**

`sudo apt install ros-melodic-gazebo-ros`

`sudo apt install ros-melodic-gazebo-ros-control`

`sudo apt install ros-melodic-gazebo-ros-pkgs`


**ROS Kinetic**

`sudo apt install ros-kinetic-gazebo-ros`

`sudo apt install ros-kinetic-gazebo-ros-control`

`sudo apt install ros-kinetic-gazebo-ros-pkgs`

# Using the joystick
The proj2.launch and proje2_quad.launch have options for using a joystick to control the robot. To use the joystick, set the following in the launch file: 

`<arg name="run_joystick" default="true"/>`

The left joystick on a logitech game pad will then run. This joystick control depends on the ros joy package. You must install the joy package (for joystick drivers)

kinetic:

`sudo apt install ros-kinetic-ros-tutorials`

`sudo apt install ros-kinetic-joy`

melodic:

`sudo apt install ros-melodic-ros-tutorials`

`sudo apt install ros-melodic-joy`

# Setting up your joystick controller
See [http://wiki.ros.org/joy](http://wiki.ros.org/joy) to setup the joystick drivers correctly.