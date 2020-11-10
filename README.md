# Cartographer for Multi-Robot Exploration

This is the modified Cartographer from [original](https://google-cartographer-ros.readthedocs.io/en/latest/compilation.html).

## Installation


1. Install Dependency on Ubuntu18.04

    ```
    sudo apt-get update
    sudo apt-get install -y python-wstool python-rosdep ninja-build stow
    ```

2. After the tools are installed, create a new cartographer_ros workspace in ```catkin_ws```.

    ```
    mkdir -p catkin_ws/src
    cd catkin_ws/src
    git clone https://github.com/efc-robot/Cartographer-for-SMMR.git
    ```

3. Update the ROS dependencies at the ```catkin_ws```.
    ```
    cd .. #cd to the catkin_ws
    sudo rosdep init
    rosdep update
    rosdep install --from-paths src --ignore-src --rosdistro=${ROS_DISTRO} -y
    ```

4. Cartographer uses the abseil-cpp library that needs to be manually installed using this script
   ```
   src/cartographer-master/scripts/install_abseil.sh
   ```
    Due to conflicting versions you might need to uninstall the ROS abseil-cpp using
    ```
    sudo apt-get remove ros-${ROS_DISTRO}-abseil-cpp
    ```

5. Build and install the ```catkin_ws```
   ```
   catkin_make_isolated --install
   ```

7. Source the ```setup.bash``` to use Cartographer
    ```
    source /PATH/TO/CATKIN_WS/devel_isolated/setup.bash
    ```
    or add the ```source``` to the ```~/.bashrc```.

8. If you have only prolem, you can refer to the original [installation guide](https://google-cartographer-ros.readthedocs.io/en/latest/compilation.html) to install&test the original Cartographer. And just replace the coresponding folders in ```catkin_ws/src/``` with these our provided  three folders. And rebuild the Cartographer.
