## UDP(User Datagram Protocol)
TCP와 UDP는 모두 OSI 7 계층 중 전송 계층에서 사용되는 프로토콜이다.<br>
TCP는 반드시 클라이언트와 서버가 안정적으로 연결된 상태에서 데이터 전송이 일어나지만<br>
UDP는 데이터를 주고 받고자 할 때 안정적인 연결이 이루어 졌는지 별도의 검사 없이 데이터 전달이 이루어진다.

UDP는 비연결형 서비스이기 때문에, 연결을 설정하고 해제하는 과정이 존재하지 않는다.<br>
서로 다른 경로로 독립적으로 처리함에도 패킷에 순서를 부여하여 재조립을 하거나 흐름 제어 또는 혼잡 제어와 같은<br>
기능도 처리하지 않기에 TCP보다 속도가 빠르며 네트워크 부하가 적다는 장점이 있지만 신뢰성 있는 데이터의 전송을<br>
보장하지는 못한다.<br>
그렇기 때문에 신뢰성보다는 `연속성`이 중요한 서비스이다. 예를 들면 실시간 서비스(Streaming)에 자주 사용된다.

<img src="https://github.com/yuwltn/yuwltn/blob/main/photo/TCPUDP.PNG" width="550" height="400" >

## References
* https://velog.io/@nnnyeong/Networking-TCP-vs-UDP
* https://mangkyu.tistory.com/15
