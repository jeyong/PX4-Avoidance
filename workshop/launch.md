# launch 파일 분석
## local_planner_stereo.launch
### 실행 순서
 * tf.tf_depth_camera
 * rqt_reconfigure.rqt_reconfigure
 * px4.launch
 * mavros.launch
 * gazebo.launch(empty_world.launch)
 * gazebo_ros.spawn_model (vehicle model 생성)
 * stereo_image_proc.stereo_image_proc
 * local_planner_node
 * rviz

## log_replay.launch
 * rosbag.player
 * local_planner.local_planner_node
 * rviz.rviz
 * rqt_reconfigure.rqt_reconfigure
### 실행 순서
 *  