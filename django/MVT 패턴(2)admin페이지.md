### admin 페이지에 model 반영해주기
model에 만들어진 데이터베이스는 admin 페이지에 반영해주어야 한다. models.py에 만들었으므로 모듈에서 import하는 방식으로 불러올 수 있으며, admin.site.register()으로 등록해주면 된다. 예시 코드는 다음과 같다. 여기서는 Developer, Quetion, Choice라는 클래스(테이블)을 등록해주었다.

```
from django.contrib import admin
from .models import Developer, Question, Choice

admin.site.register(Developer)
admin.site.register(Question)
admin.site.register(Choice)
```
### 터미널에서 admin 등록하기
``` 
python manage.py createsuperuser
```
다음의 코드로 사용자 이름, e-mail, password를 등록하면 된다. admin 페이지에 접속하면 등록한 DB가 보인다.

### DB의 이름을 바꾸기
models.py에서 class마다 (dunder)str(dunder) def를 주면, 대표로 뜨는 이름을 설정할 수 있다. 예시 코드는 다음과 같다.

```
class Example(models.Model):
    name = models.CharField(max_length=5)
    number = models.IntegerField(default=0)
    
    def __str__(self):
        return self.name
```

#### 참고자료
파이썬 웹 프로그래밍(2018, 김석훈 지음, 한빛미디어)
