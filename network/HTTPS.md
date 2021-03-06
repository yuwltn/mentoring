## HTTPS가 필요한 이유
일반 HTTP 프로토콜의 문제점은 서버에서부터 브라우저로 전송되는 정보가 암호화되지 않아서<br>
데이터가 쉽게 도난당할 수 있다. HTTPS는 HTTPS의 `SSL`이나 `TLS` 프로토콜을 사용해서<br>
데이터를 `암호화`하여 이런 보안 문제를 해결해 줄 수 있다.

HTTPS는 보안 말고도 SEO 품질(검색 엔진 최적화)에 있어서도 큰 이점이 있다.<br>
또한 가소화된 모바일 페이지(AMP, Accelerated Mobile Pages)를 만들고 싶을 때도 <br>
HTTPS 프로토콜을 사용해야 한다. 여기서 AMP란 모바일 기기에서 훨씬 빠르게 콘텐츠를 로딩하기 위한<br>
방법으로 구글이 만든 것이다. AMP는 HTML에서 불필요한 부분을 없앤 것이라고 볼 수 있다.<br>
구글의 SERP(검색 결과 페이지)를 보면 스마트폰과 태블릿의 사용자들이 모바일에서 사용하기<br>
편하도록 AMP 콘텐츠들이 두드러져 보이는 것을 볼 수 있다.

모바일 친화적인 웹사이트를 만드는 것과 모바일 검색 순위 및 지역에 SEO를 증가시키는 것이<br>
점점 더 중요해지고 있는 요즘에는 HTTP를 HTTPS로 전환하는 것이 필수라고 볼 수 있다.

## HTTPS
HTTP는 Hypertext Transfer Protocol Secure의 약자이다.<br>
HTTPS는 쉽게 말해서 HTTP 프로토콜에 보안 기능을 추가한 것이라고 말할 수 있다.

HTTPS 프로토콜은 `SSL(보안 소켓 계층, Secure Sockets Layer)`을 사용하는데<br>
SSL은 서버와 브라우저 사이에 안전하게 암호화된 연결을 만들 수 있게 도와주고,<br>
서버 브라우저가 민감한 정보를 주고 받을 때 이것이 도난당하는 것을 막아준다.

SSL 인증서는 사용자가 사이트에 제공하는 정보를 `암호화`하는데, <br>
쉽게 말해서 데이터를 암호로 바꾼다고 할 수 있다. 이렇게 전송된 데이터는 중간에서 누군가<br>
훔친다고 하더라도 데이터가 암호화되어있기 때문에 해독할 수 없다.

그 외에도 HTTPS는 `TLS(전송 계층 보안, Transport Layer Security)` 프로토콜을 통해서도 보안을 유지한다.<br>
TSL은 데이터 무결성을 제공하기 때문에 데이터가 전송 중에 수정되거나 손상되는 것을 방지하고,<br>
사용자가 자신이 의도하는 웹사이트와 통신하고 있음을 입증하는 인증 기능도 제공하고 있다.

## HTTPS HandShake
> 암호화 : 어떤 정보를 암호화된 정보로 바꾸는 것<br>
> 복호화 : 암호화된 정보를 다시 원래 정보로 바꾸는 것<br>
> 키 : 암호화, 복호화할 때 쓰는 비밀번호<br>
> 개인키 = 비밀키 = 비공개키 => 대칭키<br>
> 공개키 => 비대칭키
  
* 대칭키 방식 : 암호화할 때와 복호화할 때 하나의 비밀키를 양쪽(client&server)이 같이 사용하는 방식이다.
    * 장점 : 단순한 구조로 CPU를 적게 쓰고 빠르다.
    * 단점 : 비밀키만 알아내면 복호화를 할 수 있으므로 보안에 취약하다는 단점이 있다.
* 비대칭키 방식 : 암호화할 때와 복호화할 때 `공개키`와 `개인키` 두 개를 사용하는 비대칭 방식이다.
    * 클라이언트는 `개인키`를, 서버는 `인증서`와 `공개키`를 제공하며, 클라이언트는 서버가 제공한<br>
      `공개키`를 통해 데이터를 `암호화`하여 서버에게 전송한다. 서버는 수신한 HTTPS의 `인증서`와<br>
      `공개키` 일치를 바탕으로 `개인키`로 데이터를 `복호화`해 요청에 응답한다.
    * 장점 : 키 전송 과정 중 빼앗겨도(해킹 당해도) 빼앗은 자(해커)가 해독할 수 없어 대칭키 방식보다
      안전하다.
    * 단점 : 대칭키 방식보다 느리고 리소스 소비가 크다. 

HTTPS는 대칭키 방식과 비대칭키 방식을 같이 사용한다.
비대칭 키 방식이 가진 이점은 이어가되 전송 소요시간 및 리소스 부담은 줄이는 방식을 사용하는 것이다.

## SSL Handshake(TLS Handshake)
HTTPS가 TCP 기반의 프로토콜이기 때문에 연결을 생성하기 위해 TCP layer의 `3-way handshake`를 <br>
먼저 진행하고 `SSL Handshake`를 진행한다.

SSL Handshake는 송신자와 수신자가 암호화된 데이터를 교환하기 위한 일련의 협상 과정을 의미한다.<br>
협상과정에는 SSL 인증서 전달, 대칭키(비밀키) 전달, 암호화 알고리즘 결정, SSL/TLS 프로토콜 결정 등이 포함된다.


> 1. 암호화 알고리즘(Cipher Suite) 결정<br>
> 2. 데이터를 암호화할 대칭키(비밀키) 전달<br>

> Client Hello(암호화 알고리즘 나열 및 전달) -> Server Hello(암호화 알고리즘 선택) -> Certificate(인증서 검증, 전달) ->
> Server Key Exchange / Server Hello Done(데이터를 암호화 할 대칭키 전달) -> Client Key Exchange(정보 전달 완료) ->
> ChangeCipherSpec/Finished(SSL Handshake 종료)<br>
> 과정이 끝나면 Client와 Server는 데이터를 암호화할 동일한 `대칭키(비밀키)`를 갖게 되며, 서로에게 각자 갖고 있는 동일한
> 대칭키를 통해 데이터를 암호화하여 전송하거나 데이터를 복호화한다.<br>


1. Client Hello<br>
   Client가 Server에 연결을 시도하며 전송하는 패킷이다.<br>
   자신이 사용 가능한 암호화 알고리즘 목록, Session ID, SSL Protocol Version, Random byte 등을 전달한다.

   암호화 알고리즘은 SSL Protocol Version, 인증서 검증, 데이터 암호화 프로토콜, Hash 방식 등의<br>
   정보를 담고 있는 존재로 선택된 암호화 알고리즘에 따라 데이터를 암호화한다.

   Client가 사용 가능한 암호화 알고리즘은 Server에서 제공한다.<br>
2. Server Hello<br>
   Client가 보내온 ClientHello Packet을 받아 암호화 알고리즘 중 하나를 선택한 다음 Client에게 이를 알린다.<br>
   또한 자신의 SSL 프로토콜 버전 등도 같이 보낸다. 
3. Certificate<br>
   Server가 자신의 SSL `인증서`를 Client에게 전달한다. 인증서 내부에는 Server가 발행한 `공개키`가 들어있다.<br>
   Client는 Server가 보낸 CA(Certificate Authority, 인증기관)의 `개인키`로 암호화된 이 SSL `인증서`를<br>
   이미 모두에게 공개된 CA의 `공개키`를 사용하여 `복호화`한다.<br>
   복호화에 성공하면 이 인증서는 CA가 서명한 것이 맞는 것이니 진짜임이 증명되는 것이다.<br>
   즉, 인증서를 검증하는 것이다.
   
   또한, Client는 데이터 암호화에 사용할 `대칭키(비밀키)`를 생성한 후, SSL 인증서 내부에 들어있던 <br>
   `공개키`를 이용해 `암호화`하여 Server에게 전송할 것이다.
4. Server Key Exchange / Server Hello Done<br>
   'Server Key Exchange'는 Server의 `공개키`가 SSL 인증서 내부에 없는 경우, Server가 직접 전달함을 의미한다.<br>
   `공개키`가 SSL 인증서 내부에 있을 경우 Server Key Exchange는 생략된다. 인증서 내부에 공개키가 있다면<br>
   Client가 CA의 공개키를 통해 인증서를 복호화한 후 Server의 공개키를 확보할 수 있다. 
5. Client Key Exchange<br>
   대칭키(비밀키, 데이터를 실제로 암호화하는 키)를 Client가 생성하여 SSL 인증서 내부에서 추출한 <br>
   Server 공개키를 이용해 암호화한 후 Server에 전달한다. 여기서 전달된 `대칭키`가 바로 SSL Handshake의 <br>
   목적이자 가장 중요한 수단인 데이터를 실제로 암호화할 대칭키이다. 이제 키를 통해 Client와 Server가 <br>
   교환하고자 하는 데이터를 암호화한다.
6. ChangeCipherSpec/Finished<br>
   Client, Server 모두가 서로에게 보내는 Packet으로 교환할 정보를 모두 교환한 뒤 통신할 준비가 다 되었음을 <br>
   알리는 패킷이다. 그리고 'Finished' Packet을 모내어 SSL Handshake를 종료하게 된다. 
   

## References
* https://blog.wishket.com/http-vs-https-%EC%B0%A8%EC%9D%B4-%EC%95%8C%EB%A9%B4-%EC%82%AC%EC%9D%B4%ED%8A%B8%EC%9D%98-%EB%A0%88%EB%B2%A8%EC%9D%B4-%EB%B3%B4%EC%9D%B8%EB%8B%A4/
* https://blog.wishket.com/http-%EA%B7%B8%EB%A6%AC%EA%B3%A0-https%EC%9D%98-%EC%9D%B4%ED%95%B4/
* https://aws-hyoh.tistory.com/entry/HTTPS-%ED%86%B5%EC%8B%A0%EA%B3%BC%EC%A0%95-%EC%89%BD%EA%B2%8C-%EC%9D%B4%ED%95%B4%ED%95%98%EA%B8%B0-3SSL-Handshake
