## Check Source 
```bash
cat .bashrc
```
## INSTALL PACKAGES
```bash
sudo apt update
sudo apt install ros-humble-navigation2 ros-humble-nav2-bringup ros-humble-turtlebot3*
```
## add the command to bash file 
```bash
gedit ~/.bashrc
export TURTLEBOT3_MODEL=waffle   #paste it in bash file
source .bashrc
```
## CHECK THE ENVIRONMENT
```bash
printenv | grep TURTLE
```
## TEST THE GAZEBO 
```bash
gazebo
```
## RUN THE TURTLE BOT IN GAZEBO 
```bash
ros2 launch turtlebot3_gazebo turtlebot3_world.launch.py
```
## to move the robot using keyboard
```bash
ros2 run turtlebot3_teleop teleop_keyboard
```
## to launch rviz 
```bash
ros2 launch turtlebot3_cartographer cartographer.launch.py use_sim_time:=True
```
Navigate the entire area using keyboard commands 

## Create a dir for maps 
```bash
mkdir maps
```
## TO GENERATE MAPS 
In the home dir run this command 
```bash
ros2 run nav2_map_server map_saver_cli -f maps/my_maps
```
## CHANGE THE DDS 

```bash
sudo apt update
sudo apt install ros-humble-rmw-cyclonedds-cpp
```
## add command to bash file 
```bash
export RMW_IMPLEMENTATION=rmw_cyclonedds_cpp
```
## Changes to files of turtlebo3 
```bash
cd /opt/ros//humble/share/turtlebot3_navigation2/param
```
Run this command 
```bash
sudo gedit waffle.yaml
```
NOW SEARCH FOR 
```bash
robot_model_type: "differential "
```
replace it with the following
```bash
robot_model_type: "nav2_amcl::DifferentialMotionModel"
```
## Reboot ur system now 

## RUN THE TURTLE BOT IN GAZEBO 
```bash
ros2 launch turtlebot3_gazebo turtlebot3_world.launch.py
```
## to move the robot using keyboard
```bash
ros2 run turtlebot3_teleop teleop_keyboard
```
## run the rviz 
```bash
ros2 launch turtlebot3_navigation2 navigation2.launch.py use_sim_time:=True maps:=maps/my_maps.yaml
```
## click on the 2d esitmation to estomate ur robot location 

## Click on nav2 goal and click on any part of the map it will move to that area 
