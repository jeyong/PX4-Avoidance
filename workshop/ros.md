# ROS
 
## Package
 * tf
 * rviz
 * topic
 * stereo_image_proc

## [stereo_image_proc](http://wiki.ros.org/stereo_image_proc)
 * stereo image에 대한 rectification 및 disparity processing
 * stereo camera driver <-> vision processing nodes 사이에 위치
 * 2개 camera에 대한 image_proc 담당
   * 왜곡 없애고(undistortion) 색상 보정
   * undistortion : rectification, image 변환
 * 2개 camera 사이의 disparity 계산
   * [OpenCV blocking matching 알고리즘](https://docs.opencv.org/2.4/modules/calib3d/doc/camera_calibration_and_3d_reconstruction.html#stereobm)
 * camera에서 들어오는 이미지 확인 - stereo_view 이용
   * http://wiki.ros.org/image_view#stereo_view
 * stereo processing
   * disparity images 및 point clouds 생성
 * point cloud 생성
   * rviz로 확인 가능
   * pcl로 처리
 
 ![](http://wiki.ros.org/stereo_image_proc/cturtle?action=AttachFile&do=get&target=stereo_image_proc.png)


## realsense2_camera
 * [realsense2_camera](http://wiki.ros.org/realsense2_camera)
## launch
 * 
## tool
 * 
