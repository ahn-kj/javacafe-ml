담당자: 이은미



Exploit, Exploration 을 적용하기 위해선 앞에서 설명한 E-greedy 방법 말고도 다른 많은 방법들이 있습니다.

그 중 한가지 방법은 Random한 noise 값을 추가하는 것입니다.



음식점의 평점들이 있다고 했을 때, 평점이 가장 좋은 식당을 가는 것이 아니라,

평점에 Random 값을 더해서 그 중 가장 좋은 식당을 방문하게 됩니다.



이를 수식으로 표현 하면 아래와 같습니다.

a = argmax\(Q\(s, a\) + random\_values\)



a = argmax\(\[0.5 0.6 0.3 0.2 0.5\] + \[0.1 0.2 0.7 0.3 0.1\]



Random noise 에도 decaying 을 적용 할 수 있습니다.



action = np.argmax\(Q\[state, :\] + np.random.randn\(1, env.action\_space.n\) / \(i + 1\)\)



for i in range \(1000\)

	a = argmax\(Q\(s, a\) + random\_values / \(i+1\)\)



첨에는 랜덤 노이즈를 크게 적용하고 가면 갈수록 작은 값의 랜덤 노이즈를 적용해서 크게 영향을 끼치지 않도록 한다.

앞에 이 그리드와 다른 방법이 있는데

노이즈를 추가하게 되면 어떤 영향력을 끼치지만,좀 값이 높은 애들이 선택된 확률이 높다.

가장 좋은 식당이 아닌 두 세번째 좋은 식당이 선정될 가능성이 높은 것이다



