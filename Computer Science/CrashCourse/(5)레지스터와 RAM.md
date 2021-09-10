### 정보 기억 장치

아무리 개별 단위의 컴퓨터의 연산이 잘 이루어진다고 하더라도, 이를 기억할 수 있어야 더욱 복잡한(추상화 된) 연산을 수행할 수 있다.

이번에는 논리게이트를 이용해 구성한 LATCH에서 Register, 그리고 RAM으로 개념을 확장해 볼 것이다.

#### 논리 게이트로 간단한 저장 장치 만들기
![image](https://user-images.githubusercontent.com/88834958/132808790-c90ab6fe-f38a-4d20-8713-4df6720ce2c2.png)

#### LATCH
![image](https://user-images.githubusercontent.com/88834958/132808878-dbba6c30-5a29-4062-8105-bbc9089ec29f.png)

여기에서 Data를 입력하고, 저장할 수 있는지 여부까지 조작할 수 있는 GATED LATCH를 만들어 낼 수 있다.
![image](https://user-images.githubusercontent.com/88834958/132809013-8cfc0768-f5f3-483f-9823-7fcfc479e683.png)

#### 레지스터
이러한 래치를 나란히 늘어놓아서, 더 많은 비트의 정보를 저장하는 래치 그룹을 레지스터라고 한다. 8개 늘어놓으면 8bit 저장소가 된다. 이 때, 레지스터의 비트 수는 너비(width)라고 한다.

#### RAM
래치를 나란히 늘어놓으면, 활용되는 회로의 개수가 지나치게 늘어난다. 이를 방지하기 위해서 매트릭스 형태로 구성을 하고, 특정 위치에 있는 래치를 활성화시킬 수 있게끔 설계한다.
특정 위치 활성화를 위해, 멀티플렉서라는 부품을 활용해 주소를 받아준다.

![image](https://user-images.githubusercontent.com/88834958/132809803-73e3606f-68c3-4810-bf51-109f34fe267b.png)

메모리는 언제, 어느 위치든 무작위 순서로 접근이 가능하다. 그래서 RAM(Random Access Memory)이라고 부른다.

지금까지 살펴본 것은 SRAM(Static Random Access Memory)이고, DRAM, Flash Memory, NVRAM과 같이 다른 종류의 RAM들도 있다.

