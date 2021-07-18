![이미지 033](https://user-images.githubusercontent.com/64997345/124758412-86bc9c80-df69-11eb-9556-ec3347594abf.png)

- HTTP 전송에 필요한 모든 부가정보
- 메세지 바디의 내용, 바디의 크기, 압축, 인증 요청 클라이언트, 서버 정보, 캐시 관리 정보 등등
- 필요 시 임의의 헤더 추가 가능함.

![이미지 035](https://user-images.githubusercontent.com/64997345/124758553-a5229800-df69-11eb-8637-9661a789413d.png)

[ 과거의 HTTP BODY ]

- 메시지 본문은(message body)은 엔티티 본문 (entity body)을 전달하는데 사용함.
- 엔티티 본문은 요청이나 응답에서 전달할 실제 데이터
- 엔티티 헤더는 엔티티 본문의 데이터를 해석할 수 있는 정보 제공
- 엔티티의 본문이 html, json 등 여러가지 일 수 있어서 엔티티 헤더에 어떤 데이터인지 명시해 주는 것
- 그 외 데이터길이, 압축정보 등등 표기되어있음.

![이미지 036](https://user-images.githubusercontent.com/64997345/124758641-bd92b280-df69-11eb-8b46-c716494d94c7.png)

- 과거에는 엔티티라는 표현을 사용했지만 2014년 개정이후 엔티티 대신 표현이라고 부름



- 이제는 메시지본문을 엔티티 본문이라 하지 않고 페이로드(payload)라고 함.

**[ 표현 ]**

![이미지 037](https://user-images.githubusercontent.com/64997345/124758699-cd11fb80-df69-11eb-99df-7cd117d62ae0.png)

- 메시지본문(페이로드)의 데이터의 형식 압축방식 자연언어 데이터길이 등 이 모든 것들을 표현이라함.

![이미지 039](https://user-images.githubusercontent.com/64997345/124758771-e1ee8f00-df69-11eb-8272-af74408c2363.png)
![이미지 040](https://user-images.githubusercontent.com/64997345/124758818-edda5100-df69-11eb-9ef8-87f4e980f6db.png)

- 표현 데이터에 대한 설명 html, json, image

![이미지 041](https://user-images.githubusercontent.com/64997345/124759278-6f31e380-df6a-11eb-9658-06166555cd58.png)

- 서버에 데이터를 요청해서 받아오는 데이터가 만약에 압축되어있다면 압축정보가 gzip, deflate, identity 무엇으로 압축되어있는지 알아야 확인 가능하니 인코딩 헤더에 명시한 것
- identity는 압축을 안했다는 뜻

![이미지 042](https://user-images.githubusercontent.com/64997345/124758904-05193e80-df6a-11eb-9734-aed3979ead63.png)

- 자연어의 형식을 인코딩 헤더에 명시 한국어인지 영어인지

[ 콘텐츠 네고시에이션 ]

- 클라이언트가 원하는 표현을 달라고 서버에 요청
- 물론 서버가 그에 맞는 표현을 리턴 못할수도있음
- 클라이언트가 선호하는 표현을 요청할 때 4가지가 있다.

[ 협상 헤더 ]

- Accept : 클라이언트가 선호하는 미디어 타입전달 json, html
- Accept-Charset : 클라이언트가 선호하는 문자 인코딩
- Accept-Encodig : 클라이언트가 선호하는 압축 인코딩
- Aceept-Language : 클라이언트가 선호하는 자연언어 인코딩

[ 협상 헤더의 우선순위 ]

- Accept-Language 에는 요청할 때 우선순위를 부여할 수 있다.
- 어떤서버가 독일어, 영어만 지원한다고 했을 때 지원하지 않는 언어의 요청이 온다면 기본값으로 독일어를 주게되어있다.
- 근데 클라이언트는 한국어가 없다면 영어를 원하는데 독일어를 서버가 줄 수 있으니
- 만약에 내가 원하는 언어를 지원하지 않는다면 디폴트값 주지말고 영어를 달라고 요청을 하고 싶을 때 언어 요청의 우선순위를 정하는 것임.

![이미지 018](https://user-images.githubusercontent.com/64997345/126031107-0d65f74a-672a-4c2e-ba2d-6fa752e4716b.png)

[ 전송방식 ]

- Content-Length 단순전송 방식 콘텐츠 바디 그대로 전송
- Content-Encoding 압축 전송 콘텐츠 바디를 압축해서 전송하는 형태 대신 압축을 풀 수 있또록 콘텐츠인코딩 방식을 추가해주어야 함.
- Transfer-Encoding 분할전송 콘텐츠바디를 분할해서 전송하는 방식 주의사항으로는 분할전송할 땐 헤더에 Content-Length를 추가하면 안됨. 분할해서 계속 전송하기에 길이를 예상하기 어렵기 때문임.
- Range, Content-Range 범위전송 컨텐츠바디 전체를 요청하는 것이 아닌 범위를 지정해서 요청하는 방식