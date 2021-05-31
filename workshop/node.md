# nodes
 * tf.static_transform_publisher (tf_depth_camera)
 * rqt_reconfigure.rqt_reconfigure
 * px4.launch
 * mavros.launch
 * gazebo.launch(empty_world.launch)
 * gazebo_ros.spawn_model (vehicle model 생성)
 * [stereo_image_proc.stereo_image_proc](http://wiki.ros.org/stereo_image_proc)

 * local_planner_node
 * rviz

## [rqt_reconfigure](http://mirror-ap.wiki.ros.org/rqt_reconfigure.html)
 * parameter 확인 및 수정

 ![](http://mirror-ap.wiki.ros.org/attachments/rqt_reconfigure/reconfigure_gui1.png)

## tf
 * 시간에 따른 다양한 coordinate frame을 추적
 * 특정 시간 동안 tree구조로 buffer에 저장
 * 이를 point, vector 등으로 변환(2개 좌표 frame 사이의 변환)
 * robotics
   * 시간에 따른 3D 좌표 frame의 변화
     * world frame, base frame, gripper frame, head frame
   * 질문
     * 5초 전에 world frame에 대한 head frame은?
     * base에 대한 gripper에서 pose는?
     * map frame에서 base frame의 pose는?
 * ToDO
   * http://wiki.ros.org/tf/Tutorials/Introduction%20to%20tf     

## static_transform_publisher
 * static transform을 전송하는 tool
 * static transform을 tf에게 publish
   * x, y, z (단위 : m) yaw/pitch/roll (단위 : radian)
 * 
## Point
 * node의 역할
 * 간단한 사용 방법
