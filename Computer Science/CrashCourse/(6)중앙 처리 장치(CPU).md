### 중앙 처리 장치(CPU)
앞서 두 개의 강의에서 ALU와 RAM에 대해 배웠다. 이걸 베이스로 컴퓨터의 "심장"에 비유되는 CPU를 만들 수 있다.

### CPU의 예시
![image](https://user-images.githubusercontent.com/88834958/132811113-053cfb3f-c1d3-4575-b1b8-2012172f2adf.png)

단순한 CPU를 도식화 한 것이다. 그림에서 설명한 바와 같이 CPU는 Fetch, Decode, Execute의 순으로 실행된다.
Fetch는 RAM에서 Instruction(명령)을 가져오는 행위인데, Instruction은 Instruction Table에 맞게 코드로 작성되어 있다. 
Decode는 가져온 instruction의 코드를 instruction table에 근거해서 해석한다. 
이제 Register A, B, C, D에 값을 조작하고 임시로 저장하는 Execute 단계를 거친다.

### CLOCK
CPU에 CLOCK이라는 부품을 추가해서, Fetch - Decode - Execute 의 사이클을 자동으로 돌릴 수 있게 해준다. CLOCK은 정확하고 규칙적인 시간에 전기 신호를 발생시킴으로써 이를 가능하게 만든다.
CPU가 각 사이클을 도는 속도를 clock speed라고 표현하는데, Hz로 표현하며 1Hz = 1 cycle / 1s 이다. 더 빠른 단위로 KHz, MHz, GHz 등의 단위가 있다.
기본 clock speed보다 더 속도를 높여서 CPU를 빠르게 할 수도(Overclock), 속도를 낮춰서 CPU를 느리게 할 수도(Underclock) 있다. Underclock의 경우 전력 소비 감축 효과가 있기 때문에, 배터리로
동작하는 노트북이나 스마트폰에서 아주 중요하다. 그래서 clock speed를 자동으로 조절해줄 필요가 있는데, 이를 dynamic speed scaling(동적 주파수 스케일링) 이라고 한다.
