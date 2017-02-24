#
Q Learning 기법 소개

그렇다면 강화 학습을 프로그램으로 구현하기 위해서는 어떻게 해야 할까요? 위의 실습에서 Open AI Gym 프로즌 레이크 게임을 예로 들어 보겠습니다. 위의 게임에서는 현재 상태와 맵 정보, 골은 어디에 있고 어디가 함정인지 모두 알고 있는 상태에서 시작했습니다.

하지만 실제 게임에서는 전혀 다른 이야기가 됩니다. 이유는 현재 맵 정보를 알지 못하기 때문입니다. 현재 상태에서 어떤 액션을 취했을때 그곳이 보상을 받을수 있는 골 지점인지, 또는 그냥 길인지, 아니면 게임을 종료시키는 함정인지 알 방법이 없습니다.

여기서 Q가 등장합니다. 위에서 강화학습은 주어진 환경, 상태에서 액션을 취해 환경을 변화시키고 그것에 대한 보상으로 학습을 한다고 했습니다. 만일 이미 상태에 따라 여러가지 액션을 취해보고 그에 따른 결과(보상)를 알고 있는 존재가 있다면 어떨까요?

만약 그런 존재가 있다면 쉽게 목적지까지 도달 할 수 있을 것입니다. Q 라는 존재에게 현재 상태와 액션을 알려주고, 액션 중 가장 보상이 큰 행동을 취하면 될 것이기 때문입니다.

위에서 설명한 것처럼 Q는 현재상태에서 어떤 액션을 취했을때 보상이 어느정도 되는지 돌려주는 존재입니다. 즉 Q 란 다음과 같은 기능을 제공한다고 볼 수 있습니다.

* 현재 상태에서 특정 액션을 취했을때 기대되는 보상을 알려주는 기능 -> maxQ(상태, 액션)

* 현재 상태에서 가장 보상이 높은 액션을 알려주는 기능 -> argmaxQ(상태, 액션[])

위에 기능을 구현하기 위하여 Q 는 Q 테이블을 사용합니다. Q 테이블은 각 상태에서 취할수 있는 모든 액션들의 기대보상을 가지고 있습니다. 그리고 액션을 취하면서 이 Q 테이블을 업데이트 하자는 것이 기본적인 아이디어입니다.

Frozen Lake 게임을 예로 Q 가 어떻게 동작하는지 예를 들어보겠습니다.

위 실습에서 게임을 진행해본 Frozen Lake 게임은 16개의 상태가 있습니다. 각 상태를 테이블처럼 표현하면 다음과 같이 될 것입니다.

<img src="http://postfiles14.naver.net/MjAxNzAyMThfMTg4/MDAxNDg3NDAzMDA3Nzc0.nQedecAA5-pH98E_ndo3XWb6AhqbrGYoMqS8z9MiQxgg.FjYBlLdIgOEiduV6-qpGSAKJuq3LKT1wi-YctEpqLnYg.PNG.akj61300/map.png?type=w2" />

여러가지 방법으로 각 상태에 대한 보상을 줄수 있지만 여기서는 단순하게 생각하기 위해 골(목적지) 상태는 보상을 1로 하고 나머지 상태는 보상을 0으로 해보겠습니다. 그것을 그림으로 보면 다음과 같이 됩니다. 

<img src="http://postfiles6.naver.net/MjAxNzAyMjRfMTgw/MDAxNDg3OTAxNzAzMzk0.6IWM8bF39JFph3SoDI9fFV5vd6V0aouYWc7LcnAhFBog.ydBLN2lk8eQnAscIU3hcX4j95Jd57D21Vw9cLY8PbcQg.PNG.akj61300/map2.png?type=w2" />

각 상태에서는 4가지 액션을 취할 수 있습니다. 그리고 Q 는 각 상태에서 취할수 있는 액션에 대한 기대 보상을 가지고 있다고 했습니다. 그것을 그림으로 그려보면 다음과 같이 될것입니다.

<img src="http://postfiles6.naver.net/MjAxNzAyMjRfNTAg/MDAxNDg3OTAzNDU2ODYw.0usB7QOnkg1uKMs5T0wd4yMrCfzB78-HG4c_VbyoxHkg.oQpQ72rgcM_VU3knfw6zLftAEjm3BgrKLN06leCy6UIg.PNG.akj61300/q_map01.png?type=w2" />

각 상태에서 취할수 있는 모든 액션에 대한 기대보상을 Q 는 위 그림과 같이 가지고 있습니다. 여기서 문제는 최초 게임이 시작되었을때는 Q 도 어디가 골이고 보상이 있는지 모른다는 것입니다.

따라서 최초에는 Q 테이블의 모든 값을 0 으로 초기화 합니다.

<img src="http://postfiles10.naver.net/MjAxNzAyMjRfODIg/MDAxNDg3OTA0MDc3Mjg5.Y4xUGwQ-OfBAghDoJXi0zYzmZnf4pt7DDqy0iwvClUsg.cY4dMc0cgNl9_rUN_uRcEvQRrAecWX7_3j-wdCgSRI0g.PNG.akj61300/q_map02.png?type=w2" />

게임을 시작하고 꽤 오랫동안은 Q 테이블의 값이 모두 0이기 때문에 어디로 가는것이 최선인지 알려줄수가 없습니다. 
그러므로 어느정도 기간은 아무 액션이나 랜덤하게 선택하여 환경을 변화시켜 보는 방법 밖에 없습니다.

만약 랜덤으로 선택한 액션이 시작점에서 오른쪽으로 간 뒤 아래쪽으로 가는 액션이면 어떻게 될까요?

* Right -> Down

<img src="http://postfiles5.naver.net/MjAxNzAyMjRfMTY2/MDAxNDg3OTA5OTk2MDMw.hBtqS9cDz3U6TZgkZpeW-jJkW-MF-BU66cEcILJ6hX8g.6z8Dd_n7cCruTxMJEOXTJpp9tzlBhlcNrDUtg5pRktUg.GIF.akj61300/random02.gif?type=w2" />

보상이 있는 상태까지 도달하지 못했기 때문에 모든 Q 테이블은 0 인 채로 게임이 종료되게 됩니다. 아무것도 변한것이 없는 것이죠. 즉 시행착오만 있었던 셈입니다.

하지만 어느순간 운이 좋게도 보상까지 도달하는 경우도 있을 것입니다. 이를테면 운이좋게 다음과 같이 액션을 취했다고 생각해봅시다.

* Right -> Right -> Down -> Down -> Down -> Right

<img src="http://postfiles5.naver.net/MjAxNzAyMjRfMzAw/MDAxNDg3OTEwNTk0NzYx.YlZoQoPlZSrx-p8XWxBXldwYsX1WDud1Wt5czoPiKWsg.xWkFwXIF3IFAg73gthpbMOS_hCi3vh7mE_ZKHGSymWYg.GIF.akj61300/random03.gif?type=w2" />

마지막 골에 도착한 후에 골 바로 이전 상태에서 Right 액션에 대한 기대보상이 1로 바뀐것에 주목해주세요.

