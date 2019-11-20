In one terminal:

cd ~/reacor_ws/
(only if some code changed do catkin build)
roscore 


In second terminal:

Operate robotic arm when everything is working

cd reactor_ws/
source devel/setup.bash

check for servo engines (8 of them should be printed)
rosrun arbotix_python arbotix_terminal
type ls

if not! Try to harden the connector downstares on the arbotix board

roslaunch turtlebot_arm_moveit_config demo.launch

if you want to use python code
open third terminal:

cd reactor_ws/
source devel/setup.bash
rosrun phantomx_reactor_arm_moveit_demos pick_and_place.py

