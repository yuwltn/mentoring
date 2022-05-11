## URI(Uniform Resource Identifier)
URI는 특정 리소스를 식별하는 `통합 자원 식별자`를 의미한다.

## URL(Uniform Resource Locator)
URL은 흔히 웹 `주소`라고도 하며, 컴퓨터 네트워크 상에서 리소스가 어디 있는지 알려주기 위한 규약이다.<br>
URI의 서브넷이다.

## URI vs URL
> URI는 식별하고, URL은 위치를 가리킨다.

<img src="https://github.com/yuwltn/yuwltn/blob/main/photo/URIURL.PNG" width="300" height="300" >

URL은 URI에 포함된다.

URL이면 URI이지만 URI라고해서 URL인 것은 아니다.<br>
즉, 식별자(URI)는 위치에 대한 정보가 없으므로 URL이 될 수 없고 <br>
주소(URL)는 특정 위치를 가르키기 때문에 간접적으로 식별하기도 해서 URI가 될 수 있다.

실제 네트워크 상에서 URI와 URL의 예시는 다음과 같다.

<img src="https://github.com/yuwltn/yuwltn/blob/main/photo/URI.PNG" width="700" height="200" >
두 주소는 모두 index.html을 가리키고 있다.

첫 번째 주소는 웹 서버의 실제 파일 위치를 나타내는 `주소`이므로 URI이면서 URL이다.<br>
두 번째 주소는 실제로 index라는 파일이 웹 서버에 존재하지 않으므로 URL은 아니다. 하지만 서버 내부에서<br>
이를 처리하여 결국 index.html을 가리키기 때문에 URI라고 볼 수 있다.

## URI 구조
```
scheme:[//[user[:password]@]host[:port]][/path][?query][#fragment]
```

1. scheme : 사용할 프로토콜을 뜻하며 웹에서는 http 또는 https를 사용
2. user와 password : (서버에 있는) 데이터에 접근하기 위한 사용자의 이름과 비밀번호
3. host와 port : 접근할 대상(서버)의 호스트명과 포트번호
4. path : 접근할 대상(서버)의 경로에 대한 상세 정보
5. query : 접근할 대상에 전달하는 추가적인 정보 (파라미터)
6. fragment : 메인 리소스 내에 존재하는 서브 리소스에 접근할 때 이를 식별하기 위한 정보

## References
* https://www.charlezz.com/?p=44767
