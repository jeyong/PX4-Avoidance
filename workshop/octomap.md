# OctoMap
 * 3D Occupancy grid mapping library
   * data structure
   * mapping algorithm (C++)
   * octree 기반
## 특징
 * Full 3D model
   * free 공간과 occupied 공간 표현
   * unknown 영역에 대해 encoding 가능 (uncertain state)
   * 자율 주행에 적합(free, occupied, unkown 영역 구분 가능해야함)
 * Updatable
   * 센서나 기타 새로운 정보로 언제든 update 가능
   * modeling과 update는 통계적 방식
   * 하나의 map을 여러 robot이 업데이트 가능
 * Flexible
   * multi-resolution
     * coarse map, fine map(local planner)
     * 시각화시에 zoom in/out 가능
 * Compact
   * 저장시 메모리 효율
   * 압축 가능(통신 및 교환시 유리)
## Occupancy Grid Map
 * 공간을 독립적인 cell로 나누기
 * 각 cell은 0/1로 occupied or free 표현
 * 각 cell에 대해서 static state binary Bayes filter
 * pose를 알고 있으면 mapping이 쉽다.
 * log odds model은 계산이 빠름
 * predefined features에 대한 필요가 없음
## 참고
 * [ROS OctoMap](http://wiki.ros.org/octomap)
 * [OctoMap](http://octomap.github.io/)
 * [논문 : OctoMap:An Efficient Probabilistic 3D Mapping Framework Based on Octrees](http://ais.informatik.uni-freiburg.de/publications/papers/hornung13auro.pdf)
