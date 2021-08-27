# Robot_Arm_Control_in_ROS
**This Repository will explain my first task in smart method**
## Task Requirements:
- Control a robot arm using ROS platform with Rviz, Gazebo and Moveit Simulator.
## Steps:
1. Install Ubuntu to work with ROS.I will use Ubuntu-18.04 with a virtual machine like Virtual box.
2. Instal [ROS Melodic](http://wiki.ros.org/melodic/Installation/Ubuntu) using the commands bellow in the terminal (Melodic is the version of ROS that correspond with Ubuntu-18.04).
* `sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'`
* `sudo apt install curl` 
* `curl -s https://raw.githubusercontent.com/ros/rosdistro/master/ros.asc | sudo apt-key add -`
* `sudo apt-get update`
* `sudo apt install ros-melodic-desktop-full`
* `apt search ros-melodic`
* `echo "source /opt/ros/melodic/setup.bash" >> ~/.bashrc`
* `source ~/.bashrc`
* `sudo apt install python-rosdep python-rosinstall python-rosinstall-generator python-wstool build-essential`
* `sudo apt install python-rosdep`
* `sudo rosdep init`
*  `rosdep update`
3. Install a Catkin Workspace which is a folder to combine all packages for ROS.
* `sudo apt-get install ros-melodic-catkin` 
* `mkdir -p ~/catkin_ws/src`
* `cd ~/catkin_ws/`
* `catkin_make`
* `cd ~/catkin_ws/src`
* `git clone https://github.com/smart-methods/arduino_robot_arm.git` we will use the arm from SM to work with.
* `cd ~/catkin_ws`
* `rosdep install --from-paths src --ignore-src -r -y`
*  `sudo apt-get install ros-melodic-moveit`
*  `sudo apt-get install ros-melodic-joint-state-publisher ros-melodic-joint-state-publisher-gui`
*  `sudo apt-get install ros-melodic-gazebo-ros-control joint-state-publisher`
*  `sudo apt-get install ros-melodic-ros-controllers ros-melodic-ros-control`
*  open a file (bashrc) : `sudo nano ~/.bashrc`.
*  At the end of the file add the follwing line`source /home/username/catkin_ws/devel/setup.bash` then press ctrl + o,(Note that username is your ubuntu username).
*  `source ~/.bashrc`
*  To lunch the Rviz simulator with slider motors control (joint_state_publisher) use this command `roslaunch robot_arm_pkg check_motors.launch`
*  Rviz Simulator:

![Rviz](https://github.com/faisalsaud63192/Robot_Arm_Control_in_ROS/blob/main/Rviz.png)

4. Control the Arm in Gazebo simulator .
* Change the permission `cd catkin/src/arduino_robot_arm/robot_arm_pkg/scripts` then `sudo chmod +x joint_states_to_gazebo.py`
* Open new terminal to launch Rviz `roslaunch robot_arm_pkg check_motors.launch`
* Open new terminal to launch Gazebo `roslaunch robot_arm_pkg check_motors_gazebo.launch`
* Then run the python script to communicate with Gazebo `rosrun robot_arm_pkg joint_states_to_gazebo.py` 
* Rviz with Gazebo:
![Gazebo](https://github.com/faisalsaud63192/Robot_Arm_Control_in_ROS/blob/main/Gazebo.png)
5. Now, lets used Moveit in Rvis which will help for kinematics, motion planning, trajectory processing and controlling the robot 
* `roslaunch moveit_pkg demo.launch`
* Moveit:

![3](https://github.com/faisalsaud63192/Robot_Arm_Control_in_ROS/blob/main/3.png)

![moveit](https://github.com/faisalsaud63192/Robot_Arm_Control_in_ROS/blob/main/moveit.png)

6. Task is Done .

