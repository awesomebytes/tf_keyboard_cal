# TF Keyboard Calibration and TF Interactive Marker

Move /tf frames around using your keyboard - a simple calibration-by-eye tool!

Or

Move /tf frames around using an Interactive marker!

TF Keyboard Calibration developed by Andy McEvoy and [Dave Coleman](http://dav.ee/) at the University of Colorado Boulder, TF Interactive Marker developed by [Sammy Pfeiffer](http://github.com/awesomebytes) at PAL Robotics.

 * [![Build Status](https://travis-ci.org/davetcoleman/tf_keyboard_cal.svg)](https://travis-ci.org/davetcoleman/tf_keyboard_cal) Travis CI
 * [![Devel Job Status](http://jenkins.ros.org/buildStatus/icon?job=devel-indigo-tf_keyboard_cal)](http://jenkins.ros.org/job/devel-indigo-tf_keyboard_cal) Devel Job Status
 * [![Build Status](http://jenkins.ros.org/buildStatus/icon?job=ros-indigo-tf-keyboard-cal_binarydeb_trusty_amd64)](http://jenkins.ros.org/job/ros-indigo-tf-keyboard-cal_binarydeb_trusty_amd64/) AMD64 Debian Job Status

![](resources/thing.png)

## Usage of TF Keyboard Cal:

To test, create a new ``/thing`` coordinate from the following demo:

    roslaunch tf_keyboard_cal tf_keyboard_world_to_thing.launch

Start Rviz and use the TF display to visualize its effect.

    roslaunch tf_keyboard_cal rviz_demo.launch

You can now use the keyboard shorcuts below to move the frame around. **NOTE:** Be sure to have the little black window focused on to recieve keyboard input. Once the TF has been positioned, press `p` to save the settings to the config file. The TF will use these new settings when relaunched.

    Manual alignment of camera to world CS:
    =======================================
    MOVE: X  Y  Z  R  P  YAW
    ------------------------
    up    q  w  e  r  t  y
    down  a  s  d  f  g  h
    Fast: u
    Med:  i
    Slow: o
    Save: p

Create a launch file and configuration file similar to the demos in the package's ``config/`` and ``launch/`` folders.


## Usage of TF Interactive Marker

Note that this node is self contained! You can just copy tf_interactive_marker.py and it will work in a standalone fashion.

To test, create a new ``/thing`` coordinate from the following demo (check out the parameters with -h):

    rosrun tf_keyboard_cal tf_interactive_marker.py base_footprint new_frame 1.0 0.0 1.0 0.0 0.0 1.57

You can also check the launch example (does the same):

    roslaunch tf_keyboard_cal tf_im_world_to_thing.launch

Start Rviz and use the TF display to visualize its effect.

    roslaunch tf_keyboard_cal rviz_demo.launch

Meanwhile you move the Interactive Marker the TF transform will be published (can be stopped with right click menu of the IM) and you'll see an output in the terminal like:

````
Static transform publisher command (with roll pitch yaw):
  rosrun tf static_transform_publisher 1.0 0.0 1.0 0.0 -0.0 1.57 base_footprint new_frame 50

Static transform publisher command (with quaternion):
  rosrun tf static_transform_publisher 1.0 0.0 1.0 0.0 0.7068 0.7074 0.0 base_footprint new_frame 50

Roslaunch line of static transform publisher (rpy):
  <node name="from_base_footprint_to_new_frame_static_tf" pkg="tf" type="static_transform_publisher" args="1.0 0.0 1.0 0.0 -0.0 1.57 base_footprint new_frame 50" />

URDF format:
  <origin xyz="1.0 0.0 1.0" rpy="0.0 -0.0 1.57" />
````

Which hopefully makes your life easier, you can check out a [video example here](https://www.youtube.com/watch?v=C9BbFv-C9Zo).


