## 알고리즘
 * local planner
   * vector field histogram
   * VFH+* - [논문](https://drive.google.com/file/d/1yjDtxRrIntr5Mdaj9CCB4IFJn0Iy2-bR/view)
 * global planner
   * graph 기반
   * octomap occupancy grid
 * safe landing planner
   * local planner로 착륙할 safe area 찾기
## PX4
 * 장애물 회피(Obstacle Avoidance)
 * Collision Prevention(충돌 방지)

## Docker
 * Ubuntu 20.04 에서 가능한지
 * 
## Tool
 * rviz
 * rosbag
 * 
## Index
 * 실행하기
   * 개발환경 설치
     * Ubuntu 20.04 (or Ubuntu 18.04)
     * Visual Studio Code
     * ROS
 * 기술 분해
   * ROS
   * PX4
   * Gazebo
   * QGC
 * ROS
   * 기술
     * launch 파일 읽기
   * 알고리즘
 * 응용분야
   * Mission 인증
   * Failsafe 테스트
   * ....
 * 실제 기체에 적용

## 분석 방법
 * 실행 flow
   * local_planner_stereo.launch 시작
 * 각 package.node 역할
 * node간 통신
 * class - local_planner
 * class - avoidance

## local_planner_stereo.launch
 * local_planner.local_planner_node
 * rviz.rviz
 * avoidance_sitl_stereo.launch
   * tf.tf_depth_camera
   * stereo_image_proc.stereo_image_proc
   * avoidance_sitl_mavros.launch
     * rqt_reconfigure.rqt_reconfigure
     * gazebo_ros.spawn_model
     * px4.launch (px4)
     * node.launch (mavros)
     * empty_world.launch (gazebo)
 
## Localization 알고리즘
 * Extended Kalman Filter (v)
 * Markov Localization
 * Grid Localization
 * Monte Carlo Localization (v) (particle)

## Localization 문제 종류
 * Position tracking
   * local localization
     * robot은 초기 자신의 위치를 알고 있다.
     * world를 돌면서 robot의 위치를 estimate하는 것
 * global location
   * robot의 초기 위치를 모름
   * ground truth map에서 자신의 pose를 결정해야만 함
 * kidnapped problem
   * global localization과 유사
   * 순간순간 다른 위치로 robot이 점프한다는 점이 다른점
   * 잘못 계산하고 난 후 복구 즉 보정할 때 필요하다.

## 고려 사항
 * world의 특징
   * static
   * dynamic

## 순서
 * kalman filter 배우기
 * sensor fusion
 * MCL(Monte Carlo Localization)
 * C++ MCL

## MCL
 * 개념
 * MCL vs. EKF
 * Particle Filters
 * Bayes Filtering
 * MCL Pseudo Code
 * MCL 적용
### MCL vs. EKF
 * 장점
   * 구현이 쉽
   * linear Gaussian states-based 가정을 하지 않아도 됨(모든 world를 Guassian으로 바라보지 않아도 되어서 다양한 접근 가능) - noise 측정
   * 메모리 및 resolution 제어 가능(리소스 사용 제한 가능)
  
## MCL
 * 초기
   * 어디 있는지 모름
 * global localization 문제를 해결함으로써 자신의 pose를 estimate할려고 노력
 * 센싱
   * 센싱을 통해서 자신이 어디 있는지 확인
 * 현재 robot pose
   * x, y, orientation vector
 * particle을 random하게 공간에 뿌린다.
 * 각 particle도 robot처럼 x, y, orientation, weight를 가진다.
 * weight
   * robot의 실제 pose와 particle의 예상 pose
   * 값이 클수록 resample하는 동안 살아남는다.
 * iteration을 거쳐서
   * particle들이 수렴되어 robot의 pose를 estimation하게 된다.
