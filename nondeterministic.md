# Nondeterministic 환경 설명
action을 예측할 수 없는 환경
(어떤 색다른 예가 좋을지 고민 중)

# Nondeterministic 에서는 어떻게 학습해야 하는가?

## Temporal-Difference Learning
value function 이 최대가 되는 policy을 찾는 알고리즘 중에는 Dynamic Programming과 와 Monte Carlo Methods가 있습니다.

dynamic progamming은 environment의 model을 다 알고 문제를 푸는 planning입니다.

Monte Carlo Methods 엄청나게 많은 수를 일일이 다 다루지 않더라도 그 가운데에서 샘플링을 하여 확률적 연산을 수행함으로써 최선의 수를 찾아가는 기법으로 알려져 있습니다. 게임 프로그램에서는 이미 많이 사용된다고 합니다.

Temporal-Difference는 Dynamic Programming과 와 Monte Carlo Methods를 조합한 것입니다.

## Q-Learning: Off-Policy TD Control
### Off-Policy
look over someone's shoulder
간접 경험

## Sarsa: On-Policy TD Control  
### On-Policy
learn on the job
직접 경험


