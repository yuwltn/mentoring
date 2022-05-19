CORS 정책은 우리가 가져오는 리소스들이 안전한지 검사하는 관문이다.

### 출처(Origin)이란?
서버의 위치를 의미하는 URL의 구성에서 출처는 Protocol, Host, Port까지 모두 합친 것을 의미한다.<br>

<img src="https://github.com/yuwltn/yuwltn/blob/main/photo/Origin.PNG" width="700" height="250" >

웹에는 `SOP(Same Origin Policy)`와 `CORS(Corss Origin Resurce Sharing)` 두가지 정책이 있다.

## 동일 출처 정책(SOP, Same Origin Policy)
SOP는 같은 출저에서만 리소스를 공유할 수 있다라는 규칙을 가진 정책이다.<br>
두 개의 출처를 비교하는 방법은 URL의 구성요소중 Protocol, Host, Port 이 세가지가 동일한지 확인하면 된다.

출처를 비교하는 로직은 서버에 구현된 스펙이 아닌 브라우저에 구현된 스펙이다.<br>
만약 CORS 정책을 위반하는 요청에 서버가 정상적으로 응답을 하더라도 브라우저가 이 응답을 분석해서<br>
CORS 정책에 위반되면 그 응답은 처리하지 않게 된다.

요약하면 프로토콜, 포트, 호스트 중 하나라도 일치하지 않으면 Cross Origin이라고 한다.

## 교차&다른 출처 리소스 공유(CORS, Cross Origin Resource Sharing)
CORS는 추가 HTTP 헤더를 사용하여, 한 출처에서 실행중인 웹 애플리케이션이 다른 출처의 선택한 자원에<br>
접근할 수 있는 권한을 부여하도록 브라우저에 알려주는 체제이다.

### CORS 기본 동작과정
1. 클라이언트에서 HTTP 요청의 헤더에 Origin을 담아 전달한다.<br>
2. 서버는 응답헤더에 Access-Control-Allow-Origin을 담아 클라이언트로 전달한다.<br>
3. 클라이언트에서 자신이 보냈던 요청의 Origin과 서버가 보내준 Access-Control-Allow-Origin을 비교한다.<br>
  만약 유효하지 않다면 그 응답을 사용하지 않고 버린다.
  
## CORS 해결방법 두가지
1. 서버에서 Access-Control-Allow-Origin 세팅하기<br>
  가장 정성적이고 근본적인 해결책이다.
  ```
  res.setHeader('Access-Control-Allow-origin', '*');
  res.setHeader('Access-Control-Allow-Credentials', 'true'); //쿠키 주고 받기 허용
  ```
  이때 `*`을 사용하면 모든 Origin에서 오는 요청을 허용한다는 의미이므로 당장은 편할 수 있겠지만<br>
  정체도 모르는 이상한 출처에서 오는 요청까지 모두 허용하기 때문에 보안은 더 허술해진다.
  ```
  res.setHeader('Access-Control-Allow-origin', 'http://example.com');
  ```
  그래서 가급적 귀찮더라도 출처를 명시해주는 것이 좋다.
2. Proxy
    
  
  ## References
  * https://inpa.tistory.com/entry/WEB-%F0%9F%93%9A-CORS-%F0%9F%92%AF-%EC%A0%95%EB%A6%AC-%ED%95%B4%EA%B2%B0-%EB%B0%A9%EB%B2%95-%F0%9F%91%8F
