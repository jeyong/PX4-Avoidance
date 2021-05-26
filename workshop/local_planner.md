# local_planner package
## class
 * LocalPlannerNodelet
 * LocalPlannerVisualization
 * LocalPlanner
 * StarPlanner
 * TreeNode
 * WaypointGenerator

### LocalPlannerNodelet
 * method
   * onInit()
   * InitializeNodelet()
   * threadFunction()
   * startNode()
   * updatePlannerInfo()
   * numTransformedClouds()
   * pointCloudTransformThread()
   * calculateWapoints()
   * publishSystemStatus()
   * setSystemStatus()
   * getSystemStatus()
   * checkFailsafe()
   * transformBufferThread()
   * dynamicReconfigureCallback()
   * initializeCameraSubscribers()
   * positionCallback()
   * pointCloudCallback()
   * cameraInfoCallback()
   * velocityCallback()
   * stateCallback()
   * cmdLoopCallback()
   * readParams()
   * clickedPointCallback()
   * clickedGoalCallback()
   * updateGoalCallback()
   * fcuInputGoalCallback()
   * distanceSensorCallback()
   * printPointInfo()
   * publishLaserScan()
 * 분류
   * 초기화 - init
     * onInit
     * Initialize nodelet
     * start node
   * thread
     * transform buffer thread
     * pointCloud transform thread
     * thread function
   * event
     * point click
     * goal click
     * fuc mission waypoint 
     * distance sensor (지상까지 거리 센서)
     * command loop
     * state
     * velocity
     * camera info
     * point cloud
     * position
     * dynamic reconfigure
   * publish
     * laser scan
   * subscribe
     * camera
   * 기타
     * checkFailsafe()
     * get/set system Status()
     * calculate waypoint
     * update planner info

### LocalPlanner
 * method
   * updateObstacleDistanceMsg() - histogram을 FCU에 보내기 위해 메시지 채우기
   * create2DObstacleRepresentation() - pointcloud의 polar histogram 표현 생성
   * generateHistogramImage() - polar histogram의 image 표현 생성
   * setState() - 기채 position, orientation, velocity에 대한 setter
   * getGoal() - mission goal
   * setPreviousGoal()
   * get/setFOV() - FOV
   * getSensorRange()
   * applyGoal()
   * dynamicReconfigureSetParams() - ROS parameter server로부터 param 설정
   * getOrientation() - 현재 비행체의 orientation 얻기
   * getPosition() - 
   * getPointcloud() - planning에 사용할 pointcloud를 시각화하기 위한 getter
   * getTree() - rviz에서 tree를 시각화하기 위한 getter
   * getAvoidanceOutput() - 
   * determineStrategy() - 장애물을 회피하는 방법과 사용할 알고리즘 결정
   * runPlanner() - local planner 알고리즘의 iteration 시작
   * setDefaultPx4Parameters()
 * member
   * original_cloud_vector_
     * 카메라에서 n개의 완전한 cloud를 포함 
   * 
### StarPlanner
 * A* 알고리즘
 * method
   * treeHeuristicFunction() - 어떤 node에 대한 heuristic 계산
   * setParams() - costMatrix param을 위한 setter
   * setPointCloud() - star_planner pointcloud를 위한 setter
   * setPose() - 비행체 position
   * setClosestPointOnLine() - 현재와 이전 goal 사이의 line에서 비행체의 position projection을 위한 setter
   * setGoal() - 현재 goal을 위한 setter
   * buildLookAheadTree() - goal 방향으로 향하는 후보군 tree 구성
   * dynamicReconfigureSetStarParams() - server param을 위한 setter

### TreeNode
 * method
   * setCosts() - tree node의 heuristic과 cost에 대한 setter

### WaypointGenerator
 * method
   * runTryPath()
   * runAltitudeChange()
   * runLoiter()
   * runDirect()
   * runCurrentState()
   * chooseNextState()
   * claculateWaypoint() - 입력 waypoint 선택을 기반으로 position, velocity waypoint를 계산
   * transformPositionToVelocityWaypoint() - position waypoint를 velocity waypoint로 변환
   * smoothWaypoint() - damped PD 제어기로 waypoint를 smooth하게
   * nextSmoothYaw() - damped PD 제어기로 next yaw smooth하게
   * adaptSpeed() - 장애물, 목표지점 접근, waypoint에 따라서 속도 변경
   * getPathMsg()
   * isAltitudeChange()
   * getWaypoints() - FCU에 전달할 position과 velocity waypoint를 위한 getter
   * setPlannerInfo() - planning 알고리즘의 최신 결과를 바탕으로 WaypointGenerator를 업데이트
   * setFOV() - camera matrix를 기반으로 FOV 설정
   * updateState() - FCU 비행체 상태를 업데이트
   * setSmoothingSpeed() - smoothing의 응답성 설정. xy, z에 대해서 설정
   * getSystemTime() - 
   * getOfftrackPointsForVisualization() - offtrack state를 시각화하기 위한 getter

## 질문
 * 몇 개의 thread
 * 각 thread의 역할
 * 각 thread의 역할은??

## flow
 * local_planner_node_main.cpp
   * local_planner_nodelet.cpp - LocalPlannerNodelet


## info
 * nodelet
 * 