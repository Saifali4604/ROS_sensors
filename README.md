# ROS_sensors
# 1. Velodyne VLP16 Lidar
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
source devel/setup.bash
```
Now, your Velodyne package is ready to run.

## 1.3 Communicate with the Velodyne sensor
1. Power the LIDAR via the included adapter.
2. Connect the LIDAR to an Ethernet port on your computer.
3. For now, disable the WiFi connection on your computer.
4. Go to settings, open Networks then click on wired Networks -> IPv4
5. Select Manual and  Set the **Address:** ```192.168.1.202```
6. **Netmask:** ```255.255.255.0```
7. **Gateway:** ```0.0.0.0``` and click on apply.

## 1.4 Run the package
1. Run the launch file:
```
roslaunch velodyne_pointcloud VLP16_points.launch
```
2. Launch RVIZ
```
rosrun rviz rviz -f velodyne
```

# 2. Flir Camera

## 2.1 Installing Spinnaker SDK 

(Download)https://flir.netx.net/file/asset/54573/original/attachment

**Extract:** x64_focal -> spinnaker-2.7.0.128-amd64 

Open the terminal inside spinnaker-2.7.0.128-amd64

**DEPENDENCY INSTALLATION**
```
sudo apt-get install libavcodec58 libavformat58 \
libswscale5 libswresample3 libavutil56 libusb-1.0-0 \
libpcre2-16-0 libdouble-conversion3 libxcb-xinput0 \
libxcb-xinerama0
```
**SPINNAKER INSTALLATION**

```sudo sh install_spinnaker.sh```

**USB CAMERA SETUP**
```
sudo sh configure_usbfs.sh
sudo sh configure_spinnaker.sh
reboot
```

## 2.2 Installing ROS dependencies
``` sudo apt install libunwind-dev ros-noetic-cv-bridge ros-noetic-image-transport```

## 2.3 Installing the spinnaker_sdk_camera_driver
```
cd ~/ros_sensors/src
git clone https://github.com/Saifali4604/ROS_sensors
cd ..
catkin_make
source devel/setup.bash
```

## 2.4 Run the package
1. Run the launch file:
```
roslaunch spinnaker_sdk_camera_driver acquisition.launch
```
2. Launch RVIZ
```rviz``` go to ```by topic``` and click on ```image```

3. To launch node version of driver, use 
```
roslaunch spinnaker_sdk_camera_driver node_acquisition.launch
```
---
(Camera)https://github.com/neufieldrobotics/spinnaker_sdk_camera_driver
(VLP16)https://wiki.ros.org/velodyne/Tutorials/Getting%20Started%20with%20the%20Velodyne%20VLP16
