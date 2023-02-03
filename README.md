# ca1_2023s

include your report here. 
these are my result  for each cli
$ros2 run turtlesim turtlesim_node
#output
Warning: Ignoring XDG_SESSION_TYPE=wayland on Gnome. Use QT_QPA_PLATFORM=wayland to run on Wayland anyway.
[INFO] [1675461527.795708121] [turtlesim]: Starting turtlesim with node name /turtlesim
[INFO] [1675461527.799225340] [turtlesim]: Spawning turtle [turtle1] at x=[5.544445], y=[5.544445], theta=[0.000000]

femi@femi-GE72VR-7RF:~$ ros2 run turtlesim turtle_teleop_key
#output for runing the teleop key
Reading from keyboard
---------------------------
Use arrow keys to move the turtle.
Use G|B|V|C|D|E|R|T keys to rotate to absolute orientations. 'F' to cancel a rotation.
'Q' to quit.

#ros node info 
femi@femi-GE72VR-7RF:~$ ros2 node info /turtlesim/turtlesim
Unable to find node '/turtlesim/turtlesim'
femi@femi-GE72VR-7RF:~$ ros2 node info /teleop_turtle 
/teleop_turtle
  Subscribers:
    /parameter_events: rcl_interfaces/msg/ParameterEvent
  Publishers:
    /parameter_events: rcl_interfaces/msg/ParameterEvent
    /rosout: rcl_interfaces/msg/Log
    /turtle1/cmd_vel: geometry_msgs/msg/Twist
  Service Servers:
    /teleop_turtle/describe_parameters: rcl_interfaces/srv/DescribeParameters
    /teleop_turtle/get_parameter_types: rcl_interfaces/srv/GetParameterTypes
    /teleop_turtle/get_parameters: rcl_interfaces/srv/GetParameters
    /teleop_turtle/list_parameters: rcl_interfaces/srv/ListParameters
    /teleop_turtle/set_parameters: rcl_interfaces/srv/SetParameters
    /teleop_turtle/set_parameters_atomically: rcl_interfaces/srv/SetParametersAtomically
  Service Clients:

  Action Servers:

  Action Clients:
    /turtle1/rotate_absolute: turtlesim/action/RotateAbsolute

    ##remapping
femi@femi-GE72VR-7RF:~$ ros2 run turtlesim turtlesim_node 
--ros-args --remap __node:=my_turtle
Warning: Ignoring XDG_SESSION_TYPE=wayland on Gnome. Use QT_QPA_PLATFORM=wayland to run on Wayland anyway.
[INFO] [1675463121.171570736] [my_turtle]: Starting turtlesim with node name /my_turtle
[INFO] [1675463121.178685100] [my_turtle]: Spawning turtle [turtle1] at x=[5.544445], y=[5.544445], theta=[0.000000]\

#display of rostopic list

femi@femi-GE72VR-7RF:~$ ros2 topic list
/parameter_events
/rosout
/turtle1/cmd_vel
/turtle1/color_sensor
/turtle1/pose

#the ros topic type output

femi@femi-GE72VR-7RF:~$ ros2 topic list -t
/parameter_events [rcl_interfaces/msg/ParameterEvent]
/rosout [rcl_interfaces/msg/Log]
/turtle1/cmd_vel [geometry_msgs/msg/Twist]
/turtle1/color_sensor [turtlesim/msg/Color]
/turtle1/pose [turtlesim/msg/Pose]

#the rostopic echoing pose
femi@femi-GE72VR-7RF:~$ ros2 topic echo /turtle1/pose
x: 5.544444561004639
y: 5.544444561004639
theta: 0.0
linear_velocity: 0.0
angular_velocity: 0.0
---
x: 5.544444561004639
y: 5.544444561004639
theta: 0.0
linear_velocity: 0.0
angular_velocity: 0.0

#echoing velocity
femi@femi-GE72VR-7RF:~$ ros2 topic echo /turtle1/cmd_vel 

linear:
  x: 2.0
  y: 0.0
  z: 0.0
angular:
  x: 0.0
  y: 0.0
  z: 0.0
---
linear:
  x: 0.0
  y: 0.0
  z: 0.0
angular:
  x: 0.0
  y: 0.0
  z: -2.0
---
#check topic info
femi@femi-GE72VR-7RF:~$ ros2 topic info /turtle1/cmd_vel 
Type: geometry_msgs/msg/Twist
Publisher count: 1
Subscription count: 2
