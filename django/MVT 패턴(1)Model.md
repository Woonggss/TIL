Model은 데이터베이스를 정의하는 django의 클래스이다. django는 ORM 기법을 사용해서 따로 SQL을 활용하지 않고도 테이블을 클래스로 매핑할 수 있다.

### ORM 기법
ORM은 Object-Relational Mapping의 약자이다. 기존에 웹 프로그래밍을 할 때, 데이터베이스를 접근하려면 직접 SQL 언어로 접근해야 했다. ORM을 활용하면 SQL 언어를 모르더라도 객체(클래스)를 사용해서 데이터를 처리할 수 있는데, ORM이 자동으로 적절한 SQL 구문이나 데이터베이스 API를 호출해오기 때문이다.
### 테이블 정의하기
class 테이블명(models.Model) 과 같이, Model 클래스를 상속받아서 원하는 이름으로 테이블을 정의할 수 있다. Model 클래스의 속성은 테이블의 컬럼에 매핑된다. 예시 코드는 다음과 같다.

```
from django.db import models

class 폰트현황(models.Model):
	폰트이름 = models.CharField(max_length=10)
    	폰트속성 = models.IntegerField
    	...
```
이런 방식으로 정의를 할 수 있다. django는 내부적으로 명령을 SQL 명령을 사용해서 TABLE을 만들어낸다.

### 데이터베이스에 테이블 생성하기
터미널에서 다음 명령어로 테이블을 생성하고 변경사항 반영을 할 수 있다.

```
# 맨 처음에는 테이블 만들기. 테이블이 만들어진 이후에는 변경사항 반영하기 
python manage.py migrate 

# 변경사항 추출하기
python manage.py makemigrations

```
데이터를 입력하고 조작하는 방법에 대해서는 추후에 더 자세히 다룰 예정이다.

#### 참고자료
파이썬 웹 프로그래밍(2018, 김석훈 지음, 한빛미디어)
