### django에서 정적 파일 사용하기
HTML 문서를 작성하면 css, javascript, 이미지 등의 정적 요소들을 추가하게 된다. django에서는 정적 파일들은 따로 지정된 경로에 넣어주어야 사용할 수 있다. 

settings.py의 STATIC_URL에 경로가 있는데, 초기값은 보통 STATIC_URL = '/static/' 으로 지정되어 있다. 따로 수정하지 않는다면, 정적 파일들은 모두 (프로젝트 경로)/static/에 넣고 사용해야 한다.

### {% load static %}
static 요소들은 해당 HTML 문서에서 템플릿 태그로 불러서 사용해야 한다. 문서의 맨 위에 {% load static %}을 넣어주고, 경로에 "{% static 'css/reset.css' %}"와 같은 형식으로 static을 불러줘야 한다. 아래는 예시이다.
![](https://images.velog.io/images/woongss/post/3ca3c763-a76a-4b01-bffb-d17aeecc5f5d/image.png)

#### 참고자료
<M.B.I.T> 테스트 페이지 만들기! With Django (제주코딩베이스캠프)
