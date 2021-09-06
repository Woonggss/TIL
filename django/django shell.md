### django shell
앞서 django에서는 admin page에서 DB를 관리한다고 했다. admin page의 GUI로 데이터를 생성,조회,변경,삭제하면 편리하기는 하나, 커맨드로 더 복잡한 작업을 빠르게 하고 싶을 수도 있다. 이럴 때 django shell을 활용할 수 있다. django shell에서는 ORM을 포함한 일반 파이썬 문법을 활용할 수 있어 유용하게 쓸 수 있다. 참고로 django에서 models.py에 DB를 설계할 때도 그랬듯, 테이블을 클래스로 표현한다.
### 실행하기
```python
python manage.py shell
```
을 입력하면 실행할 수 있다. 이후 필요한 모듈을 import하고 원하는 동작을 입력하면 된다. 

모듈을 일일이 불러오는 것이 귀찮다면, django-extensions을 설치하고 shell_plus를 이용하면 필요한 모듈을 미리 다 불러놓는다.
```python
pip install django-extensions
python manage.py shell_plus
```
settings.py의 INSTALLED_APPS 에 django_extensions을 꼭 추가해줘야 한다.
![](https://images.velog.io/images/woongss/post/da611411-c89f-4bc1-9023-deca3c53da40/image.png)

django-extension이 아닌 django_extensions라는 점에 주의해야 한다.
### Create - 데이터 생성/입력
데이터를 입력하는 방법은 필드값을 지정해서 객체를 생성한 이후, save() 메소드를 호출하면 된다.
```
from main.models import Question

q = Question(question_text = "What's your choice?")
q.save()
```
### Read - 데이터 조회
데이터베이스로부터 테이블을 조회하기 위해서는 QuerySet 객체를 활용한다. Question.objects.~~ 형태로 쓰면 되고, objects 까지는 '테이블의 레코드들' 이라고 해석하면 된다. ~~ 자리에 들어가는 메소드 중 자주 쓰이는 것들은 다음과 같다.
* all() : 객체 전부 가져오기
* filter() : 조건에 맞는 객체들 가져오기
* exclude() : 괄호 안 조건의 객체들은 제외하고 가져오기
* get(pk=n) : 'id=n'인 요소 가져오기

전부 QuerySet 객체를 돌려주기 때문에, 체인식 호출(연달아서 .찍고 쓰는 것)이 가능하다. 또한 all()로 불러온 QuerySet은 리스트 슬라이싱이 가능한데, 이 경우 리스트 객체를 돌려준다는 점은 유의해야 한다.
### Update - 데이터 수정
필드 속성값을 수정하고 save() 메소드를 호출하면 된다.
```
q.question_text = "Revised Question"
q.save()
```
또한 여러 객체를 한 번에 수정할수도 있는데, update() 메소드를 사용한다.
```
Question.objects.filter(pub_date__month=Jul).update(question_text='Every choice is the same')
```
### Delete - 데이터 삭제
객체를 지정하고 .delete() 메소드를 붙이면 해당 데이터를 지울 수 있다. 주의할 점은 django에서는 Question.objects.all.delete()는 사용할 수 없다는 점인데, all을 사용할 수 없게 만듦으로써 데이터를 전부 지워버리는 실수를 줄이기 위함이다.
```
Question.objects.filter(pub_date__month=Jul).delete()
```

#### 참고자료
파이썬 웹 프로그래밍 (2018, 김석훈 지음, 한빛미디어)
<M.B.I.T> 테스트 페이지! With Django (제주코딩베이스캠프)
