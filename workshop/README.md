# 제목
 * 워크숍 - PX4 장애물 회피 구현 이해 - AI시리즈(PX4 Avoidance Implementation)

https://www.youtube.com/watch?v=Qh5z7-PZCEs
# 목표
 * PX4 Avoidance 프로젝트 이해 및 활용
# 내용
 * 개발환경 설정
 * Avoidance 알고리즘 
 * ROS 이해
 * 구현 코드
 * 개발 방법
 * Pixhawk와 연동

# 시간
 * 2일간

# 준비물
 * Ubuntu 18.04/ROS Melodic
# 소개
 * 자율기능 중에서 가장 기본이 되는 기능은 장애물 회피와 충돌 방지입니다.
 * PX4 프로젝트가 제공하는 Avoidance 기능 구현을 위한 이론 및 실제 구현에 이해하는 워크숍을 마련하였습니다.
 * 실습
 * 이론 이해
 * 기체 장착
# 내용
 * Avoidance 개발 환경
   * 따라서 실행하기
   * 전체 구조
   * 연결 방법
   * 각자 실행시키기
 * 알고리즘
   * 비행 예제 (Youtube로 만들기)
     * 무한루프 (설정값)
     * 특정 지점까지 가기 (설정값)
   * Local Planner 비행 방식
     * histogram
     * Octomap
     * strategy
     * Library
 * ROS
   * node들 소개
     * tf(*)
     * stereo camera 관련
     * block matching
     * OpenCV
   * mavros
 * gazebo
   * server
   * client
   * sdf 파일
 * PX4 모듈
   * simullator 모듈
 * avoidance 패키지
   * aovoidance library
   * local_planner 구조
   * nodelet
 * 실제 비행체 탑재
   * NVIDIA + Realsense(ZED 카메라)
 * C++ for Avoidance
   * 어떤 C++ 문법을 알아야할까?
   * 자주쓰는 패턴?
   
# ToDo
 * 알고리즘
 * 개발환경
 * ROS
 * Stereo Camera
 * PX4 설정
 * 시뮬레이션
 * Gazebo
 * QGC
 * docker
 * mavros