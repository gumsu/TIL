# 네트워크
## 웹 브라우저에 URL을 입력하면 일어나는 일
1. `www.naver.com` 을 검색한다.
2. DNS lookup 을 수행한다.
   -  브라우저 -> hosts 파일 -> DNS cache 순서로 도메인에 매칭되는 ip 를 찾는다.
   -  hosts 파일을 찾아본다.
   -  없다면 DNS cache 기록을 확인한다.
   -  없다면 DNS 서버에 질의를 하고, 응답을 얻어 ip 주소를 획득한다. (GSLB, CDN)
3. naver 서버에 tcp 연결을 시도한다. (3-way handshaking)
4. tcp 연결에 성공하면 http request 를 보낸다. (GET)
5. http response 응답을 받는다.
6. 브라우저가 컨텐츠를 보여준다.

### CDN, GSLB를 사용하는 이유?
- 가장 최적의 서버 환경을 찾아 클라이언트의 대기시간을 줄이기 위해 사용한다.
- CDN (Content Delivery Network)
  - 전 세계에 분산되어 있는 네트워크를 말한다. 각 세계에 서버가 퍼져있기 때문에 지연 시간을 감소시켜 요청/응답을 빠르게 받을 수 있다.
- GSLB (Global Server Load Balance)
  - 클라이언트가 컨텐츠 요청이 있는 경우 가장 최적의 서버를 찾아주는 역할을 한다.
  - 서버가 살아있는지 실시간으로 상태를 확인 `(health check)` 하여 정상적으로 동작하는 ip를 응답한다.

## URL vs. URI vs. URN
- URL은 Location 으로 리소스를 구분하며 일반적인 도메인을 의미한다.
- URI은 Identifier 으로 식별자를 구분하며 수신하는 기기에 맞게 반환한다. (tel:010)
- URN은 자원의 name 으로 구분하며, 리소스 자체에 부여된 영구적이고 유일한 이름이다.

## http 의 무상태성과 비연결성
- 서버와 클라이언트의 연결 상태가 유지되지 않고, 상태 정보를 저장하지 않는다.
- 단점 -> 사용자를 식별할 수 없다. 이를 해결하기 위해 쿠키와 세션을 사용한다.
