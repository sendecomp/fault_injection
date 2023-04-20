# fault_injection_ros2
Ros injection tool that subscribes to a topic and makes chenges to it according to preset behavior

Setting up procedure

As it stands this tool works with ROS2 Humble, planned to port on ROS Noetic in near future. You need to have Carla 0.9.10.1 installed as well as newest version of Autoware-AI.

1. `mkdir -p ws/src` 
2. `cd ws/src`
We need to clone couple of packages in order to get everything to work. You can host them spearately or in one workspace
3. `git clone https://github.com/danilo-pejovic/fault_injection_ros2`
4. `git clone https://github.com/autowarefoundation/autoware_ai_simulation`
5. `git clone https://github.com/carla-simulator/carla-autoware.git`
6. `git clone https://github.com/carla-simulator/ros-bridge.git`
7. `cd ..`
8. `rosdep install --from-paths src --ignore-src -r -y`
9. `source /opt/ros/humble/setup.bash`
10. `MAKEFLAGS="-j1 -l1" colcon build`
11. `source install/setup.bash`

After that one of the launch files like: 
 
  `ros2 launch fault_injection_ros2 launch_robot.launch.py`

Should have mux enabled by default with hardcorded priorities. 

Known limitations: 

- Works only with untimestamped messages
- Produces bit of lag when taking a lot of data
- Has to be manually turned on and take messages
