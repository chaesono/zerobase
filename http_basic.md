# 인터넷

**인터넷(Internet)** 이란 전 세계 컴퓨터들을 하나로 연결하는 거대한 통신망을 의미합니다.

월드 와이드 웹(World Wide Web, WWW, W3)은 **인터넷**에 연결된 컴퓨터를 통해 사람들이 정보를 공유할 수 있는 전 세계적인 정보 공간을 말한다. 간단히 웹(Web)이라 부르는 경우가 많다.

# HTTP

**HTTP(Hyper Text Transfer Protocol)** 이란 인터넷에서, 웹 서버와 사용자의 인터넷 브라우저 사이에 문서를 전송하기 위해 사용되는 프로토콜을 말합니다.

- 프로토콜은 특정 기기 사이에서 데이터를 주고 받기 위해 정의하는 규칙입니다.

- Hypertext(하이퍼텍스트)란 웹 페이지를 다른 페이지로 연결하는 링크를 말합니다.

- HTTP는 클라이언트가 요청을 생성하기 위한 연결을 연다음 응답을 받을때 까지 대기하는 전통적인 클라이언트-서버 모델을 따릅니다

- 클라이언트 - 서버 모델은 서비스 요청자인 클라이언트와 서버간 작업을 분리해주는 네트워크 아키텍처입니다.

- HTTP는 무상태 프로토콜이며, 무상태 프로토콜이란 서버가 두 요청간에 어떠한 데이터(상태)도 유지하지 않음을 의미합니다. 쉽게 말해서 서버가 클라이언트를 식별할수 없다는 것을 의미합니다. HTTP는 이러한 문제점을 해결하기 위해 브라우저에서 쿠키라는 것을 저장하여 서버가 클라이언트를 식별할 수 있도록 합니다.(HTTP 헤더항목중 set-cookie)

- HTTP 서버는 기본 포트인 80번 포트에서 서비스 대기 중이며, 클라이언트가 80포트를 사용해 연결하면 서버는 요청에 응답하면서 자료를 전송한다. HTTP는 정보를 텍스트로 주고 받는다. 단순 텍스트를 주고 받기 때문에 네트워크에서 전송 신호를 인터셉트하는 경우 원하지 않는 데이터 유출이 발생할 수 있다.

- 포트란 네트워크 서비스나 특정 프로세스를 식별하는 논리 단위를 뜻합니다.

# HTTPS

**HTTPS** 는 HTTP에 S(Secure Socket)을 추가한 것이다. 기본 골격이나 사용 목적은 HTTP와 거의 동일하지만, 데이터를 주고 받는 과정에 “보안”요소가 추가된다는 것이 가장 큰 차이점이다. 쉽게 말해 HTTPS를 사용하면 서버와 클라이언트 사이의 모든 통신 내용이 암호화된다는 것이다.

HTTPS는 웹 서버에 접속하는 사용자에게 모두 동일한 암호를 제공하는 것이 아니라 사용자 마다 다른 암호를 제공해야 한다.

HTTPS는 암호화와 복호화를 시킬 수 있는 서로 다른 키 2개가 존재할 때 이 2개의 키는 서로 암호화 / 복호화할 수 있다는 규칙을 갖고 있다. 예를들어 A키로 암호화하면 반드시 B키로 복호화할 수 있고, B키로 암호화하면 반드시 A키로 복호화 할 수 있다는 것이다. 그 중 하나의 키는 모두에게 공개키로 공개키 저장소에 등록해 사용하고, 남은 하나의 키를 개인키로 이용해 통신한다. 클라이언트는 공개키를 얻어 데이터를 암호화해서 전송하고, 서버는 개인키를 이용해 복호화한다. 만약 반대로 서버가 정보를 제공하는 경우에는 개인키로 암호화한 정보를 전송하기 때문에 공개키가 있는 사용자는 누구나 정보를 알 수 있다.

---

# HTTP Header

## Header란?

HTTP 헤더는 클라이언트와 서버가 요청 또는 응답으로 부가적인 정보를 전송할 수 있도록 해줍니다.

## 1. HTTP 요청 메시지 구조

1. Start Line(요청내용)

- HTTP 메소드 / Request target / HTTP version

  - HTTP 메소드: 요청의 의도를 말합니다. ex) GET, POST
  - Request target: HTTP 요청이 전송되는 목표 주소
  - HTTP version : version을 명시합니다.

2. Header

- General 헤더
  - 요청과 응답 모두에 적용되지만 바디에서 최종적으로 전송되는 데이터와는 관련이 없는 헤더 입니다.
- Request 헤더
  - 페치될 리소스나 클라이언트 자체에 대한 자세한 정보를 포함하는 헤더입니다.
- Entity 헤더
  - 컨텐츠 길이나 MIME 타입과 같이 엔티티 바디에 대한 자세한 정보를 포함하는 헤더입니다.

3. Body

- HTTP 요청이 전송하는 데이터를 담고 있는 부분입니다. 모든 요청에 본문이 들어가지는 않습니다.

### Request Header 주요 항목

- Host
  - 요청하는 호스트에 대한 호스트명 및 포트번호(필수)
- User-Agent
  - 클라이언트 소프트웨어(브라우저, OS) 명칭 및 버전 정보
- From
  - 클라이언트 사용자 메일 주소
    - 주로 검색엔진 웹 로봇의 연락처 메일 주소를 나타낸다.
      때로는, 이 연락처 메일 주소를 User-Agent 항목에 두는 경우도 있다.
- Cookie
  - 서버에 의해 Set-Cookie로 클라이언트에게 설정된 쿠키 정보
- Referer
  - 바로 직전에 머물렀던 웹 링크 주소
- If-Modified-Since
  - 제시한 일시 이후로만 변경된 리소스를 취득 요청
- Authorization
  - 인증토큰(JWT/Bearer 토큰)을 서버로 보낼 때 사용하는 헤더
  - "토큰의 종류 + 실제 토큰 문자"를 전송
- Origin
  - 서버로 POST 요청을 보낼 때, 요청이 어느 주소에서 시작되었는지 나타낸다.
  - 여기서 요청을 보낸 주소와 받는 주소가 다르면 CORS 에러가 발생한다.
  - 응답 헤더의 Access-Control-Allow-Origin와 관련
- 다음 4개는 주로 HTTP 메시지 Body의 속성 또는 내용 협상용 항목
  - Accept
    - 클라이언트 자신이 원하는 미디어 타입 및 우선순위를 알린다
      - 텍스트, 이미지 등
    - Ex) `Accept: */*`
      - 어떤 미디어 타입도 가능하다.
    - Ex) `Accept: image/*`
      - 모든 이미지 유형이 가능하다
  - Accept-Charset
    - 클라이언트 자신이 원하는 문자 집함
  - Accept_Encoding
    - 클라이언트 자신이 원하는 문자 인코딩 방식
  - Accept-Language
    - 클라이언트 자신이 원하는 가능한 언어

예시)

```
GET /home.html HTTP/1.1
Host: developer.mozilla.org
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10.9; rv:50.0) Gecko/20100101 Firefox/50.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/ *;q=0.8
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate, br
Referer: https://developer.mozilla.org/testpage.html
Connection: keep-alive
Upgrade-Insecure-Requests: 1
If-Modified-Since: Mon, 18 Jul 2016 02:36:04 GMT
If-None-Match: "c561c68d0ba92bbeb8b0fff2a9199f722e3a621a"
Cache-Control: max-age=0
```

```
POST /myform.html HTTP/1.1
Host: developer.mozilla.org
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10.9; rv:50.0) Gecko/20100101 Firefox/50.0
Content-Length: 128
https://gmlwjd9405.github.io/2019/01/28/http-header-types.html
```

## 2. HTTP 응답 메세지 구조

1. Status Line

- HTTP version / Status Code / Status Text
  - Status Code 는 응답상태를 나타내는 코드입니다. (ex. 200, 400, 404)
- Status Text
  - 응답 상태를 간략하게 글로 설명해줍니다.

2. Header

- General 헤더
  - 요청과 응답 모두에 적용되지만 바디에서 최종적으로 전송되는 데이터와는 관련이 없는 헤더 입니다.
- Response 헤더
  - 위치 또는 서버 자체에 대한 정보(이름, 버전 등)와 같이 응답에 대한 부가적인 정보를 갖는 헤더입니다.
- Entity 헤더
  - 컨텐츠 길이나 MIME 타입과 같이 엔티티 바디에 대한 자세한 정보를 포함하는 헤더입니다.

3. Body

- HTTP 요청 메시지의 body와 동일합니다.
- 전송하는 데이터가 없으면 비어 있습니다.

### Response header 주요 항목

- Server
  - 서버 소프트웨어 정보
- Accept-Range
- Set-Cookie
  - 서버측에서 클라이언트에게 세션 쿠키 정보를 설정
- Expires
  - 리소스가 지정된 일시까지 캐시로써 유효함을 나ㅏ낸다. 즉, 응답컨텐츠가 언제 만료되는지를 나타낸다.
  - Ex) `Expires: Fri, 11 Sep 2020 13:29:00 GMT`
- Age
  - 캐시 응답. max-age 시간 내에서 얼마나 흘렀는지 초 단위로 알려준다.
- ETag
  - HTTP 컨텐츠가 바뀌었는지를 검사할 수 있는 태그
- Proxy-authenticate
- Allow
  - 해당 엔티티에 대해 서버 측에서 지원 가능한 HTTP메소드의 리스트를 나타낸다
  - 때론, HTTP 요청 메세지의 HTTP 메소드 OPTIONS에 대한 응답용 항목으로 사용된다.
    - OPTIONS: 웹서버측 제공 HTTP 메소드에 대한 질의
  - EX) `Allow: GET,HEAD`
    - 405 Method Not Allowed 에러와 함께
    - 웹 서버에서 제공 가능한 HTTP 메소드는 GET, HEAD뿐임을 알린다.
- Access-Control-Allow-Origin
  - 요청을 보내는 프론트 주소와 받는 백엔드 주소가 다르면 CORS 에러가 발생
    - 서버에서 이 헤더에 프론트 주소를 적어주어야 에러가 나지 않는다.
  - Ex) `Access-Control-Allow-Origin: www.naver.com`
    - 프로토콜, 서브도메인, 도메인, 포트 중 하나만 달라도 CORS 에러가 난다.
  - Ex) `Access-Control-Allow-Origin: *`
    - 만약 주소를 일일이 지정하기 싫다면 \*으로 모든 주소에 CORS 요청을 허용되지만 그만큼 보안이 취약해진다.
  - 유사한 헤더로 `Access-Control-Request-Method, Access-Control-Request-Headers, Access-Control-Allow-Methods, Access-Control-Allow-Headers` 등이 있다.

예시)

```
200 OK
Access-Control-Allow-Origin: *
Connection: Keep-Alive
Content-Encoding: gzip
Content-Type: text/html; charset=utf-8
Date: Mon, 18 Jul 2016 16:06:00 GMT
Etag: "c561c68d0ba92bbeb8b0f612a9199f722e3a621a"
Keep-Alive: timeout=5, max=997
Last-Modified: Mon, 18 Jul 2016 02:36:04 GMT
Server: Apache
Set-Cookie: mykey=myvalue; expires=Mon, 17-Jul-2017 16:06:00 GMT; Max-Age=31449600; Path=/; secure
Transfer-Encoding: chunked
Vary: Cookie, Accept-Encoding
X-Backend-Server: developer2.webapp.scl3.mozilla.com
X-Cache-Info: not cacheable; meta data too large
X-kuma-revision: 1085259
x-frame-options: DENY
```

---

# Requested Url

- URL

  - URL이란 Uniform Resource Locators의 약자로 인터넷에 접속할 때, 네트워크 상에서 해당자원이 어디에 위치해있는지를 알려주는 문자열 입니다.

  - URL은 `"protocol://host.domain[:port]/path/filename"`와 같은 형식으로 구성된다.
