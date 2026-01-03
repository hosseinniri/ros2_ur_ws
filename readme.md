# ROS2 UR5 Workspace with Gazebo Simulation

This repository contains a complete ROS2 Humble workspace for **Universal Robots UR5**, including:

* ROS2 driver for UR5
* Gazebo simulation with controllers
* MoveIt2 configuration for motion planning

---

## 📝 Prerequisites

* Ubuntu 22.04
* ROS2 Humble installed
* Gazebo 11 installed
* `colcon` build tools
* Python3 packages: `rosdep`, `vcs`, etc.

---

## 📂 Workspace Structure

```
ros2_ur_ws/
├── src/
│   ├── Universal_Robots_ROS2_Driver
│   └── Universal_Robots_ROS2_Gazebo_Simulation
├── build/          # ignored in git
├── install/        # ignored in git
├── log/            # ignored in git
└── README.md
```

---

## ⚡ Setup Instructions

### 1. Clone repository

```bash
git clone https://github.com/hosseinniri/ros2_ur_ws.git
cd ros2_ur_ws
```

### 2. Install dependencies

```bash
sudo apt update
sudo apt install python3-rosdep2
rosdep update
rosdep install --from-paths src --ignore-src -r -y
```

### 3. Build workspace

```bash
rm -rf build install log
colcon build --symlink-install
```

### 4. Source environment

```bash
source /opt/ros/humble/setup.bash
source install/setup.bash
```

---

## 🚀 Run UR5 in Gazebo

### 1. Launch simulation with controllers

```bash
ros2 launch ur_simulation_gazebo ur_sim_control.launch.py
```

This will:

* Start Gazebo with an empty world
* Spawn the UR5 robot
* Load joint state and trajectory controllers

---

### 2. Launch simulation with MoveIt2 (motion planning)

```bash
ros2 launch ur_simulation_gazebo ur_sim_moveit.launch.py
```

This will:

* Start Gazebo
* Load UR5 robot
* Start MoveIt2 with planning scene

---

### 3. Spawn robot manually (optional)

If needed, you can spawn the UR5 from `robot_description`:

```bash
ros2 run gazebo_ros spawn_entity.py -entity ur5 -topic robot_description
```

---

## 📌 Notes

* **Do not push **`**, **`**, **``** to GitHub**. Use `.gitignore` to ignore them.
* To rebuild workspace after changes:

```bash
colcon build --symlink-install
source install/setup.bash
```

* Make sure to source both ROS2 and workspace every new terminal:

```bash
source /opt/ros/humble/setup.bash
source ~/ros2_ur_ws/install/setup.bash
```

---

## 🔗 References

* [Universal Robots ROS2 Driver](https://github.com/UniversalRobots/Universal_Robots_ROS2_Driver)
* [Universal Robots Gazebo Simulation](https://github.com/ros-industrial/universal_robot)
* [ROS2 Humble Installation](https://docs.ros.org/en/humble/Installation.html)
* [Gazebo Tutorials](http://gazebosim.org/tutorials)
* [MoveIt2 Tutorials](https://moveit.ros.org/documentation/)

---

## 🛠️ Author

Hossein Niri
