## TCP(Transmisson Control Protocol)
전송 제어 프로토콜(TCP)은 인터넷 프로토콜 스위트(IP)의 핵심 프로토콜 중 하나로,<br>
IP와 함께 TCP/IP라는 명칭으로도 널리 불린다.<br>

### 역할
TCP는 근거리 통신망이나 인트라넷, 인터넷에 연결된 컴퓨터에서 실행되는 프로그램 간에 <br>
일련의 옥텟을 안정적으로, 순서대로, 에러없이 교환할 수 있게 한다.<br>

### 특징
* TCP는 OSI 7Layer 중 4계층 전송 계층에 위치하고 네트워크의 정보 전달을 통제하는 프로토콜이자 
  인터넷을 이루는 핵심 프로토콜의 하나이다.
* TCP는 웹 브라우저들이 월드 워이드 웹에서 서버에 연결할 때 사용되며, 
  이메일 전송이나 파일 전송에도 사용된다.
* TCP는 동시제어가 가능하다. 이는 초기 요청이 작게 시작해도 컴퓨터들과 서버들의 대역폭의 깊이가 증가해도
  네트워크가 지원할 수 있다는 것을 뜻한다.

```
OSI 7 Layer 쉽게 이해하기
7 Layer - 응용(Application) : HTTP, SMTP, SNMP, FTP, 텔넷, NFS, NTP
6 Layer - 표현(Presentation) : XDR
5 Layer - 세션(Session) : TCP의 세션 관리 부분
4 Layer - 전송(Transport) : TCP, UDP, RTP, SCTP
3 Layer - 네트워크(Network) : IP, ICMP, IPsec, ARP, RIP, BGP
2 Layer - 데이터 링크(Data Link)
1 Layer - 물리(Physical)

Transport Layer(4 Layer)
전송 계층
송신자와 수신자의 논리적 연결(Connection)을 담당하는 부분으로, 신뢰성 있는 연결을 
유지할 수 있도록 도와준다. 즉 Endpoint(사용자) 간의 연결을 생성하고 데이터를 
얼마나 보냈는지 얼마나 받았는지, 제대로 받았는지 등을 확인한다.
TCP와 UDP가 대표적이다.

Network Layer(3 Layer)
네트워크 계층
IP(Internet Protocaol)이 활용되는 부분으로, 한 Endpoint가 다른 Endpoint로 
가고자 할 경우, 경로와 목적지를 찾아준다. 이를 Routing이라고 하며 
대역이 다른 IP들이 목적지를 향해 제대로 찾아갈 수 있도록 돕는 역할을 한다.
```

### TCP/IP
TCP/IP는 패킷 통신 방식의 인터넷 프로토콜 `IP`와 전송 조절 프로토콜인 `TCP`로 이루어져 있다.<br>
`IP`는 패킷 전달 여부를 보증하지 않고, 패킷을 보낸 순서와 받는 순서가 다를 수 있다.<br>
`TCP`는 IP 위에서 동작하는 프로토콜로, 데이터의 전달을 보증하고 보낸 순서대로 받게 해준다.<br>
HTTP, FTP, SWTP 등 TCP를 기반으로 한 많은 수의 애플리케이션 프토토콜들이 IP 위에서 동작하기 때문에,<br>
묶어서 TCP/IP로 부르기도 한다.

TCP/IP를 사용하겠다는 것은 `IP` 주소 체계를 따르고 IP Routing을 이용해 목적지에 도달하여
`TCP`의 특성을 활용해 송신자와 수신자의 논리적 연결을 생성하고 신뢰성을 유지할 수 있도록 하겠다는 것을 의미한다.

즉, TCP/IP를 말한다는 것은 송신자가 수신자에게 IP 주소를 사용하여 데이터를 전달하고
그 데이터가 제대로 갔는지, 너무 빠르지는 않았는지, 제대로 받았다고 연락은 오는지에 대한 이야기를 하는 것이다.

우리가 인터넷에서 무언가를 다운로드 할 때 중간에 끊기거나 빠지는 부분 없이 완벽하게 받을 수 있는 이유도
TCP의 이러한 특성 덕분이다.

TCP를 기반으로 하는 프로토콜들은 차후 언급할 TCP의 '3 way handshake'를 거친 후, 각자 프로토콜(Layer 7)에 기반한
교환 과정을 실시한다.

IP가 패킷들의 관계를 이해하지 못하고 그저 목적지를 제대로 찾아가는 것에 중점을 둔다면
TCP는 통신하고자 하는 양쪽 단말(endpoint)이 통신할 준비가 되었는지, 데이터가 제대로 전송되었는지,
데이터가 가는 도중 변질되지는 않았는지, 수신자가 얼마나 받았고 빠진 부분은 없는지 등을 점검한다.

이런 정보는 TCP Header에 담겨 있으며 SYN, ACK, FIN, RST, Source Port, Destination Port, 
Sequence Number, Window Size, Checksum과 같은 `신뢰성 보장`과 `흐름 제어`, `혼잡 제어`에 관여할 수 있는 요소들도
포함되어 있다. 또한 IP Head er와 TCP Header를 제외한 TCP가 실을 수 있는 데이터 크키를 `세그먼트(Segment)`라고 부른다.

[TCP Header]
<img src="https://github.com/yuwltn/yuwltn/blob/main/photo/TCPHeader.PNG" width="900" header="300" >


## TCP 3 way handshake
> TCP 연결 생성

TCP는 장치들 사이에 논리적인 접속을 성립(establish)하기 위하여 3 way handshake를 사용한다. <br>
TCP 3 way handshake는 TCP/IP 프로토콜을 이용해서 통신을 하는 응용프로그램이 데이터를 전송하기 전에<br>
먼저 정확한 전송을 보장하기 위해 상대방 컴퓨터와 사전에 세션을 수립하는 과정을 의미한다.

Client > Server : TCP SYN(Synchronize sequence numbers)<br>
Server > Client : TCP SYN ACK(Acknowledgment)<br>
Client > Server : TCP ACK<br>

### TCP 3 way handshaking 역할
양쪽 모두 데이터를 전송할 준비가 되었다는 것을 보장하고, 실제로 데이터 전달을 시작하기 전에<br>
한 쪽이 다른 쪽이 준비되었다는 것을 알 수 있도록 한다.<br>
양쪽 모두 상대편에 대한 초기 순차 일련번호를 얻을 수 있도록 한다.<br>

### TCP 3 way handshaking 과정
<img src="https://github.com/yuwltn/yuwltn/blob/main/photo/TCP3-way.PNG" width ="550" height="350" >

STEP1<br>
A 클라이언트는 B 서버에 접속을 요청하는 `SYN` 패킷을 보낸다. <br>
이때 A 클라이언트는 `SYN`을 보내고 `SYN/ACK` 응답을 기다리는 `SYN_SENT` 상태가 되는 것이다.

STEP2<br>
B 서버는 `SYN` 요청을 받고 A 클라이언트에게 요청을 수락한다는 `ACK`와 `SYN flag`가 설정된 패킷을 <br>
발송하고 A가 다시 `ACK`로 응답하기를 기다린다. 이때 B서버는 `SYN_RECEIVED` 상태가 된다.

STEP3<br>
> TCP 연결 종료

A 클라이언트는 B 서버에게 ACK을 보내고 이후로부터는 연결이 이루어지고 데이터가 오가게 되는 것이다.<br>
이때의 B 서버 상태가 `Established`이다.

## TCP 4 way handshake
TCP 4way handshake는 세션을 종료하기 위해 수행되는 절차

## TCP 4 way handshacking 과정 
<img src="https://github.com/yuwltn/yuwltn/blob/main/photo/TCP4way.PNG" width="500" height="400" >

STEP1
클라이언트가 연결을 종료하겠다는 `FIN` 플래그를 전송한다.

STEP 2
서버는 일단 확인 메세지를 보내고 자신의 통신이 끝날 때까지 기다리는데 이 상태가 `TIME_WAIT` 상태다.

STEP 3
서버가 통신이 끝났으면 연결이 종료되었다고 클라이언트에게 `FIN` 플래그를 전송한다.

STEP 4
클라이언트는 확인했다는 메세지를 보낸다.

그런데 만약 "Server에서 FIN을 전송하기 전에 전송한 패킷이 Routing 지연이나 패킷 유실로 인한 재전송 등으로
인해 FIN 패킷보다 늦게 도착하는 상황"이 발생한다면 어떻게 될까?

클라이언트에서 세션을 종료시킨 후 뒤늦게 도착하는 패킷이 있다면
이 패킷은 DROP되고 데이터는 유실될 것이다.

이러한 현상에 대비하여 클라이언트는 서버로부터 FIN을 수신하더라도 일정시간(default 240초) 동안
세션을 남겨놓고 잉여 패킷을 기다리는 과정을 거치게 되는데 이 과정을 `TIME_WAIT`이라고 한다.

## TCP가 안정적인 네트워크를 보장하는데 4가지 문제점
1. 손실 : 패킷이 손실될 수 있는 문제
2. 순서 바뀜 : 패킷의 순서가 바뀌는 문제
3. 혼잡 : 네트워크가 혼잡한 문제
4. 오버로드 : 수신측이 오버로드되는 문제

## 흐름제어(Flow control)
> Host와 Host 간에 데이터 처리를 효율적으로 하기 위한 기법, End to End)
> `송신측(클라이언트)`과 `수신측(서버)` 사이의 `전송 속도`를 다룬다.

수신측이 송신측보다 속도가 빠른 것은 문제가 되지 않지만, 송신측이 수신측보다 속도가 빠르면 문제가 발생한다.
수신측에서 수신된 데이터를 처리에서 윗 계층으로 서비스하는 속도보다 송신측에서 보내는 데이터 속도가 더 빠르다면,
수신측에서 제한된 저장용량(일반적으로 큐)을 초과하여 이후에 도착하는 데이터의  `손실 `을 가져올 수 있다.
이렇게 되면 불필요하게 응답과 재전송의 데이터가 다시 송신측과 수신측 간에 빈번히 이동해야 한다.
따라서 이러한 위험을 줄이기 위해 송신측의 데이터 전송량을 수신측에 따라 조절해야 한다.

두가지 방법이 있다.
### Stop and Wait 방식
매번 전송한 패킷에 대해 확인 응답을 받아야만 그 다음 패킷을 전송하는 방법

### Sliding Window 방식
수신측에서 설정한 윈도우 크기만큼 송신측에서 확인 응답없이 세그먼트를 전송할 수 있게 하여
데이터 흐름을 동적으로 조절하는 제어 기법


## 혼잡제어
## 오류제어
## UDP
