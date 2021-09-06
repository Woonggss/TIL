### 메타 태그로 공유 시 미리보기 화면 설정
메타 태그를 활용하면 공유할 때, 미리보기 카드가 뜨게 만들 수 있다. opengraph 속성을 활용해주면 되는데, 예시 코드는 다음과 같다.

```
<meta property="og:title" content="" />
<meta property="og:image" content="" />
<meta property="og:url" content="" />
<meta property="og:description" content="" />
```
title, image, url, description에 각자 원하는 내용을 집어넣고, html 문서의 head 속성 안에 붙여넣으면 사용할 수 있다.

강의 들을 때 보니까, 메타 태그로 검색어 추적도 가능하게 해주는 것 같다. 
```
<meta name="Keywords" content="" />
<meta name="Description" content="" />
```
Keyword에는 검색 엔진에서 검색할 때 사용할 수 있는 단어들을 넣어주고, Description에는 검색 결과에 표시되는 문자를 지정한다. 이 밖에도 다양한 meta 속성이 있음을 확인했다. 참고 자료의 사이트로 가면 확인할 수 있다.

#### 참고 자료
https://webclub.tistory.com/354 메타(meta) 태그 정리
