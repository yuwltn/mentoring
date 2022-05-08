# REST(Representational State Tranfer)
REST는 자원을 이름으로 구분하여 해당 자원의 상태를 주고 받는 모든 것을 의미한다.

REST는 기본적으로 웹의 기존 기술과 HTTP 프로토콜의 그대로 사용하기 때문에 웹의 장점을 최대한 활용할 수 있는 아키텍처 스타일이다.<br>
REST는 네트워크 상에서 Client와 Server 사이의 통신 방식 중 하나이다.

즉 REST란
1. HTTP URI(Uniform Resource Identifier)를 통해 자원(Resource)을 명시하고,
2. HTTP Method(POST, GET, PUT, DELETE)를 통해
3. 해당 자원(URI)에 대한 CRUD Operation을 적용하는 것을 의미한다.

> CRUD Operation
> Create : 데이터 생성(POST)
> Read : 데이터 조회(GET)
> Update : 데이터 수정(PUT)
> Delete: 데이터 삭제(DELETE)

## REST 구성 요소
1. 자원(Resource) : HTTP URI
   * 모든 자원은 고유한 ID가 존재하고, 이 자원은 Server에 존재한다.
   * 자원을 구별하는 ID는 '/groups/:group_id'와 같은 HTTP URI이다.
   * Client는 URI를 이용해서 자원을 지정하고 해당 자원의 상태(정보)에 대한 조작을 Server에 요청한다.
2. 자원에 대한 행위(Verb) : HTTP Method
   * HTTP 프로토콜의 Method를 사용한다.
   * HTTP 프로토콜은 GET, POST, PUT, DELETE와 같은 Method를 제공한다.
3. 자원에 대한 행위의 내용(Representations) : HTTP Message Pay Load
   * Client가 자원의 상태(정보)에 대한 조작을 요청하면 Server는 이에 적절한 응답(Representations)을 보낸다.
   * REST에서 하나의 자원은 JSON, XML, TEXT, RSS 등 여러 형태의 Representation으로 나타내어 질 수 있다.
   * JSON 혹은 XML을 통해 데이터를 주고 받는 것이 일반적이다.

## REST 특징
1. Server-Client(서버-클라이언트 구조)
   * 자원이 있는 쪽이 Server, 자원을 요청하는 쪽이 Client가 된다.
     * REST Server : API를 제공하고 비즈니스 로직 처리 및 저장을 책임진다.
     * Client : 사용자 인증이나 context(세션, 로그인 정보)등을 직접 관리하고 책임진다.
   * 서로 간 의존성이 줄어든다.  
2. Stateless(무상태)
   * HTTP 프로토콜이 Stateless를 갖기 때문에 REST 역시 Stateless를 갖는다.  
3. Cacheable(캐시 처리 가능)
   * HTTP가 가진 가장 강력한 특징 중 하나인 캐싱 기능을 적용할 수 있다.
5. Layered System(계층화)
   * Client는 REST API Server만 호출한다.
   * REST Server는 다중 계층으로 구성될 수 있다.
     * API Server는 순수 비즈니스 로직을 수행하고 그 앞단에 보안, 로드 밸런싱, 암호화, 사용자 인증 등을 추가하여<br>
       구조상의 유연성을 줄 수 있다.
     * 또한 로드밸런싱, 공유 캐시 등을 통해 확장성과 보안성을 향상시킬 수 있다. 
     * PROXY, 게이트웨이 같은 네트워크 기반의 중간 매체를 사용할 수 있다.
5. Uniform Interface(인터페이스 일관성)
   * URI로 지정한 Resource에 대한 조작을 통일되고 한정적인 인터페이스로 수행한다.
   * HTTP 표준 프로토콜에 따르는 모든 플랫폼에서 사용이 가능하다.
     * 특정 언어나 기술에 종속되지 않는다. 

## REST의 장단점
### 장점
* HTTP 프로토콜의 표준을 최대한 활용하여 여러 추가적인 장점을 함께 가져갈 수 있게 해준다.
* HTTP 표준 프로토콜에 따르는 모든 플랫폼에서 사용이 가능하다.
* Hypermedia API의 기본을 충실히 지키면서 범용성을 보장한다. -> 공부 더 필요
* REST API 메시지가 의도하는 바를 명확하게 나타내므로 의도하는 바를 쉽게 파악할 수 있다.
* 여러가지 서비스 디자인에서 생길 수 있는 문제를 최소화한다.
* 서버와 클라이언트의 역할을 명확하게 분리한다.

### 단점
* 표준이 존재하지 않는다.
* 사용할 수 있는 메소드가 네가지 밖에 없다.
* 브라우저를 통해 테스트 할 일이 많은 서비스라면 쉽게 고칠 수 있는 URL보다 Header 값이 왠지 더 어렵게 느껴진다.
* 구형 브라우저가 아직 제대로 지원해주지 못하는 부분이 존재한다.
  * PUT, DELETE를 사용하지 못하는 점
  * PushState를 지원하지 않는 점 

## REST가 필요한 이유
최근의 서버 프로그램은 다양한 브라우저와 안드로이드폰, 아이폰과 같은 모바일 디바이스에서도 통신을 할 수 있어야 한다.<br>
이러한 멀티 플랫폼에 대한 지원을 위해 서비스 자원에 대한 아키텍처를 세우고 이용하는 방법을 모색한 결과,<br>
REST에 관심을 가지게 된 것이다.

# REST API
REST를 기반으로 서비스 API를 구현한 것을 말한다.

최근 OpenAPI, 마이크로 서비스(하나의 큰 애플리케이션을 여러 개의 작은 애플리케이션으로 쪼개어 <br>
변경과 조합이 가능하도록 만든 아키텍처) 등을 제공하는 업체 대부분은 REST API를 제공한다.

### 특징
* 사내 시스템들도 REST 기반으로 시스템을 분산해 확장성과 재사용성을 높여 유지보수 및 운용을 편리하게 할 수 있다.
* REST는 HTTP 표준을 기반으로 구현하므로, HTTP를 지원하는 프로그램 언어로 클라이언트, 서버를 구현할 수 있다.
* 즉, REST API를 제작하면 델파이 클라이언트 뿐 아니라, 자바, C#, 웹 등을 이용해 클라이언트를 제작할 수 있다.

## REST API 설계 기본 규칙
> 리소스 원형 종류
> * 리소스(Resource) : 데이터의 일부
> * 도큐먼트(Document) : 객체 인스턴스나 데이터베이스 레코드와 유사한 개념(단수)
> * 컬렉션(Collection) : 리소스의 집합(복수)
> * 스토어(Store) : 클라이언트에서 관리하는 리소스 저장소(복수)
> * 컨트롤러(Controller) : 컬렉션, 스토어의 메서드 기능, CRUD라는 표준적인 메서드와 논리적으로 매핑되지 않는 애플리케이션의 고유한 행동을 의미(복수)

1. URI는 정보의 리소스를 표현해야 한다.
   1. 리소스는 동사보다는 명사를, 대문자보다는 소문자를 사용한다.
   2. 리소스의 도큐먼트 이름으로는 단수 명사를 사용해야 한다.
   3. 리소스의 컬렉션 이름으로는 복수 명사를 사용해야 한다.
   4. 리소스의 스토어 이름으로는 복수 명사를 사용해야 한다.<br>
      Ex) GET /Meber/1 -> GET /members/1
2. 자원에 대한 행위는 HTTP Method(GET, POST, PUT, DELETE)로 표현한다.
   1. URI에 HTTP Method가 들어가면 안된다.<br>
      Ex) GET /members/delete/1 -> DELETE /members/1
   2. URI에 행위에 대한 동사 표현이 들어가면 안된다.(URI에 CRUD 기능을 나타내는 것을 사용하지 않는다.)<br>
      Ex) GET /members/insert/2 -> POST /members/2
   3. 경로 부분 중 변하는 부분은 유일한 값으로 대체한다.<br>
      Ex) student를 생성하는 루트 : POST /students<br>
      Ex) id=12인 student를 삭제하는 루트: DELETE /students/12
      
## REST API 설계 규칙
1. 슬래시 구분자(/)는 계층 관계를 나타내는데 사용한다.
2. URI 마지막 문자로 슬래시(/)를 포함하지 않는다.
   * URI에 포함되는 모든글자는 리로스의 유일한 식별자로 사용되어야 하며 <br>
     URI가 다르다는 것은 리소스가 다르다는 것이고, 역으로 리소스가 다르면 URI도 달라져야 한다.
   * REST API는 분명한 API를 만들어 통신을 해야 하기 때문에 혼동을 주지 않도록 URI 경로의 마지막에는 슬래시(/)를 사용하지 않는다.
3. 하이픈(-)은 URI 가독성을 높이는데 사용한다.
   * 불가피하게 긴 URI 경로를 사용하게 된다면 하이픈을 사용해 가독성을 높인다.
4. 밑줄(_)은 URI에서 사용하지 않는다.
   * 밑줄은 보기 어렵거나 밑줄 때문에 문자가 가려지기도 하므로 가독성을 위해 밑줄은 사용하지 않는다.
5. URI 경로에는 소문자가 적합하다.
   * URI 경로에 대문자 사용은 피하도록 한다.
   * RFC 3986(URI 문법 형식)은 URI 스키마와 호스트를 제외하고는 대소문자를 구별하도록 규정하기 때문이다.
6. 파일확장자는 URI에 포함하지 않는다.
   * REST API에서는 메시지 바디 내용의 포맷을 나타내기 위한 파일 확장자를 URI 안에 포함시키지 않는다.
   * Accept header를 사용한다.
7. 리소스 간에 연관 관계가 있는 경우
   * /리로스명/리소스ID/관계가 있는 다른 리소스명<br>
   Ex) GET : /users/{userid}/devices (일반적으로 소유의 관계를 표현할 때)

# RESTful
RESTful이란 REST의 원리를 따르는 시스템을 의미한다.<br>
하지만 REST를 사용했다 하여 모두가 RESTful한 것은 아니다.<br>

REST API의 설계 규칙을 올바르게 지킨 시스템을 RESTful하다 말할 수 있으며<br>
모든 CRUD 기능을 POST로 처리하는 API 혹은 URI 규칙을 올바르게 지키지 않은 API는 REST API를 사용하였지만<br>
RESTful 하지 못한 시스템이라고 할 수 있다.

## References
* https://gmlwjd9405.github.io/2018/09/21/rest-and-restful.html
* https://khj93.tistory.com/entry/%EB%84%A4%ED%8A%B8%EC%9B%8C%ED%81%AC-REST-API%EB%9E%80-REST-RESTful%EC%9D%B4%EB%9E%80

