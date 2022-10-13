# Getting Started with ROS, Python, and TurtleSim

### Create the package
Navigate into `~/ros2_ws/src`

`cd ~/ros2_ws/src`

`ros2 pkg create turtle_sim_hw --build-type ament_python --dependencies rclpy `

### Navigate to ROS package script folder

`cd ~/ros2_ws/src/turtle_sim_hw/turtle_sim_hw`

### Get `script.py` file

Download `script.py` file

`wget https://raw.githubusercontent.com/htil/Getting-Started-with-ROS2-TurtleSim-and-Python/master/script.py`

Update `script.py` file permissions

`chmod +x script.py`

### Add dependencies

Add the following after the **license** declaration in the `~/ros2_ws/src/turtle_sim_hw/package.xml` file.

```
<exec_depend>rclpy</exec_depend>
<exec_depend>std_msgs</exec_depend>
```
 
Note: Remove `<depend>rclpy</exec_depend>` in the `package.xml` file.

### Add an entry point

Open the `~/ros2_ws/src/turtle_sim_hw/setup.py` file.

Add the following within the `console_script` brackets of the `entry_points` field:

```
entry_points={
        'console_scripts': [
            'start = turtle_sim_hw.script:main',
        ],
},
```

### Check `setup.cfg`

The contents of `setup.cfg` should look like the following.

```
[develop]
script_dir=$base/lib/turtle_sim_hw
[install]
install_scripts=$base/lib/turtle_sim_hw
```

### Build and run

Check for missing dependencies

`cd ~/ros2_ws/`

`rosdep install -i --from-path src --rosdistro humble -y`

Build new package while in `ros2_ws`

`colcon build --symlink-install --packages-select turtle_sim_hw`

**OPEN A NEW TERMINAL:** and run the command below while in `ros2_ws`:

Run the **turtlesim node**

`ros2 run turtlesim turtlesim_node`

**OPEN A NEW TERMINAL:** Run your ROS package.

`cd ~/ros2_ws/`

`. install/setup.bash`

`ros2 run turtle_sim_hw start`

### Check to see if the turtle is moving

<img src="https://github.com/htil/Getting-Started-with-ROS2-TurtleSim-and-Python/blob/master/turtlesim.png?raw=true"
     alt="Markdown Monster icon"
     style="width: 400px" />


### Get `run.sh` file

After editing the file you should be able to build and run your script using the `run.sh` file.

Navigate to `ros2_ws`

`cd ~/ros2_ws/`

Download run.sh file

`wget https://raw.githubusercontent.com/htil/Getting-Started-with-ROS2-TurtleSim-and-Python/master/run.sh`

Update `run.sh` file permissions

`chmod +x run.sh`

`./run.sh`
