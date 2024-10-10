## Check Source 
```bash
cat .bashrc
```
## Install Packages
```bash
sudo apt update
sudo apt install ros-humble-navigation2 ros-humble-nav2-bringup ros-humble-turtlebot3*
```
## Add Command to Bash File 
```bash
gedit ~/.bashrc
export TURTLEBOT3_MODEL=waffle   # Paste this line into the .bashrc file
source ~/.bashrc

```
## Check the Environment
```bash
printenv | grep TURTLE
```
## Test Gazebo 
Launch Gazebo:
```bash
gazebo
```
## Run the TurtleBot in Gazebo 

Launch the TurtleBot in a Gazebo world:
```bash
ros2 launch turtlebot3_gazebo turtlebot3_world.launch.py
```
## Move the Robot Using Keyboard
Use the following command to control the robot:
```bash
ros2 run turtlebot3_teleop teleop_keyboard
```
## Launch RViz
To visualize the robot in RViz:
```bash
ros2 launch turtlebot3_cartographer cartographer.launch.py use_sim_time:=True
```
Navigate the entire area using keyboard commands 

## Create a Directory for Maps
Make a directory for saving maps:
```bash
mkdir maps
```
## To Generate Maps
In your home directory, run the following command to save the map:
```bash
ros2 run nav2_map_server map_saver_cli -f maps/my_maps
```
## Change the DDS
Install Cyclone DDS:


```bash
sudo apt update
sudo apt install ros-humble-rmw-cyclonedds-cpp
```
## Add Command to Bash File
 Add the following line to your .bashrc file:

```bash
export RMW_IMPLEMENTATION=rmw_cyclonedds_cpp
```
## Changes to TurtleBot3 Files
Navigate to the parameter files:

```bash
cd /opt/ros//humble/share/turtlebot3_navigation2/param
```
Edit the waffle.yaml file:
```bash
sudo gedit waffle.yaml
```
Search for:
```bash
robot_model_type: "differential "
```
Replace it with:

```bash
robot_model_type: "nav2_amcl::DifferentialMotionModel"
```
## Reboot Your System
Reboot your system to apply the changes.



## Run the TurtleBot in Gazebo
Launch the TurtleBot again:


```bash
ros2 launch turtlebot3_gazebo turtlebot3_world.launch.py
```

## Run RViz
Launch RViz:


```bash
ros2 launch turtlebot3_navigation2 navigation2.launch.py use_sim_time:=True maps:=maps/my_maps.yaml
```
## Estimate Robot Location
In RViz, click on "2D Pose Estimate" to estimate the robot's location.



## Set Navigation Goal
Click on "Nav2 Goal" and select any point on the map; the robot will move to that area.


