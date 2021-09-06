### Redirect
Redirect는 브라우저에게 특정 페이지로 이동하게끔 요청한다. 여태껏 활용했던 render가 html 파일을 띄워준다는 것과는 다르다. django.shortcuts에서 redirect 메소드를 불러와야 쓸 수 있다. views.py에서 다음과 같이 사용할 수 있다.
```
from django.shortcuts import render, redirect

def redirect_to_page(request) :
	
    함수 내용
    
    #arg1, arg2 에는 넘겨줄 변수 등이 들어간다
    
    return redirect(urlpattern, arg1, arg2 , ..)
```

Redirect는 form 형식을 제출할 때 유용하게 활용될 수 있다. form page에서 제출을 하고 바로 결과 페이지로 넘어가게 하면, 새로고침을 할 때 마다 제출까지 함께 실행이 되어 중복 카운트가 되어버린다. 제출 -> redirect -> 결과 페이지를 거침으로써 제출하는 행위를 실행했던 내역에서 지워줄 수 있다. 웹 브라우저는 한 번에 한 개의 실행 내역만 기억하기 때문이다.

### URL 인자
Redirect는 context로 변수를 넘겨줄 수 없다. 그래서 url argument를 이용해야 한다. 먼저, urls.py에 다음과 같은 형식으로 추가해준다.
```
urlpatterns = [
	
    ...
    #int형으로 class_id 값을 받을 수 있다는 의미이다.
    path('result/<int:class_id>', views.result),
]
```
해당 예시는 result 함수로 이동하는 예시이다. result 함수에 class_id라는 인자를 받을 수 있게 추가해주고, redirect를 쓰는 함수에는 class_id 값을 지정해주면 된다. 저 class_id라고 쓰인 자리에는 그냥 해당 함수 내에서 만들어 준 다른 int형 변수가 들어와도 된다. redirect는 그냥 페이지를 이동만 시켜주기 때문이다.

```
def result(request, class_id):
...


```

이 코드는 result 함수의 예시이고, 다음은 redirect를 return하는 함수의 예시이다.

~~~
return redirect(f'/result/{class_id}')
~~~

두 번째 코드의 {class_id}라고 쓰인 자리에는 그냥 해당 함수 내에서 만들어 준 다른 int형 변수가 들어와도 된다. redirect는 그냥 페이지를 이동만 시켜주기 때문이다.

#### 참고자료
M.B.I.T 테스트 페이지 만들기! With Django (제주코딩베이스캠프)
