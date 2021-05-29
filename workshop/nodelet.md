# [nodelet](http://wiki.ros.org/nodelet)
 * 동일 process 내에서 여러 알고리즘을 실행하는 방법 제공
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

## Thread model
 * nodelet manager
   * thread pool을 가짐
   *    manager(thread pool)
      /     !     \
nodelet   nodelet  nodelet
   * thread 개수 설정 : num_worker_threads
 * shared_ptr로 message를 publish
