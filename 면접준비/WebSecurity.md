### 💜 웹사이트 보안 공격
#### 🎈 XSS(Cross Site Scripting)
- 웹페이지에 악성 스크립트를 삽입하는 형태의 공격
- 사용자 입력값에 대한 검증 및 필터링을 확실하게 하거나,
- `< script>` 같은 태그를 못쓰게 막아두거나,
- 네이버 등에서 제공하는 lucy 필터를 사용
  
#### 🎈 CSRF(Cross Site Request Fergery)
- 로그인 한 사용자의 세션을 재사용해 서버에 가짜 요청을 보냄
- 특정 동작을 일으키는 uri에 대해 알아내어 자동으로 로그인 되어 있는 사이트를 통해 특정 동작을 일으키는 스크립트를 심어 넣음
- 요청은 Post 방식으로 할것!! => 하이퍼링크로 공격 못함
- 같은 도메인 상에서 들어오는 요청만 허용하거나,
  - [protocol][host][port]가 같으면 같은 출처라고 판단
  - 예: https://localhost:8080
- CSRF 토큰 사용
  - 로그인 시 csrf 토큰 생성하여 세션에 저장, 
  - 사용자는 form submit에 대한 요청에 input hidden 으로 토큰을 함께 보내어 서버에서 검증

### 💜 CORS(Cross Origin Resource Sharing)
- 지정된 도메인 외부에 있는 리소스에 대한 엑세스 제어
- 브라우저는 SOP(Same Origin Policy)를 통해 다른 Origin의 리소스에 대해서 접근을 금지하도록 함
- Origin : [protocol][host][port] 로 구성되어있고, 이 세가지가 모두 같아야 같은 출처
- 해결방법
  - 서버에서 응답 헤더에 `Access-Control-Allow-Origin` 등의 정보를 포함하는 방식으로 해결
  - ex: 스프링에서 addCorsMappings 사용, 리액트에서 "proxy" : "http://localhost:8080" 추가, 플라스크에서 `from flask_cors import CORS` 

#### 🎈 참조블로그
- [port Swigger](https://portswigger.net/web-security)
- [Brouk's devlog](https://brouk-devlog.netlify.app/programming/websecurity_(CORS+XSS+CSRF)/)
- [Evans Library](https://evan-moon.github.io/2020/05/21/about-cors/)

