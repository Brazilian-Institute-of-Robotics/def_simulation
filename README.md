# def_simulation
Package to simulate the robot model in Gazebo. Used to validate the motion planning made by MoveIt! and the visual detection of the apriltag.

# Installation
Clone the repositories ```def_moveit``` and ```def_apriltag``` into your catkin_workspace. Also, Gazebo needs to be installed on your machine. 

# Robot model
The package uses ```.stl``` files located in the ```/meshes```folder to create a model of the robot. The arrangement of these single robot parts is defined in ```/urdf/dynamic-ef.urdf.xacro```. To control the robot in the simulation, a ros_control_plugin is added in ```/urdf/dynamic-ef.gazebo```. The controllers specified in ```config/def_controllers.yaml``` will interact with MoveIt!, so the names must match the names in ```def_moveit```. A camera plugin is also implemented in ```dynamic-ef.gazebo``` to get a video stream from the simulated camera. This is used to detect the apriltags in the simulation.

# Launch it!
- You can just display the .urdf robot model in rviz with ```display.launch```. Usually used to verify changes of the urdf
- To start gazebo use ```dyn_ef_robot_bringup_gazebo.launch```. This will launch a world with an apriltag. Changes on this world can be made in ```/models/our_world.world```.

# notes
- the transmission_interface in the .urdf.xacro file (in /urdf) must be of the same type as the ```dyn_ef_robot_controller``` in  ```config/def_controllers.yaml```. In this case its velocity
