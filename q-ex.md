#간단한 Q 알고리즘 적용 실습


```python
import numpy as np
import random as pr

def rargmax(vector):
    """ Argmax that chooses randomly among eligible maximum indices."""
    m = np.amax(vector)
    indices = np.nonzero(vector == m)[0]
    return pr.choice(indices)
```

액션을 정하기 위한 알고리즘을 정의합니다. Q테이블의 액션 기대값이 가장 큰 액션을 선택하거나, 모든 액션의 기대값이 0 이라면 랜덤하게 액션 선택합니다.


```python
import gym
from gym.envs.registration import register

register(
    id='FrozenLake-v3',
    entry_point='gym.envs.toy_text:FrozenLakeEnv',
    kwargs={'map_name' : '4x4', 'is_slippery': False}
)
env = gym.make('FrozenLake-v3')
```

gym 패키지를 import하고 OpenAI GYM에서 제공하고 있는 환경 중 FrozenLake-v3 환경을 생성합니다.


```python
# Initialize table with all zeros
Q =np.zeros([env.observation_space.n,env.action_space.n])
```

Q 테이블의 모든 값을 0으로 초기화 합니다.  


```python
# create lists to contaion total rewards and steps per episode
rList = []

# Set learning parameters
num_episodes = 2000

for i in range(num_episodes):
    # Reset environment and get first new observation
    state = env.reset()
    rAll = 0
    done = False

    # The Q-Table learning algorithm
    while not done:
        action = rargmax(Q[state, :])

        # Get new state and reward from environment
        new_state, reward, done,_ = env.step(action)

        # Update Q-Table with new knowledge using learning rate
        Q[state,action] = reward + np.max(Q[new_state,:])

        rAll += reward
        state = new_state

    rList.append(rAll)
```

키 값을 입력 받고 사용자가 입력한 키 값에 따라 액션 취합니다.  
총 2000번의 에피소드를 정의하고 에피소드가 끝날때까지 액션을 취하고 최종 보상값을 리스트에 담습니다.  
이 때 액션은 위에서 정의해 놓은 알고리즘을 통해 정합니다.


```python
print("Sucss rate: " + str(sum(rList)/num_episodes))
print("Final Q-Table Values")
print("LEFT DOWN RIGHT UP")
print(Q)
```

2000번의 에피소드를 진행한 결과값을 출력합니다.  
(2000번의 에피소드 중 목적지까지 도달한 확률, 2000번의 에피소드 진행 후 Q테이블의 값)


```python
import matplotlib.pyplot as plt

plt.bar(range(len(rList)), rList, color="blue")
plt.show()
```

matplotlib 패키지를 import하고 성공한 횟수를 그래픽으로 출력합니다.  
* 그래프를 출력하는 코드는 notebook 또는 pycharm등의 애플리케이션 환경에서는 정상적으로 실행되지 않습니다. 터미널을 이용하여 직접 실행 해야 합니다.

######(Jupyter Notebook 실습코드 - 하단이 보이지 않을 경우 새로고침)
<script src="https://gist.github.com/rygh4775/1f502f134bcd8601a910840e1c8a4563.js"></script>
