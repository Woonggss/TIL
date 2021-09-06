### 사이트가 보여지는 원리
![](https://images.velog.io/images/woongss/post/abc121f4-d6d4-43d1-946f-d251694cabfa/image.png)

Client가 웹에서 URL 요청을 보내면, URL/View 매칭을 한다. 이후 View에서 Template을 rendering하고, Model에서 데이터베이스를 조작하거나 요청된 데이터를 가져온다.
### URLConf
URL과 View를 매칭하는 과정을 URLConf라고 한다. django에서는 urls.py라는 파일에 urlpatterns라는 url list에서 사용자가 요청한 url과 매칭이 되는 url이 있는지를 확인한다. url이 있다면, 매칭이 된 view의 함수를 실행시킨다. view를 모듈로 불러온 다음 적용해주면 된다. 예시 코드는 다음과 같다.

```
from django.contrib import admin
from django.urls import path
from main import views

urlpatterns = [
    path('admin/', admin.site.urls),
    path('', views.index),
    path('form/', views.form),
]
```

### View
View는 웹 사이트의 로직을 정의한다. 요청을 받으면, View에 설계된 대로 template에 저장된 사이트를 띄우고 DB의 내용을 조작하고 가져온다. views.py에 코딩하면 된다. DB 내용을 임의의 변수에 담고, context라는 변수에 dict 타입으로 담으면 적용할 수 있다.(django에서는 dict 타입을 많이 활용한다. 그러나 파이썬의 dict 자료형을 온전히 가져온 것 같지는 않다.) 이후 render를 return해서 사이트를 띄운다. render의 사용법은 예시 코드를 직접 보는 게 이해가 빠르다. 예시 코드는 다음과 같다. 

```
from django.shortcuts import render
from .models import Developer

def index(request):
    developers = Developer.objects.all()
    
    context = {
        'developers' : developers,
    }
    
    return render(request, 'index.html', context=context)
```
### Template
템플릿은 앱 폴더 아래에 templates라는 폴더를 만들어주어야 한다(규칙이다). 그 안에 내가 사용자에게 띄워줄 페이지를 넣으면 된다. 페이지를 디자인하는 것은 프론트의 영역이니 자세한 설명은 생략한다. 이제 Template의 내용에 DB 내용을 어떻게 뿌려줄 것인지 아는 것이 중요한데, 다음 글에서 다뤄보겠다.

#### 참고자료
파이썬 웹 프로그래밍(2018, 김석훈 지음, 한빛미디어)
