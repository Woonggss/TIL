지금까지는 프로젝트 전체의 urlpattern과 templates을 일괄적으로 관리했다. 앱이 다양해지고 연결해야 될 url, template이 많아지면 깔끔하게 관리할 수 없게 된다. url과 template을 관리하는 방법을 알아보자.

### URL 관리하기
각 앱 폴더의 하위에 urls.py 파일을 작성해주고, 전체 프로젝트의 urls.py 파일에서 path('', include('앱이름.urls'))을 추가해준다. 이러면 [프로젝트 URL]/~ 으로 요청이 왔을 때 해당 앱 폴더의 url으로 연결하라는 뜻이다.아래는 전체 프로젝트 urls.py 파일의 예시 코드이다.

```
from django.contrib import admin
from django.urls import path, include
from main import views

urlpatterns = [
    path('admin/', admin.site.urls),
    path('', include('main.urls')),
]
```

앱 단위로 관리해주면 url 이름이 겹쳐서 헷갈리는 경우도 방지할 수 있다. 다음과 같이 app_name을 지정하고, url마다 name 변수를 설정해준다. 이후 template에서 url 부분을 % url app_name : name % 의 형식으로 URL을 바꿔주면 된다.


```
app_name = 'main'

urlpatterns = [
    path('',views.index,name='index'
    
    ...
    
]
```

~~~
<form id="form" action="{% url 'main:index' %}" method="post">
~~~

### 템플릿 관리하기
템플릿 관리는 좀 더 간단하다. 각 앱의 하위 폴더로 template을 만들고 html 파일들을 넣어준 다음, views.py의 경로를 [앱 이름]/파일 이름.html 로 바꾸어주면 된다.

```
def index(request):
    
    ...
    
    return render(request, 'main/index.html')
```

또한, 반복되는 부분은 템플릿 상속으로 코드를 줄여줄 수 있다. 반복할 html 문서를 작성하는데, 바뀌는 코드를 집어넣을 부분을 {% block head(속성명) %} ~ {% endblock head(속성명) %}와 같은 방식으로 작성해준다. 이후 각 문서마다에는 저 템플릿 태그를 열고 닫으면서 작성해주고, 맨 위에 {% extends 반복할 문서 %}을 넣어주면 적용된다. 템플릿이라는 이름처럼, PPT 템플릿 적용하는 거랑 똑같다.

#### 참고자료
M.B.I.T 테스트 페이지 만들기! with Django (제주코딩베이스캠프)
