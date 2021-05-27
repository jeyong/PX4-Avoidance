# tf package
## coordinate frames, Transforms, TF
 * [참고자료 : Introduction to Robotics - John J. Craig](http://www.mech.sharif.ir/c/document_library/get_file?uuid=5a4bb247-1430-4e46-942c-d692dead831f&groupId=14040)
 * tf 상에 있는 Geometric object를 tf type으로 표현

### Frames와 Points
 * frame
   * 좌표 시스템
   * ROS에서는 항상 3D기준
   * 오른손 기준
   * x, y, z = forward, left, up
   * 특정 frame W 상에 있는 point p 표현 : Wp
### Frame Poses
 * 2개 frame 사이의 관계
   * 6 DOF 상대 pose로 표현
   * 회전에 의한 변환(translation by rotation)
 * 2개 frame : W, A
   * W 상에 A의 pose
     * W의 원점으로부터 A의 원점으로의 변환이(translation) 주어짐
     * W에서 A의 좌표 축의 회전(rotation)
 * translation(변환)
   * W의 좌표에서의 vector
   * WtA
   * 표현 : tf:Vector3, btVector3
 *      


## 용어
 * translation
   * W 좌표에 있는 vector
 * rotation
   * 


# Rotation
## 개념
 * 고정축(fixed Axis)
   * RPY(XYZ축으로)
 * 오일러각(Euler Angle)
   * YPR(ZYX축으로)
   * 