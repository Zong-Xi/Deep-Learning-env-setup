# Openai_ros example in local computer
-----------

<br>

install `openai_ros` and try [tutorial 1](<http://wiki.ros.org/openai_ros/TurtleBot2%20with%20openai_ros>) and [tutorial 2](http://wiki.ros.org/openai_ros/Wam-V%20RobotX%20Challenge%20with%20openai_ros), not using ROS Development Studio(RDS)

<br>

[Tutorial1](#tutorial1) <br>
[Tutorial2](#tutorial2) <br>
[Problem](#problem) 

<br>

# Tutorial1
Q learning on Turtlebot2 simulation
### 1. Download [Turtlebot2Maze](https://bitbucket.org/theconstructcore/turtlebot/src/master/) pkg, and set branch
```
cd ~/catkin_ws/src
git clone https://bitbucket.org/theconstructcore/turtlebot.git
cd ~/catkin_ws/src/turtle
git fetch && git checkout kinetic
cd ~/catkin_ws
catkin_make
source devel/setup.bash
```

### 2. Download [openai_ros](https://bitbucket.org/theconstructcore/openai_ros/src/kinetic-devel/) pkg, and set branch
```
cd ~/catkin_ws/src
git clone https://bitbucket.org/theconstructcore/openai_ros.git
cd ~/catkin_ws/src/openai_ros
git fetch && git checkout kinetic-devel
cd ~/catkin_ws
catkin_make
source devel/setup.bash
```

### 3. Download [openai_examples_projects](https://bitbucket.org/theconstructcore/openai_examples_projects/src/master/) pkg, and set branch
```
cd ~/catkin_ws/src
git clone https://bitbucket.org/theconstructcore/openai_examples_projects.git
cd ~/catkin_ws/src/openai_examples_projects
git fetch && git checkout tutorials
cd ~/catkin_ws
catkin_make
source devel/setup.bash
```

### 4. Download [open_ai_gym_construct](https://bitbucket.org/theconstructcore/open_ai_gym_construct/src/master/) pkg, and set branch
```
cd ~/catkin_ws/src
git clone https://bitbucket.org/theconstructcore/open_ai_gym_construct.git
cd ~/catkin_ws/src/open_ai_gym_construct
git fetch && git checkout master
cd ~/catkin_ws
catkin_make
source devel/setup.bash
```

### 5. Launch gym_constructure main.launch file in command terminal
```
roslaunch gym_construct main.launch
roslaunch turtle2_ros_example start_training.launch
```

<br>

# Tutorial2
Q learning on Wam-V RobotX
### 1. Download [WAMV_Simulation](https://bitbucket.org/theconstructcore/vmrc/src/master/)
in simulation_ws:
```
cd ~/simulation_ws/src
git clone https://bitbucket.org/theconstructcore/vmrc.git
cd ~/simulation_ws
catkin_make
```

### 2. Download [spawn_robot_tools](https://bitbucket.org/theconstructcore/spawn_robot_tools/src/master/)
in simulation_ws:
```
cd ~/simulation_ws/src
git clone https://bitbucket.org/theconstructcore/spawn_robot_tools.git
cd ~/simulation_ws
catkin_make
```

### 3. Download [openai_ros](https://bitbucket.org/theconstructcore/openai_ros/src/kinetic-devel/) pkg, and set branch
```
cd ~/catkin_ws/src
git clone https://bitbucket.org/theconstructcore/openai_ros.git
cd ~/catkin_ws/src/openai_ros
git fetch && git checkout kinetic-devel
cd ~/catkin_ws
catkin_make
source devel/setup.bash
```

### 4. Download [openai_examples_projects](https://bitbucket.org/theconstructcore/openai_examples_projects/src/master/) pkg, and set branch
```
cd ~/catkin_ws/src
git clone https://bitbucket.org/theconstructcore/openai_examples_projects.git
cd ~/catkin_ws/src/openai_examples_projects
git fetch && git checkout tutorials
cd ~/catkin_ws
catkin_make
source devel/setup.bash
```

### 5. Start training
```
roslaunch robotx_gazebo sandisland.launch
roslaunch wamv_openai_ros_example start_training.launch
```


# Problem
the turtlebot is training, and can see the loss and episode in terminal, but the gazebo simulation has not be loaded
```
 [ INFO] [1537961641.295151763, 0.348000000]: DiffDrive(ns = //): Advertise joint_states
 [ INFO] [1537961641.295818023, 0.348000000]: DiffDrive(ns = //): Try to subscribe to cmd_vel
 [ INFO] [1537961641.298928159, 0.348000000]: DiffDrive(ns = //): Subscribe to cmd_vel
 [ INFO] [1537961641.299555014, 0.348000000]: DiffDrive(ns = //): Advertise odom on odom 
 [spawn_turtlebot_model-2] process has finished cleanly
 log file: /home/parkbj/.ros/log/043fb95e-c180-11e8-8ab1-7085c22a655c/spawn_turtlebot_model-2*.log
```

<br>

## Solve
There are no issues here, all the requested nodes with their parameters are correctly launched (and it's normal that the `spawn_turtlebot_model` process end once launched in case you were wondering).

"Nothing happen" because you don't launch the Gazebo GUI (ie. `gzclient`), in your nodes you simply have `gzserver`. Look at your `main.launch` :
```launch
  <arg name="paused" value="true"/>
  <arg name="gui" default="false"/>
  <arg name="headless" value="true"/>
  <arg name="stacks"    value="$(optenv TURTLEBOT_STACKS hexagons)"/>  <!-- circles, hexagons --> 
  <arg name="3d_sensor" value="$(optenv TURTLEBOT_3D_SENSOR kinect)"/>  <!-- kinect, asus_xtion_pro --> 

  <include file="$(find gazebo_ros)/launch/empty_world.launch">
    <arg name="use_sim_time" value="true"/>
    <arg name="debug" value="false"/>
    <arg name="gui" value="$(arg gui)" />
    <arg name="world_name" value="$(find gym_construct)/worlds/maze_loop_brick.world"/>
  </include>
  ```

  If you change `<arg name="gui" default="false"/>` to `<arg name="gui" default="true"/>` everything should be fine.

Or if you don't want to modify the launch file, you can also run :
```
roslaunch gym_construct main.launch gui:=true
```
In addition : you have `<arg name="paused" value="true"/>`, eventhough you don't use the arg its default value is false (if you have to use it and it's set to true Gazebo will be started on a paused state)

## Reference
ROS Answer:
- [openai_ros example in local computer does not work](https://answers.ros.org/question/304330/openai_ros-example-in-local-computer-does-not-work/)
