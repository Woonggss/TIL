### Application : 웹을 구성하는 단위
일반적으로 application은 웹에서 프로그램으로 코딩할 대상을 의미한다. 그러나 django에서는 application을 좀 더 구체화하여 사용하고 있다. 웹 사이트에 대한 전체 프로그램을 project라고 지칭하고, project를 구성하는 모듈화 된 단위 프로그램을 application이라고 부른다.

즉, django로 웹 사이트를 개발할 때, application이라는 기능 단위로 쪼개서 개발을 하게 된다. 만들어서 조립하는 느낌으로 이해하면 될 것 같다.

### MVT 패턴
django에서는 application을 개발할 때 MVT 패턴을 따라서 개발한다. 일반적으로는 MVC 패턴이라고 해서, 데이터(Model)와 사용자 인터페이스(View), 데이터를 처리하는 로직(Controller)을 구분해서 상호간에 영향을 주지 않도록 개발해서, 합칠 수 있도록 하는 패턴으로 웹을 개발한다. 

django에서는 같은 방식을 채택하고 있는데, 용어만 MVT로 바뀐 것이다. 데이터(Model), 데이터를 처리하는 로직(View), 사용자 인터페이스(Templete)으로 구성된다.

![](https://images.velog.io/images/woongss/post/a658f6c2-61c1-485a-ada5-a2d66d6143de/image.png)

(장고의 애플리케이션 개발 프로세스)

#### 참고자료
파이썬 웹 프로그래밍(2018, 김석훈 저, 한빛미디어)
