# Gazebo model path example

This package shows how to use tags in the package.xml to avoid a race condition that occurs when trying to spawn both a table and a robot on top of it.
The motivation is to share mesh/urdf resources with gazebo and rviz.

```
. /opt/ros/<rosdistro>/setup.bash
. /usr/share/gazebo/setup.sh
mkdir -p catkin_ws/src
cd catkin_ws/src
git clone https://github.com/sloretz/gazebo_model_path_example.git
cd ..
catkin build
. devel/setup.bash
roslaunch gazebo_model_path_example granite.launch
```

The granite table is defined as a urdf.
A `model.config` for the granite table tricks sdformat into converting the URDF to SDF.
The package.xml includes `<gazebo_ros gazebo_model_path=""/>` to add the path to the table model as a place to search for gazebo models.
The tag `<gazebo_ros gazebo_media_path=""/>` Adds places to search for meshes and worlds.
There are no meshes in this example, but it would be trivial to add them.
`table.world` includes the table model by name which guarantees that the table will be loaded before the robot model is spawned on top of it.


These paths are are parsed by the system plugin [gazebo\_ros\_paths\_plugin](https://github.com/ros-simulation/gazebo_ros_pkgs/blob/kinetic-devel/gazebo_ros/src/gazebo_ros_paths_plugin.cpp) provided by `gazebo_ros_pkgs`.
