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

