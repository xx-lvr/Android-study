## OkHttp
**OkHttp**는 Square에 의해 개발된 오픈 소스 HTTP 클라이언트 라이브러리이다. 
+ REST API 및 서버와 HTTP 기반의 클라이언트의 요청과 응답에 편의성 제공을 위한 목적으로 개발되었다.
+ 이 라이브러리는 **Connection pooling**과 **Redirection**을 도입해 접속을 더 안정적이게 하면서도, 속도를 개선시킬 수 있는 여러가지 기술이 적용되었다.

## 특징
+ **Okio와**와 **코틀린**으로 구성되어있다.
+ **Connection pooling**과 **Redirection**을 도입해 더 안정적이고 개선된 속도로 HTTP 통신을 가능하게 한한다.
+ OkHttp는 통신을 동기화로할지 비동기 처리로할지 선택할 수 있다, 하지만 스레드를 넘나들 수 없으므로 Handler를 사용한다.