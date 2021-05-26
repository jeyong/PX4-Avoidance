# Avoidance package
## launch
 * tf.tf_depth_camera
 * stereo_image_proc.stereo_image_proc
 * avoidance_sitl_mavros.launch
   * rqt_reconfigure.rqt_reconfigure
   * gazebo_ros.spawn_model
   * px4.launch
   * node.launch
   * empty_world.launch

## class
 * AvoidanceNode
 * Histogram
 * WorldVisualizer
 * TransformBuffer
 * StateMachine

### AvoidanceNode
 * method
   * checkFailsafe()
   * getPX4Parameters()
   * getMissionItemSpeed()
   * getSystemStatus()
   * checkPx4Parameters()
   * setSystemStatus()
   * init()
   * missionCallback()
   * cmdLoopCallback()
   * statusLoopCallback()
   * pubishSystemStatus()
   * px4ParamCallback()
 * member
   * publish : mavros_system_status_pub_
   * subscribe : px4_param_sub_, mission_sub_
   * thread

### Histogram
 * method
   * wrapIndex() - histogram 주변에 elevation과 azimuth를 wrap하기
   * get_dist() - histogram cell 거리 getter
   * set_dist() - histogram cell 거리 setter
   * upsample() - histogram의 upsampled 버전 계산하기
   * downsample() - histogram의 downsampled 버전 계산하기
   * setZero() - histogram의 cell age와 distance를 0으로 설정
   * isEmpty() - histogram이 empty인지 결정(distance layer는 0보다 큰 distance를 포함하지 않는다.)

### WorldVisualizer
 * method
   * resolveUri() - gazebo model path를 resolve하기 위한 helper function
   * loopCallback() - 
   * initializePublisher() - local planner visualization을 위해 사용한 모든 publisher를 초기화
   * positionCallback() - mav pose topic을 subscribe한다.
   * visualizeRVIZWorld() - yaml 파일을 parse하고 world marker를 publish한다.
   * visualizeDrone() - 현재 drone position에서 drone mesh를 시각화한다.

## 질문
 * 각 class가 하는 일은?
 * thread가 있는지?
 * pub/sub 메시지, from/to node 찾기

