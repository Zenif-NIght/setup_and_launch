# setup_and_launch
This repo will contain launch and configuration files for launching the class simulators.

# Installing ROS
To begin, install the version of ROS supported by your version of Ubuntu. Currently Ubuntu 16.04 uses ROS Kinetic and 18.04 uses ROS Melodic.

[ROS Kinetic Install Instructions](http://wiki.ros.org/kinetic/Installation/Ubuntu)

[ROS Melodic Install Instructions](http://wiki.ros.org/melodic/Installation/Ubuntu)

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
# Installing Gazebo
To run the launch files, you must first install Gazebo

**ROS Melodic**

`sudo apt install ros-melodic-gazebo-ros ros-melodic-gazebo-ros-control ros-melodic-gazebo-ros-pkgs`

**ROS Kinetic**

`sudo apt install ros-kinetic-gazebo-ros ros-kinetic-gazebo-ros-control ros-kinetic-gazebo-ros-pkgs`

# Installing NLopt

[NLopt install instructions](https://nlopt.readthedocs.io/en/latest/#download-and-installation)

# Launching the sim
Prior to launching the sim, you must export the turtlebot3 model:

`export TURTLEBOT3_MODEL='waffle'`

To run a launch file, execute the following command

`roslaunch turtlebot_launch <desired launch file>.launch`

There are several launch files illustrating fundamentals. The first two present simple simulations:
* turtlebot3_gazebo.launch: Runs a robot with sensor feedback from the Gazebo simulator
  * slam_methods: allows one to change which slam library is called
* teleop.launch: Runs a robot that can be teleoperated from 
  * run_joystick: switch between joystick and keyboard teleoperation
  * spawn_gazebo: switches the physics engine from a basic sim to one run by Gazebo
  * use_turtlebot_viz: switches between a turtlebot visualization and a quadrotor visualization
* go_to_goal.launch: Runs a go-to-goal node which allows 2D goal to be specified by RVIZ
  * run_joystick: switches between joystick mode and go-to-goal mode
  * spawn_gazebo: switches the physics engine from a basic sim to one run by Gazebo
  * dynamics_model: allows switch between different dynamic models (unicycle and jerk)
  * Variations on go-to-goal 
     * go_to_random_goal.launch: Runs go_to_goal.launch with an additional node for creating a random goal
     * multi_g2g.launch: Runs multiple versions of go_to_random_goal.launch, having multiple vehicles
     *  multi_topology.launch: An additional node added to have each robot move over a random topology graph

# Using the joystick
The proj2.launch and proje2_quad.launch have options for using a joystick to control the robot. To use the joystick, set the following in the launch file: 

`<arg name="run_joystick" default="true"/>`

The left joystick on a logitech game pad will then run. This joystick control depends on the ros joy package. You must install the joy package (for joystick drivers)

**ROS Melodic**

`sudo apt install ros-melodic-ros-tutorials`

`sudo apt install ros-melodic-joy`

**ROS Kinetic**

`sudo apt install ros-kinetic-ros-tutorials`

`sudo apt install ros-kinetic-joy`

# Setting up your joystick controller
See [http://wiki.ros.org/joy](http://wiki.ros.org/joy) to setup the joystick drivers correctly.
