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

### CDN. GSLB를 사용하는 이유?
- 가장 최적의 서버 환경을 찾아 클라이언트의 대기시간을 줄이기 위해 사용한다.
- CDN (Content Delivery Network)
  - 전 세계에 분산되어 있는 네트워크를 말한다. 각 세계에 서버가 퍼져있기 때문에 지연 시간을 감소시켜 요청/응답을 빠르게 받을 수 있다.
- GSLB (Global Server Load Balance)
  - 클라이언트가 컨텐츠 요청이 있는 경우 가장 최적의 서버를 찾아주는 역할을 한다.
  - 서버가 살아있는지 실시간으로 상태를 확인 `(health check)` 하여 정상적으로 동작하는 ip를 응답한다.
