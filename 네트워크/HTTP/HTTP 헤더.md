![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/f364b40e-81ba-423e-835a-cd20dbab6e4b/_033.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/f364b40e-81ba-423e-835a-cd20dbab6e4b/_033.png)

- HTTP 전송에 필요한 모든 부가정보
- 메세지 바디의 내용, 바디의 크기, 압축, 인증 요청 클라이언트, 서버 정보, 캐시 관리 정보 등등
- 필요 시 임의의 헤더 추가 가능함.

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/448a729a-aedb-4522-9208-b2d2c0c83290/_035.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/448a729a-aedb-4522-9208-b2d2c0c83290/_035.png)

[ 과거의 HTTP BODY ]

- 메시지 본문은(message body)은 엔티티 본문 (entity body)을 전달하는데 사용함.
- 엔티티 본문은 요청이나 응답에서 전달할 실제 데이터
- 엔티티 헤더는 엔티티 본문의 데이터를 해석할 수 있는 정보 제공
- 엔티티의 본문이 html, json 등 여러가지 일 수 있어서 엔티티 헤더에 어떤 데이터인지 명시해 주는 것
- 그 외 데이터길이, 압축정보 등등 표기되어있음.

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/b5828490-6c3f-4ec9-ab23-c6e2421abb8c/_036.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/b5828490-6c3f-4ec9-ab23-c6e2421abb8c/_036.png)

- 과거에는 엔티티라는 표현을 사용했지만 2014년 개정이후 엔티티 대신 표현이라고 부름

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/6eb19a8b-4725-4874-9e5a-766bf9e2de73/_037.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/6eb19a8b-4725-4874-9e5a-766bf9e2de73/_037.png)

- 이제는 메시지본문을 엔티티 본문이라 하지 않고 페이로드(payload)라고 함.

**[ 표현 ]**

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/5a0839b4-e9fa-4249-a2f5-470679e87a54/_039.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/5a0839b4-e9fa-4249-a2f5-470679e87a54/_039.png)

- 메시지본문(페이로드)의 데이터의 형식 압축방식 자연언어 데이터길이 등 이 모든 것들을 표현이라함.

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/9d5d8b18-e1f8-40fc-aae2-15fb254807df/_040.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/9d5d8b18-e1f8-40fc-aae2-15fb254807df/_040.png)

- 표현 데이터에 대한 설명 html, json, image

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/f1c382f8-f8d4-419a-a775-5ea33f5d9ce4/_041.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/f1c382f8-f8d4-419a-a775-5ea33f5d9ce4/_041.png)

- 서버에 데이터를 요청해서 받아오는 데이터가 만약에 압축되어있다면 압축정보가 gzip, deflate, identity 무엇으로 압축되어있는지 알아야 확인 가능하니 인코딩 헤더에 명시한 것
- identity는 압축을 안했다는 뜻

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/6071096c-5c92-47a9-8b8c-e728141fd853/_042.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/6071096c-5c92-47a9-8b8c-e728141fd853/_042.png)

- 자연어의 형식을 인코딩 헤더에 명시 한국어인지 영어인지