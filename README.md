# UGV_SLAM Project

But i make project do slam on 2d map for automation navigation(creating a map in an unknown environment) 
 
## Overview
The **UGV_SLAM** project is designed to implement a robust Simultaneous Localization and Mapping (SLAM) system for an Unmanned Ground Vehicle (UGV). The system utilizes sensors such as LIDAR, cameras, and an IMU to enable the UGV to navigate autonomously through unknown environments while simultaneously creating and updating a map of the surroundings.

The SLAM system integrates real-time data to achieve high-performance navigation and obstacle detection, enabling the UGV to perform tasks such as autonomous path planning, environmental mapping, and localization in real-time. This project is intended to serve as the foundation for future autonomous vehicle systems in industrial, research, and defense applications.

## Features
- **SLAM Implementation**: The project uses LIDAR, camera, and IMU data to simultaneously localize the UGV and map its environment. 
  - We employ algorithms such as **Graph-SLAM** and **EKF (Extended Kalman Filter)** for state estimation and mapping.
  - LIDAR data is processed to detect and avoid obstacles in the UGV’s path.
- **Obstacle Detection**: The system uses real-time object detection and environmental data to avoid obstacles dynamically while navigating.
  - This feature ensures that the UGV can safely operate in unstructured environments without human intervention.
- **Navigation**: The navigation stack includes path planning and real-time localization based on the map and sensory data. The UGV dynamically adjusts its path to avoid obstacles and reach target locations.
- **Sensor Fusion**: Integration of multiple sensors (LIDAR, camera, IMU) allows the system to correct for inaccuracies in individual sensor data and produce accurate real-time maps.
- **Autonomous Decision-Making**: The system uses a decision-making algorithm to autonomously choose paths based on the generated map and real-time sensory input.

## Technical Implementation
The **UGV_SLAM** project integrates several advanced techniques in robotics, sensor fusion, and machine learning. Below are the primary components involved in the system’s implementation:

### 1. **SLAM Algorithm**:
   - **Graph-SLAM**: This method builds a map of the environment and localizes the UGV by optimizing over a graph of poses and observations. Each node in the graph represents the robot's pose at a particular time, and edges represent sensor observations.
   - **EKF-SLAM**: The Extended Kalman Filter (EKF) is used for state estimation. The system tracks the position of the robot and the map features in real-time while correcting errors in the robot's pose.

### 2. **Sensor Integration**:
   - **LIDAR**: LIDAR sensors provide precise distance measurements and are essential for detecting obstacles and building a 2D or 3D map of the environment.
   - **Camera (RGB or Depth)**: Cameras assist with object recognition and mapping in the visual spectrum. The depth camera can generate 3D point clouds, which are used to further enhance the map's accuracy.
   - **IMU (Inertial Measurement Unit)**: The IMU is used to help with the robot's orientation, especially when GPS or other global positioning systems are unavailable.

### 3. **Localization and Path Planning**:
   - The robot uses **Monte Carlo Localization (MCL)** to estimate its position based on the map it generates.
   - **A* or Dijkstra’s Algorithm** is used for path planning to calculate the most efficient path to a target location while avoiding obstacles.
   
### 4. **Obstacle Avoidance**:
   - The system implements **Dynamic Window Approach (DWA)** for real-time obstacle avoidance, using the robot's speed and velocity data to calculate the safest path.
   - LIDAR and camera data are processed using **object detection algorithms** to identify obstacles, such as walls, other vehicles, or humans.

### 5. **Real-Time Mapping**:
   - The SLAM system updates the map in real-time as the robot moves. This is accomplished by using **occupancy grid maps**, where each cell represents an area of the environment that can either be occupied, free, or unknown.
   - The system can generate **2D or 3D maps** depending on the sensor data available.

### 6. **Simulation Environment**:
   - For testing purposes, the system can be simulated using tools like **Gazebo** and **RViz** in ROS2. These tools provide a 3D visualization of the robot’s movement and the environment, allowing developers to test algorithms without requiring physical hardware.

## Requirements
- **Software Dependencies**:
  - ROS2 (Robot Operating System 2)
  - Python 3.x
  - OpenCV
  - LIDAR and Camera Sensors (if hardware integration is necessary)
  - ROS2 packages: `slam_toolbox`, `robot_localization`, `sensor_msgs`, `rviz`, and others.
  
- **Hardware Requirements**:
  - UGV platform (robot chassis with necessary sensors for SLAM)
  - LIDAR sensor (e.g., RPLIDAR, Hokuyo)
  - Camera (RGB or Depth camera)
  - IMU sensor (e.g., MPU6050, or a similar sensor)
  
## Installation
### 1. Clone the repository:
```bash
git clone https://github.com/aybergen1/UGV_SLAM.git
cd UGV_SLAM
