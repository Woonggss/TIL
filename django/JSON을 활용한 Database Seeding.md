### DB를 통으로 처리할 순 없을까?
django shell 이나 admin page 모두 편리하긴 하지만, 데이터를 일일이 반영해줘야 하는 번거로움이 있다. 이 때 dumpdata와 loaddata로 데이터베이스를 통으로 내보내거나 가져올 수 있다.
### DB 내보내기 : dumpdata
dumpdata는 현재 DB에 있는 데이터를 JSON 파일로 저장한다. (indent 4는 들여쓰기 옵션이다.)
``` Python Shell
python manage.py dumpdata main --output data.json --indent 4
```
### DB 가져오기 : loaddata
JSON 파일로 저장된 DB를 가져올 수도 있다.
```
python manage.py loaddata data.json
```
다음과 같이 나오면 성공한 것이다.
![](https://images.velog.io/images/woongss/post/d3a993e9-52b8-42ea-a4f7-254edaa4d847/image.png)

JSON 형식에 대해서는 추후에 더 공부해봐야겠다. 

#### 참고자료
<M.B.I.T> 테스트 페이지 만들기! With Django (제주코딩베이스캠프)
