# lbr_fri_meta

This repository builds Conda packages for **lbr_fri_ros2_stack** with multiple FRI client versions.  
Supported FRI versions: **1.11, 1.14, 1.15, 1.16, 1.17, 2.5, and 2.7**.

---

## How to Use the LBR FRI Packages

### ROS 2 Humble

#### Step 0  
Clone the RoboStack ROS Humble repository:  
https://github.com/RoboStack/ros-humble

#### Step 1  
Edit `pixi.toml` as follows:

```toml
[project]
...
# Add kenichi-maeda and robostack-staging channels
channels = [
  "https://repo.prefix.dev/conda-forge",
  "kenichi-maeda",
  "https://repo.prefix.dev/robostack-staging"
]

# Choose your platform
platforms = ["linux-64"]

[dependencies]
python = ">=3.11.0,<3.12"
rattler-build = ">=0.44.0"
anaconda-client = ">=1.12"

# Required for ROS 2 launch support
ros-humble-ros2launch = ">=0.19.10,<0.20"
...
```

#### Step 2  
After running:

```bash
pixi run build
```

install the LBR packages:

```bash
pixi add \
  ros-humble-iiwa7-moveit-config \
  ros-humble-iiwa14-moveit-config \
  ros-humble-med7-moveit-config \
  ros-humble-med14-moveit-config \
  ros-humble-kinematics-interface \
  ros-humble-kinematics-interface-kdl \
  ros-humble-lbr-description \
  ros-humble-lbr-moveit \
  ros-humble-lbr-moveit-cpp \
  "ros-humble-fri-client-sdk=*=fri1_15" \
  "ros-humble-lbr-fri-idl=*=fri1_15" \
  "ros-humble-lbr-fri-ros2=*=fri1_15" \
  "ros-humble-lbr-fri-ros2-stack=*=fri1_15" \
  "ros-humble-lbr-ros2-control=*=fri1_15" \
  "ros-humble-lbr-bringup=*=fri1_15" \
  "ros-humble-lbr-demos-cpp=*=fri1_15" \
  "ros-humble-lbr-demos-py=*=fri1_15" \
  "ros-humble-lbr-demos-advanced-cpp=*=fri1_15" \
  "ros-humble-lbr-demos-advanced-py=*=fri1_15"
```

You can change the FRI version tag as needed.  
Available options: **1.11, 1.14, 1.15, 1.16, 1.17, 2.5, 2.7**.

---

### ROS 2 Jazzy

Follow the same procedure as for Humble.

---

## Notes

### How to Build `.conda` Packages

#### Humble

**Step 1**  
Navigate to the ROS Humble directory:

```bash
cd ros/ros-humble
```

**Step 2**  
Run the build commands:

```bash
pixi run build-lbr-base
pixi run build-fri
```

#### Jazzy

Follow the same procedure as for Humble.

**Step 3**  
Upload the generated `.conda` files located in:

```
output/linux-64
```
