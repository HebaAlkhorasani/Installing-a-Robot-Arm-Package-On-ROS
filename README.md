# Installing-a-Robot-Arm-Package-On-ROS


Setup the environment and install the package as follows:
  1.	ROS-Melodic must be installed on an Ubuntu 18.04 virtual machine following this link: https://wiki.ros.org/melodic/Installation/Ubuntu 
  2.	Run the virtual machine terminal.
  3.	Create a workspace named catkin_ws (or another name, however, make sure to change the name in the next steps too!) following this link: http://wiki.ros.org/catkin/Tutorials/create_a_workspace 
  4.	Clone the robot_arm_package from GitHub inside catkin_ws/src:
  ```
  $ cd ~/catkin_ws/src
  $ sudo apt install git
  $ git clone https://github.com/smart-methods/arduino_robot_arm
  ```
  5.	Install the required dependencies inside catkin_ws:
  ```
  $ cd ~/catkin_ws
  $ rosdep install --from-paths src --ignore-src -r -y
  $ sudo apt-get install ros-melodic-moveit
  $ sudo apt-get install ros-melodic-joint-state-publisher ros-melodic-joint-state-publisher-gui
  $ sudo apt-get install ros-melodic-gazebo-ros-control joint-state-publisher
  $ sudo apt-get install ros-melodic-ros-controllers ros-melodic-ros-control
  ```
  6.	Compile the package:
  ```
  $ catkin_make
  ```
      
Use ROS tools to control and simulate the arm as follows:
  1.	Launch RViz to visualize the arm:
  ```
  $ roslaunch robot_arm_pkg check_motors.launch
  ```
  2.	You may need to change the permission 
  ```
	$ cd catkin/src/arduino_robot_arm/robot_arm_pkg/scripts
	$ sudo chmod +x joint_states_to_gazebo.py
  ```
  3. Launch Gazebo to simulate the motion:
  ```
  $ roslaunch robot_arm_pkg check_motors_gazebo.launch
  $ rosrun robot_arm_pkg joint_states_to_gazebo.py
  ```
  4.	Launch MoveIt to obtain the trajectories needed to move the robot arm to a specific position:
  ```
  $ roslaunch moveit_pkg demo.launch
  ```
      
Use ROS with Arduino IDE:
  1.	Download Arduino IDE on the virtual machine.
  2.	Install rosserial: 
  ```
  $ sudo apt-get install ros-melodic-rosserial-arduino
  $ sudo apt-get install ros-melodic-rosserial
  ```
  3.	Install ros_lib following this link: https://maker.pro/arduino/tutorial/how-to-use-arduino-with-robot-operating-system-ros#:~:text=%20Software%20Setup%20%201%20Install%20ROS%20on,the%20ros_lib%20package%20in%20the%20IDE.%20More%20 
  
  4.	Continue with connecting the USB.

