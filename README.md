# ROS_sensors
# 1 Velodyne VLP16 Lidar
## 1.1 Installing ROS dependencies

```sudo apt-get install ros-noetic-velodyne```

## 1.2 Installing the VLP16 driver
```
mkdir -p ~/ros_sensors/src
cd ros_sensors/src
git clone https://github.com/ros-drivers/velodyne.git
sudo apt update
sudo apt upgrade
cd ..
catkin_make
```
Now, your Velodyne package is ready to run.

## 1.3 Communicate with the Velodyne sensor
1. Power the LIDAR via the included adapter.
2. Connect the LIDAR to an Ethernet port on your computer.
3. For now, disable the WiFi connection on your computer.
4. Go to settings, open Networks then click on wired Networks -> IPv4
5. Select Manual and  Set the address: ```192.168.1.202```
6. Netmask: ```255.255.255.0```
7. Gateway: ```0.0.0.0``` and click on apply.

## 1.4 Run the package
1. Run the launch file:
```
roslaunch velodyne_pointcloud VLP16_points.launch
```
2. Launch RVIZ
```
rosrun rviz rviz -f velodyne
```

# 2 Flir Camera
