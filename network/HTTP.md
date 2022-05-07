## HTTP(HyperText Transfer Protocol)
HTTP는 W3 상에서 정보를 주고 받을 수 있는 프로토콜이다.<br>
주로 `HTML 문서`를 주고 받는데에 쓰인다. 주로 `TCP`를 사용하고 HTTP/3부터는 `UDP`를 사용하며,<br>
80번 포트를 사용한다. 1996년 버전 1.0, 그리고 1999년 1.1이 각각 발표되었다.

HTTP는 `클라이언트`와 `서버` 사이에 이루어지는 `요청/응답(request/response)` 프로토콜이다.<br>
예를 들면, 클라이언트인 웹 브라우저가 HTTP를 통하여 서버로부터 웹페이지(HTML)나 그림 정보를<br>
요청하면, 서버는 이 요청에 응답하여 필요한 정보를 해당 사용자에게 전달하게 된다.<br>
이 정보가 모니터와 같은 출력 장치를 통해 사용자에게 나타나는 것이다.

### HTTP 특징
HTTP를 통해 전달되는 자료는 `http:`로 시작하는 `URL(인터넷 주소)`로 조회할 수 있다.<br>
HTTP는 연결 상태를 유지하지 않는 비연결성(Connectless) 프로토콜이다. 이러한 단점을 해결하기 위해<br>
`쿠키`와 `세션`이 등장하였다.<br>
서버에 연결하고, 요청해서 응답을 받으면 연결을 끊어버린다. 이러한 작동 방식은 장점과 단점을 가진다.<br>
* 장점 : 불특정 다수를 대상으로 하는 서비스에 적합한 방식이다. 수십만명이 웹 서비스를 사용하더라도 <br>
  접속 유지는 최소한으로 할 수 있기 때문에, 더 많은 유저의 요청을 처리할 수 있다.
* 단점 : 연결을 끊어버리기 떄문에 클라이언트의 이전 상태를 알 수가 없다. 이러한 HTTP의 특징을<br>
  `Stateless`라고 하는데 Connectless로부터 파생되는 특징이라고 할 수 있다. <br>
  클라이언트의 이전 상태 정보를 알 수 없게 되면, 당장에 문제가 생긴다. <br>
  예컨데, 클라이언트가 과거에 로그인을 성공하더라도 로그 정보를 유지할 수가 없다.<br>
  HTTP는 `쿠키(cookie)`를 이용해서 이 문제를 해결하고 있다.
  
## Requset(요청)
클라이언트가 서버에게 연락하는 것을 요청이라고 하며 요청을 보낼 때는 요청에 대한 정보를 담아 서버로 보낸다.

## 요청 메시지 구성
* 요청 내용
* 헤더
* 본문

### Method(메서드)
메서드는 요청의 종류를 서버에게 알려주기 위해서 사용한다.<br>
* GET : 자료를 `요청`할 때 사용(SELECT)
* POST : 자료의 `생성`을 요청할 때 사용(INSERT)
* PUT : 자료의 `수정`을 요청할 때 사용(UPDATE)
* DELETE : 자료의 `삭제`를 요청할 때 사용(DELETE)
* HEAD: (HTTP)헤더 정보만 요청한다. 해당 자원이 존재하는지 혹은 서버에 문제가 없는지를 확인하기 위해서 사용한다.
* OPTIONS : 웹 서버가 지원하는 메서드의 종류를 요청한다.
* TRACE: 클라이언트가 요청을 그대로 반환한다. 예컨데 echo 서비스로 서버 상태를 확인하기 위한 목적으로 주로 사용한다.

보통 웹 서비스들은 GET과 POST만을 이용하여 개발한다.<br>
왜냐하면 GET과 POST 만드로도 모든 종류의 요청을 표현할 수 있고 편하게 개발할 수 있고<br>
웹 브라우저로 DELETE, HEAD 등을 보내는 form이 없기 때문이다.

이렇게 명시적으로 메서드를 사용하지 않아도 웹 서비스 개발에 큰 문제는 없지만<br>
가능하면 CRUD를 명시하는게 좋지 않을까?

그렇다 Restful API 서버의 경우에는 GET, POST, DELETE, PUT을 명시적으로 구분한다.<br>
자원의 위치 뿐만아니라 자원의 할 일까지 명확히 명시할 수 있기 떄문에 Open API 서버를 만들기 위해서 널리 사용된다.

### 요청 메시지 예시
```
GET https://github.com/yuwltn HTTP/1.1                        // 요청 내용
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) ...     // 헤더
Upgrade-Insecure-Requests: 1
```

1. 요청 내용 <br>
* GET : HTTP Method
* https://github.com/yuwltn : 사이트 주소
* HTTP/1.1 : HTTP 버전

2. 헤더(두 번째 줄부터)<br>
두 번째 줄 부터는 헤더로 요청에 대한 정보를 담고 있다.<br>
User-Agent, Upgrade-Insecure-Requests 등등이 헤더에 해당되며 헤더의 종류는 매우 많다.

3. 본문(헤더에서 한 줄 띄고)<br>
본문은 요청을 할 때 함께 보낼 데이터를 담는 부분이다.<br>
현재 예시는 단순히 주소로만 요청을 보내고 있고 따로 데이터를 담아 보내지 않기 때문에
본문이 비어있다.

## Response(응답)
서버가 요청에 대한 답변을 클라이언트에게 보내는 것을 응답이라고 한다.

### 응답 메시지 구성
* 상태 표시 행(status line) : 상태 코드(status code)와 reson message를 포함한다.
* 응답 헤더필드
* 빈 줄(empty line)
* 기타 메시지 

### Status Code(상태 코드)
모두 숫자 세자리로 이루어져 있으며 크게 다섯가지 부류로 나눌 수 있다.

* 1XX(Informational) : 정보. 정보 교환.
* 2XX(Sucess) :  성공. 클라이언트가 요청한 동작을 수신하여 이해했고 승낙했으며 성공적으로 처리했음을 가리킨다.
* 3XX(Redirection) : 방향 바꿈. 자료의 위치가 바뀌었다. 
* 4XX(Client Error) : 클라이언트 오류. 클라이언트에 오류가 있음을 나타낸다. 주소를 잘못 입력하였거나 요청이 잘못 되었다.
* 5XX(Server Error) : 서버 오류. 서버의 오류로 올바른 요청을 처리할 수 없다.

### 응답 메시지 예시
```
HTTP/1.1 200 OK                      // 상태 표시 행
Connection: keep-alive               // 헤더
Content-Encoding: gzip
Content-Length: 35653
Content-Type: text/html;

<!DOCTYPE html><html lang="ko" data-reactroot=""><head><title ...
```

1. 상태 표시 행
첫 줄은 버전 상태코드 상태 메시지로 구성되어 있다. 200은 클라이언트의 요청이 성공적으로<br>
전달되었음을 표시한다.

2. 헤더(두 번째 줄부터)
두 번째 줄부터는 헤더로 응답에 대한 정보를 담고 있다.

3. 본문(헤더 뒤부터)
응답에는 대부분의 경우 본문이 있다. 보통 데이터를 요청하고 응답 메시지에는 요청한 데이터를 담아서<br>
보내주기 때문이다. 응답 메시지에 HTML이 담겨 있는데 이 HTML을 받아 브라우저가 화면에 렌더링한다.


## HTTP 버전
> HTTP 역사
> * HTTP/0.9 (1991년)
> * HTTP/1.0 (1996년)
> * HTTP/1.1 (1997년) : 가장 많이 사용 중
> * HTTP/2.0 (2015년) : HTTP 1.1의 성능 개선 및 확장
> * HTTP/3.0 (진행중)

### HTTP 0.9


### HTTP 1.0 
* 단기 커넥션(Short-lived connections)
* Request를 날릴 때마다 Connection을 새로 생성
* 데이터 전송
  * 플레인 텍스트
  * Data를 압축해서 전달이 가능하도록 해서 전달하는 Data 양이 감소

### HTTP 1.1
* 지속 커넥션(Persistent connection)
* 커넥션 재사용 가능
* HTTP 파이프라이닝(Pipelining)
  * Request를 미리 여러 개 서버에 날릴 수도 있게 되었다.
* 한 Request 당, 한 개의 리소스를 받아 옴
* 헤더 압축으로 인한 성능 향상
* 단점(Head Of Line blocking)
  * 요청한 Request에 문제가 있어서, 응답이 늦어지면 2번째, 3번째에 요청한 Request의 응답도 같이 늦어짐

## HTTP 2.0
* Multiplexing
  * 프레임 단위로 나눠서 전송, 관리 가능하게 됨. 다수의 요청과 응답이 가능한 구조
* 데이터 전송
  * 바이너리로 인코딩하여 전송
* ServerPush 사용
  * 브라우저에게 필요한 리소스들을 서버가 알아서 찾아다가 내려주는 것을 의미한다
  * 필요한 경우
    * 캐싱되지 않은 리소스를 받아올 때
    * 페이지에서 필요한 리소스가 페이지를 내려주는 서버에 있을 때


## References
* https://ko.wikipedia.org/wiki/HTTP
* https://velog.io/@surim014/HTTP%EB%9E%80-%EB%AC%B4%EC%97%87%EC%9D%B8%EA%B0%80
* https://www.joinc.co.kr/w/Site/Network_Programing/AdvancedComm/HTTP
* https://jobjava00.github.io/basic/http-version/
* https://velog.io/@neity16/HTTP-HTTP-%EB%B2%84%EC%A0%84-%EB%B3%84-%ED%8A%B9%EC%A7%95
