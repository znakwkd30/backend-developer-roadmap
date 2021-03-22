## HTTP란
HTTP란 HyperText Transfer Protocol은 텍스트 기반의 통신 규약으로 W3 상에서 정보를 주고받을 수 있는 프로토콜이다. 주로 HTML 문서를 주고 받는 데에 쓰인다. 주로 TCP를 사용하고 HTTP/3 부터는 UDP를 사용하며, 80번 포트를 사용한다.  
HTTP는 클라이언트와 서버 사이에 이루어지는 요청/응답(request/response) 프로토콜이다. 예를 들면, 클라이언트인 웹 브라우저가 HTTP를 통하여 서버로부터 웹페이지(HTML)나 그림 정보를 요청하면, 서버는 이에 응답하여 필요한 정보를 해당 사용자에게 전달하게 된다.

## HTTP의 역사
하이퍼텍스트라는 용어는 1965년 제너두 프로젝트에서 테드 넬슨이 만들었으며, 팀 버니스 리와 그의 팀은 CERN에서 HTML뿐 아니라 웹 브라우저 및 텍스트 기반 웹 브라우저 관련 기술과 더불어 오리지널 HTTP을 발명하였다. 버니스 리는 최초로 "월드 와이드 웹" 프로젝트를 1989년에 제안하였으며, 이것이 현재의 월드 와이드 웹이다. 이 프로토콜의 최초 버전은 서버로부터 페이지를 요청하는 GET이라는 이름의 하나의 메소드만 있었다. 서버로부터의 응답은 무조건 HTML 문서였다.  
문서화된 최초의 HTTP 버전은 HTTP V0.9이다. 데이브 레겟은 1995년 HTTP 워킹 그룹(HTTP WG)을 이끌었으며 확장된 조작, 확장된 협상, 더 보강된 메타 정보 또 추가 메소드와 헤더 필드를 통한 더 효율적인 보안 프로토콜을 갖춘 프로토콜로 확장하기를 바랐다. RFC 1945는 공식적으로 1996년 HTTP V1.0을 도입하였다. RFC 2068에 정의된 HTTP/1.1 표준은 공식적으로 1997년 1월에 출시되었다. HTTP/1.1 표준에 대한 개선과 업데이트는 1999년 6월에 RFC 2616으로 출시되었다.  
2007년에 부분적으로 HTTP/1.1 사양을 개정하고 분명히 하기 위해 HTTPbis 워킹 그룹이 창설되었다. 2014년 6월, WG는 RFC 2616를 obsolete 처리하는, 업데이트된 6 파트 사양을 출시하였다.
- RFC 7230, HTTP/1.1 : Message Syntax and Routing
- RFC 7231, HTTP/1.1 : Sematics and Content
- RFC 7232, HTTP/1.1 : Conditional Requests
- RFC 7233, HTTP/1.1 : Message Range Requests
- RFC 7234, HTTP/1.1 : Caching
- RFC 7235, HTTP/1.1 : Authentication

## HTTP 특징
- HTTP 메시지는 HTTP 서버와 HTTP 클라이언트에 의해 해석된다.
- TCP/IP를 이용하는 응용 프로토콜이다.
- HTTP는 연결 상태를 유지하지 않는 프로토콜이다.
- HTTP는 연결을 유지하지 않는 프로토콜이기 때문에 요청/응답 방식으로 동작한다.  
![image](https://media.vlpt.us/post-images/surim014/e0aa5520-2d59-11ea-86da-fb3b00230640/image.png)

## Request (요청)
클라이언트가 서버에게 연락하는 것을 요청이라고 하며, 요청을 보낼때는 요청에 대한 정보를 담아 서버로 보낸다.

### Request Method (요청의 종류)
- GET : 데이터를 요청할 때 사용
- POST : 데이터를 생성할 때 사용
- PUT : 데이터를 수정할 때 사용
- DELETE : 데이터를 삭제할 때 사용

### Request HTTP 메시지 예시
```
GET https://... HTTP/1.1 // 시작줄
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) ... // 헤더
Upgrade-Insecure-Requests: 1
```
1. 시작줄 (첫 줄)  
첫 줄은 시작줄로 메서드 구조 버전으로 구성되었다.
- GET : HTTP Method
- https://... : 사이트 주소
- HTTP/1.1 : HTTP 버전
1. 헤더 (두 번째 줄부터)  
두번째 줄부터는 헤더이며, 요청에 대한 정보를 담고 있다.
3. 본문 (헤더에서 한 줄 띄고)  
본문은 요청을 할 때 함께 보낼 데이터를 담는 부분이다.

## Response (응답)
서버가 요청에 대한 답변을 클라이언트에게 보내는 것을 응답이라 한다.

### Status Code (상태 코드)
상태 코드에는 굉장히 많은 종류가 있고, 모두 숫자 세 자리로 이루어져있습니다. 아래처럼 크게 다섯 부류로 나눌 수 있습니다.
- 1xx (조건부 응답) : 요청을 받았으며, 작업을 계속 한다.
- 2xx (성공) : 클라이언트가 요청한 동작을 수신하여 이해했고 승낙했으며, 성공적으로 처리했음을 가리킨다.
- 3xx (리다이렉션 완료) : 클라이언트는 요청을 마치기 위해 추가 동작을 취해야 한다.
- 4xx (요청 오류) : 클라이언트에 오류가 있음을 나타낸다.
- 5xx (서버 오류) : 서버가 유효한 요청을 명백하게 수행하지 못했음을 나타낸다.  

더 상세한 상태 코드를 보고싶으면 [HTTP 상태코드](https://ko.wikipedia.org/wiki/HTTP_%EC%83%81%ED%83%9C_%EC%BD%94%EB%93%9C)를 참고해주세요.

### Response HTTP 메시지 예시
```
HTTP/1.1 200 OK
Connection: keep-alive
Content-Encoding: gzip
Content-Length: 35653
Content-Type: text/html;

<!DOCTYPE html><html lang="ko"><head><title>...
```
1. 시작줄 (첫 줄)  
첫 줄은 버전 상태 코드 상태 메시지로 구성되어 있다. 200은 성공적인 요청이란 뜻.
2. 헤더 (두 번째 줄부터)  
두 번째 줄부터는 헤더로 응답에 대한 정보를 담고 있다.
3. 본문 (헤더 뒤부터)  
보통 데이터를 요청하고 응답 메시지는 요청한 데이터를 담아서 보내주기 때문에 대부분의 경우에 본문이 있음.

## 참고 자료📚
- [HTTP, wikipedia](https://ko.wikipedia.org/wiki/HTTP)
- [HTTP란 무엇인가?, velog](https://velog.io/@surim014/HTTP%EB%9E%80-%EB%AC%B4%EC%97%87%EC%9D%B8%EA%B0%80)