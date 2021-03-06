HTTP Method 중 GET과 POST의 특징과 차이점에 대해서 알아보겠습니다.

## 1. GET 방식
어떠한 정보를 가져와서 조회하기 위해서 사용하는 방식
<br><br>

### 특징
* URL에 변수(데이터를) 포함시켜 요청한다.
  * 보내는 데이터 양에 한계가 있다. <br>
    HTTP 자체는 GET 방식의 URL 길이에 제약을 두고 있지는 않지만, 브라우저에서 최대 길이를 제한하고 있으며 <br>
    URL형식에 맞지 않는 파라미터 이름이나 값은 인코딩되어 전달해야 한다. <br>
    (보내는 데이터의 길이가 너무 길면 초과데이터는 절단된다.)
* 데이터를 `Header(헤더)`에 포함하여 전송한다.
* `?`마크를 통해 URL의 끝을 알리고, 여러개의 Key와 Value를 보내는 경우에 `&`를 사용하여 이어준다.
* URL에 데이터가 노출되어 보안에 취약하다.
  *  GET방식은 최소한의 보안유지도 하지 않기 때문에 실제 웹사이트에서 ID와 PW같은 중요한 정보를 <br>
     GET방식으로 사용하면 개인정보가 노출되는 문제가 발생한다.
* 캐싱할 수 있다.
  GET방식을 사용하여 데이터를 노출시키는 경우는 개인정보가 포함되지 않는 상황에서 <br>
  캐싱을 하여 속도를 높이거나 즐겨찾기를 편리하게 하기 위해 사용되는 경우가 많다.<br>
  * 캐싱 : 한 번 접근 후, 또 요청할 시 빠르게 접근하기 위해 레지스터에 데이터를 저장시켜 놓는 것
<br><br>

## 2. POST
데이터를 서버로 제출하여, 추가 또는 수정하기 위해서 사용하는 방식
<br><br>

### 특징
* URL에 변수(데이터)를 노출하지 않고 요청해서 보안이 유지된다.
* 데이터를 `Body`에 포함시킨다.
  * 헤더필드 중 Body의 데이터를 설명하는 Content-Type이라는 헤더 필드가 들어가고 어떠한 데이터 타입인지 명시해주어야 한다.
  * 데이터를 Body에 포함시키는 이점 때문에 메시지의 길이 제한은 없지만, 최대 요청을 받는 시간인 TimeOut이 존재하므로<br>
    클라이언트에서 페이지를 요청하고 기다리는 시간이 존재한다.
* 캐싱할 수 없다.
  * 실제로 POST 방식은 URL에 데이터가 노출되지 않으므로 즐겨찾기나 캐싱이 불가능하지만 <br>
    쿼리스트링(문자열) 데이터 뿐만아니라 라디오 버튼, 텍스트 박스와 같은 객체들의 값도 전송이 가능하다.
    
    
## References
* https://mangkyu.tistory.com/17
