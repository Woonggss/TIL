# Pandas Document

pandas library를 사용하면서 알게 된 내용들을 정리해 놓은 문서입니다.
pandas 관련 내용들은 이 문서에 정리할 예정입니다.

## Load Dataset

pd.read_csv(경로명)을 활용해 csv 데이터 셋을 가져올 수 있다.

> 사용법
> dataframe = pd.read_csv(경로명)

## 데이터셋 정보 확인하기

dataframe.info()를 활용해서 column 별 정보(데이터 갯수, 데이터 형태 등)를 확인할 수 있다.

## 결측치와 중복값 제거

결측치와 중복값은 각각 dataframe.drop_na()와 dataframe.drop_duplicates()로 제거할 수 있다.

> 사용법
> dataframe = dataframe.drop_na()
> dataframe = dataframe.drop_duplicates()
> 새로운 변수에 drop한 값을 담을 수도 있다.

## 행/열 인덱싱

여러 방법들을 작성하였지만, 만능 key는 .loc\[,]라고 생각하면 될 것 같다.

### 1. 열 인덱싱

1-1. Series로 뽑아내기

dataframe\['column_name']을 활용해서 열을 인덱싱할 수 있다. 이 때 , Series 형태의 값을 return한다.

1-2. Dataframe으로 뽑아내기

dataframe\[\['column_name_1','column_name_2',...]]으로 뽑아낼 수 있다. 이 때, dataframe 형태의 값을 return한다.

### 2. 행 인덱싱

2-1. .loc로 인덱싱하기

dataframe.loc\[]로 행 인덱스의 이름을 입력해주면 행을 불러올 수 있다. 범위로 지정할 수도 있다.

범위는 : 형태도 가능하며, 리스트 인덱싱으로 띄엄띄엄 불러오는 것도 가능하다.

> ex) datafame.loc\[\['one','three','four']] 

또한, dataframe.loc\[,]으로 args를 2개 주면, \[행,열] 형태로 인덱싱 할 수도 있다. 
> ex) datafame.loc\[\['one','three','four'],\['number','age','gender']]

2-2. .iloc로 인덱싱하기

.loc 메소드와 같은 방식으로 인덱싱하면 된다. 다만, .iloc는 인덱스 '번호'로 불러온다는 차이가 있다.
> ex) datafame.iloc\[0:3, 3:5]

### 3. Boolean 인덱싱

열에서 조건에 맞는 행을 추출할 때 사용된다.

dataframe\['column_name'] > 2015 와 같이 작성하면, 조건에 맞춰 True/False로 열들이 반환된다. 이를 mask라고 한다.

그러면 .loc로 mask를 집어넣어주면 조건에 맞는 dataframe을 불러올 수 있다.

## 행, 열 값 추가

인덱싱과 같은 방식으로 하되, 그냥 새로운 값을 주면 된다. 새로운 값은 list로 주면 된다.

> 예시
> 행 값 추가 : dataframe.loc\['row_index'] = \[value_1,value_2,value_3,value_4,...]
> 열 값 추가 : dataframe\['new_column_name'] = value

## 집계 함수

dataframe.groupby(\['column_name_1','column_name_2',...]) 형태로 집계할 수 있다. 이러면 groupby 된 객체가 반환되는데, groupby 객체의 메서드를 활용해 통계 값들을 확인할 수 있다.

> 많이 사용되는 메소드
> groupby_dataframe.count() : 개수를 집계할 때 사용된다. dataframe을 반환한다.
> groupby_dataframe.describe() : 통계량 정보를 보여준다. mean, quantile, count 등의 정보를 보여준다. dataframe을 반환한다. 

## 중복 값 제거하기

series.unique() 메소드로 중복 값들을 제거한 고유 값 series를 return 할 수 있다.

## 그래프 그리기

dataframe.plot() 메소드로 그래프를 그릴 수도 있다. 활용할 수 있는 args들은 다음과 같다.

* kind : 그래프의 종류이다.
* title : 그래프의 제목이다.
* legend : 범례이다. None을 주면 범례를 없앨 수 있다.
* color : 그래프의 색을 설정할 수 있다. list에 담아서 iterate 돌릴 수도 있다.

