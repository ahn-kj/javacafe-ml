# Stochastic이란?

지금까지 우리는 미끄러짐이 없는 FrozenLake 게임으로 학습시켜 왔습니다.
그런데 만약 얼음에서 미끄러질 수 있도록 설정한다면 어떻게 될까요?
키보드로 액션을 입력받는 예제를 통해 한번 알아보도록 하겠습니다.

```
import gym
import sys, tty, termios

class _Getch:
    def __call__(self):
        fd = sys.stdin.fileno()
        old_settings = termios.tcgetattr(fd)
        try:
            tty.setraw(sys.stdin.fileno())
            ch = sys.stdin.read(3)
        finally:
            termios.tcsetattr(fd, termios.TCSADRAIN, old_settings)
        return ch

inkey = _Getch()

# MACROS in Gym
LEFT = 0
DOWN = 1
RIGHT = 2
UP = 3

# key mapping
arrow_keys = {
    '\x1b[A': UP,
    '\x1b[B': DOWN,
    '\x1b[C': RIGHT,
    '\x1b[D': LEFT}

# is_slippery true
env = gym.make('FrozenLake-v0')
env.reset()
env.render()

while True:
    # Choose an action from keyboard
    key = inkey()
    if key not in arrow_keys:
        print("Game aborted")
        break

    action = arrow_keys[key]
    state, reward, done, info = env.step(action)
    env.render()
    print("state: ", state, "action: ", action, "reward: ", reward, "info: ", info)

    if done:
        print("finish with reward: ", reward)
        break
```


위 코드를 실행하여 Right→Right→Right→Right→Right→Right로 입력했을 때,  
실제로는 제자리→Down→Down→UP→DOWN→DOWN으로 랜덤하게 이동하는 것을 확인할 수 있습니다.

<img src="http://postfiles5.naver.net/MjAxNzAzMDdfNjcg/MDAxNDg4ODE4MzkzNDc2.1kKLbBXet8hpXCtcIK_P6zE6AHUV5D6KCRAJYnZjGoIg.nQuXsy0c0McOiUMSgwMIMbLFL9LUk_sULQ2vcbUsHfwg.PNG.kioku714/%EC%8A%A4%ED%81%AC%EB%A6%B0%EC%83%B7_2017-03-07_%EC%98%A4%EC%A0%84_12.44.52.png?type=w2" width="400px" />

이와 같이, 다음 action을 예측할 수 없을 때 Stochastic(non-deterministic) 하다고 말합니다. Stochastic 상태에서 기존의 Q-table 업데이트 알고리즘을 그대로 사용한다면 아래 이미지와 같이 성공률이 현저하게 줄어듭니다. 어떤 방법으로 Stochastic 상태의 성공률을 올릴 수 있을까요?

<img src="http://postfiles2.naver.net/MjAxNzAzMDdfMTE1/MDAxNDg4ODE5NjY2MjMz.QhJScVnswudioTU-5veabtcnmVYwuV9C-DENiTQZ31Ig.7Dp0QFeGTHOOmeKIPwv9wTyhhxdD6LmvhQes2DpaCXwg.PNG.kioku714/%EC%8A%A4%ED%81%AC%EB%A6%B0%EC%83%B7_2017-03-07_%EC%98%A4%EC%A0%84_2.00.04.png?type=w2" width="500px" />

## Sarsa 알고리즘

### Temporal-Difference Learning
value function 이 최대가 되는 policy을 찾는 알고리즘 중에는 Dynamic Programming과 와 Monte Carlo Methods가 있습니다.

dynamic progamming은 environment의 model을 다 알고 문제를 푸는 planning입니다.

Monte Carlo Methods 엄청나게 많은 수를 일일이 다 다루지 않더라도 그 가운데에서 샘플링을 하여 확률적 연산을 수행함으로써 최선의 수를 찾아가는 기법으로 알려져 있습니다. 게임 프로그램에서는 이미 많이 사용된다고 합니다.

Temporal-Difference는 Dynamic Programming과 와 Monte Carlo Methods를 조합한 것입니다.

### Q-Learning: Off-Policy TD Control
#### Off-Policy
look over someone's shoulder
간접 경험

### Sarsa: On-Policy TD Control  
#### On-Policy
learn on the job
직접 경험


