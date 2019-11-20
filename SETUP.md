# Setup instructions #


create workspace folder
~/reactor_ws
and also src folder
~/reactor_ws/src

using catkin build command (available from sudo apt-get install python-catkin-tools)

source /opt/ros/kinetic/setup.bash
catkin build

sudo apt-get install ros-kinetic-dynamixel-controllers ros-kinetic-arbotix

git clone https://github.com/RobotnikAutomation/phantomx_reactor_arm.git
(or clone the updated fork https://github.com/NoamKu/phantomx_reactor_arm.git

catkin build


sudo cp src/phantomx_reactor_arm/phantomx_reactor_arm_controller/config/57-reactor_arbotix.rules /etc/udev/rules.d

dmesg | grep tty

[    0.000000] console [tty0] enabled
[ 2421.758251] usb 1-2: FTDI USB Serial Device converter now attached to ttyUSB0

 udevadm info -a -n /dev/ttyUSB0 | grep serial
    SUBSYSTEMS=="usb-serial"
    ATTRS{serial}=="AK06SUBE"
    ATTRS{serial}=="0000:00:14.0"

sudo gedit /etc/udev/rules.d/57-reactor_arbotix.rules

change ATTRS{serial}=="******" to fit the code you got from udevadm command output

Once modified you have to reload and restart the udev daemon

sudo service udev reload
sudo service udev restart
sudo udevadm trigger

source devel/setup.bash

For the arm with wrist

roslaunch phantomx_reactor_arm_controller arbotix_phantomx_reactor_arm_wrist.launch

**Troubleshooting**

if rviz is not displaying the robot, in global options change fixed frame to base footprint


