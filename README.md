# livox_laser_simulation for ROS2
This is a ros2 port of the original repo: https://github.com/Livox-SDK/livox_laser_simulation.

Tested in ros2 foxy and humble.

In this simulation project, Livox series lidars will  publish two types of messages: 
> livox_ros_driver2/msg/CustomMsg </br>
> sensor_msgs/msg/PointCloud2

Therefore, by subscribing to the `CustomMsg` message, you can use the FAST_LIO algorithm in the your simulation.

![poincloud2](docs/poincloud2.png)

# Install
1. Clone this repo in your ros2 workspace

    ```
    git clone https://github.com/LihanChen2004/livox_laser_simulation_ros2.git
    ```

2. Follow [livox_ros_driver2 Installation](https://github.com/Livox-SDK/livox_ros_driver2)

3. build your ros2 workspace (if there are warnings that do not allow the compilation, run the build again and you will see that the error disappears)

    ```
    colcon build && source install/setup.bash
    ```

# Usage
1. include the lidar sensor in your URDF file, for example:

    ```
    <xacro:include filename="$(find ros2_livox_simulation)/urdf/mid70.xacro" />
    ```


2. attach the sensor to your robot in the URDF (or xacro) file, for example:

    ```
      <xacro:mid70 name="livox" parent="base_link" topic="mid70">
        <origin xyz="0 0 0.025" rpy="0 0 0"/>
      </xacro:mid70>
    ```

    you need to specify the parent link (usually base_link)

    that's it. the example that i gave you is for mid70, but you can use mid40, mid70, mid360 and so on.

    thanks to the original repo, you can find more info in it.

# Example

- [PB_RMSimulation](https://github.com/LihanChen2004/PB_RMSimulation)

    ROS2-Gazebo simulation package for RoboMaster University Championship

    You can use FAST_LIO by taking it as an example :)
    
    ![fastlio_pointcloud](docs/fastlio_pointcloud.png)


