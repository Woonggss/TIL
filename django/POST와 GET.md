클론 코딩을 하는데 자꾸 POST가 눈에 보여서 어떤 개념인지 궁금해서 찾아보았고, POST와 GET에 대해 공부하게 되었다.

### 클라이언트와 서버 간의 상호작용
설문조사 페이지와 같은 경우, 클라이언트와 서버는 정보를 주고 받게 된다. POST와 GET은 각각 http에서 활용되는, 7가지 규약에 속해있는 방법 중 하나이다.
### GET : 더 빠르지만 보안이 취약하다
GET 방식은 사용자의 정보가 URL에 담겨서 전송된다. URL 뒤에 parameter를 붙여서 전송하는 방식인데, (http://)해당 url?parameter:value 와 같은 방식으로 전송이 된다. 한 번에 전송할 수 있는 데이터가 제한적이다. 또한 정보가 URL에 노출되어서 보안에 취약하다는 문제점이 있다.

### POST : 대용량 데이터 전송이 가능하며 보안성이 확보되었다.
POST 방식은 사용자의 정보가 body태그에 숨겨져서 전송된다. 주고 받는 데이터의 크기에 제한이 없다. 한편, django에서는 {% csrf_token %}을 적어서 csrf 공격을 방지한다. 

### request.POST : 사용자에게 POST 형태로 전달받은 데이터를 담은 객체
![](https://images.velog.io/images/woongss/post/637ca434-c3b0-4d69-b02c-e708e13d90c5/image.png)
QueryDict 부분부터가 request.POST로 받아온 부분이다. 맨 처음은 전달받은 데이터를 설명하는 부분이고, 그 다음이 코딩할 때 관심 가져야 되는 데이터의 콘텐츠이다. dictionary 형태이므로 key로 접근해서 슬라이싱 하면 된다.
#### 참고자료
https://eveningdev.tistory.com/12 [django] 장고 GET, POST 메서드 실습
