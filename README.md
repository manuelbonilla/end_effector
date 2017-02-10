In order to make the system work

t1 - roslaunch end_effector single_lwr.launch

t2 - "send the robot to a proper initial position" 

	 rostopic pub -1 /lwr/joint_trajectory_controller/command trajectory_msgs/JointTrajectory "header:
  seq: 0
  stamp:
    secs: 0
    nsecs: 0
  frame_id: ''
joint_names: ['lwr_a1_joint', 'lwr_a2_joint', 'lwr_a3_joint', 'lwr_a4_joint', 'lwr_a5_joint', 'lwr_a6_joint', 'lwr_e1_joint']
points:
- positions: [-0.0, 0.9215338450516, -0.8796459430038002, 1.0088003076525998, -0.0, 1.2461650859237996, -0.712094334813]
  velocities: []
  accelerations: []
  effort: []
  time_from_start: {secs: 1.0, nsecs: 0}"


t3 -  rosservice call /lwr/controller_manager/switch_controller "start_controllers: ['fphic']
stop_controllers: ['joint_trajectory_controller', 'stiffness_trajectory_controller', 'damping_trajectory_controller', 'add_torque_trajectory_controller']
strictness: 2"


if a parameter needs to e updated 

t4 - rosparam set /lwr/fphic/kx 5000.0