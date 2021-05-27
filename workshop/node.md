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
## [stereo_image_proc](http://wiki.ros.org/stereo_image_proc)
 * stereo image
   * 교정
   * 차이
 * stereo camera driver <-> vision processing nodes
   * 중간에 위치
 * 2개 camera에 대한 image_proc 담당
   * 왜곡 없애고(undistortion) 색상 보정
   * undistortion : rectification, image 변환
 * 2개 camera 사이의 차이를 계산
   * [OpenCV blocking matching 알고리즘](https://docs.opencv.org/2.4/modules/calib3d/doc/camera_calibration_and_3d_reconstruction.html#stereobm)
 * camera에서 들어오는 이미지 확인 - stereo_view 이용
   * http://wiki.ros.org/image_view#stereo_view
 * point cloud 생성
   * rviz로 확인 가능
   * pcl로 처리

## [nodelet](http://wiki.ros.org/nodelet)
 * 1개 process에서 여러 알고리즘을 실행하는 방법
   * 알고리즘 <-> 알고리즘간 zero copy transport
 * 사용법
   * nodelet base class 상속
   * NodeletLoader을 이용해서 nodelet을 instance
 * 문제 상황
   * A, B, C 알고리즘 수행
   * nodeA, nodeB, nodeC 생성
   * nodeA --> nodeB 로 topic 전달
   * nodeB --> nodeC 로 topic 전달
 * 무슨 문제가 있지?
   * call by value
   * call by reference
 * 특징
   * 동적 실행 (dll)
   * 동작은 별도의 node처럼 동작(동일 process에서 실행)
   * node로 개발하느냐? nodelet으로 개발하느냐? 코드상 약간의 차이가 있음
 * 적용 분야
   * high throughput data flow
 * [nodelet 실행](http://wiki.ros.org/nodelet/Tutorials/Running%20a%20nodelet)

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
