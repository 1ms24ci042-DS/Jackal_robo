# Jackal Workspace (jackal_ws)

This workspace contains packages for control, navigation, simulation, and related utilities.

> [!IMPORTANT]
> **SUBMISSION REFERENCE (ROS 1)**
> * **ROS Version:** ROS 1 Melodic (Ubuntu 18.04 container)
> * **Submission Launch Point:** `run.py` (points to E-Band local planner via `move_base_EBAND.launch`)
> * **Final Validated Metric Score:** **0.4063** (from a 90-run stratified sample: worlds 0, 30, 60, 120, 150, 180, 210, 240, 270 x 10 runs each)
> * **Testing Command:** `./singularity_run.sh nav_competition_image.sif python3 run.py --world_idx 0`
> * For full details, see the [SUBMISSION_NOTES.md](file:///home/sankala-mahidhar/jackal_ws/src/the-barn-challenge/SUBMISSION_NOTES.md) file included in the package.

This repository contains a rigorously optimized, high-performance classical navigation stack for the **Clearpath Jackal UGV**, designed for the **ICRA BARN (Benchmark Autonomous Robot Navigation)** Challenge.

## Workspace Structure

```text
jackal_ws/
├── src/                          # Source code directory
│   ├── barn-applr/              # Barn Applicator package
│   ├── eband_local_planner/      # E-Band local planner for navigation
│   ├── jackal/                   # Main Jackal robot packages
│   ├── jackal_desktop/           # Desktop visualization and tools
│   ├── jackal_simulator/         # Gazebo simulation packages
│   ├── the-barn-challenge/       # The Barn Challenge project
│   └── The-Barn-Challenge-Ros2/  # Alternative Barn Challenge package
│
├── build/                        # Build output directory (CMake)
├── devel/                        # Development install directory
├── install/                      # Installation directory
├── log/                          # Build logs
├── .git/                         # Git repository
└── README.md                     # This file
```

## Key Packages

### Core Jackal Packages
* **jackal**: Main robot packages including base controller and drivers
* **jackal_control**: Control system for Jackal robot
* **jackal_description**: URDF robot description files
* **jackal_navigation**: Navigation stack and related configurations
* **jackal_msgs**: Custom message definitions
* **jackal_helper**: Helper utilities and tools
* **jackal_tutorials**: Example and tutorial packages

### Navigation & Planning
* **eband_local_planner**: E-Band elastic band local planner for path planning

### Simulation & Visualization
* **jackal_simulator**: Gazebo simulation environment
* **jackal_desktop**: RViz configurations and visualization tools

### Projects
* **barn-applr**: Barn application package
* **the-barn-challenge**: The Barn Challenge implementation
* **The-Barn-Challenge-Ros2**: ROS 2 version of Barn Challenge

## Prerequisites
* ROS 2 (Humble or compatible version)
* Colcon build system
* Gazebo simulator (for simulation)
* RViz (for visualization)

## Building

```bash
# Navigate to workspace
cd jackal_ws

# Build all packages
colcon build

# Build specific package
colcon build --packages-select <package_name>

# Build with CMake verbose output
colcon build --cmake-args -DCMAKE_BUILD_TYPE=Debug
```

## Setup

```bash
# Source the setup script
source install/setup.bash

# Or for zsh
source install/setup.zsh
```

## Running

After building and sourcing the setup:

```bash
# Launch Jackal simulation
ros2 launch jackal_simulator jackal_world.launch.py

# Launch navigation
ros2 launch jackal_navigation navigation.launch.py

# Run The Barn Challenge
ros2 launch the-barn-challenge <launch_file>
```

## Repository Information
* **Repository**: https://github.com/1ms24ci042-DS/Jackal_robo.git
* **Branch**: main
* **Last Updated**: July 15, 2026

## Contributors
* Dhanekula Sathwika
* S Madhidhar
* Reema Sree Harshini
* Raji
* Manish

## License
Please check individual packages for license information.

## Notes
* This workspace uses ROS 2 with colcon build system
* The workspace includes both simulation and real robot packages
* Refer to individual package README files for detailed documentation
* Build artifacts (build/, devel/, install/) are generated during compilation

## Troubleshooting

If you encounter build issues:
* Ensure ROS 2 is properly installed and sourced
* Run `colcon clean` to clean build artifacts
* Delete `build/`, `devel/`, and `install/` directories and rebuild
* Check package dependencies with `rosdep install --from-paths src --ignore-src -r -y`

For more information, visit the Jackal documentation or refer to individual package documentation.
