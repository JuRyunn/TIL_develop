## 인공지능 (AI)
- 학습, 문제해결, 패턴인식과 같은 주로 인간 지능과 연결된 인지 문제를 해결하는 컴퓨터 공학.

#### 머신러닝
- 경험을 통해 자동으로 학습하는 컴퓨터 알고리즘.
- 기본구조: 입력 -> Mapping -> 출력

#### 딥러닝
- 머신러닝의 한 분야로써 연속된 층(= Layer)에서 의미있는 표현을 배우는데 강점이 있으며 데이터로부터 표현을 학습하는 방식이다.
- ex) 알파고


<br>

## 환경구성
- [Anaconda package Download](https://www.anaconda.com/)
- 설치경로는 간단하게 설정해주어야한다 -> cmd 창에서 추가 설치할 때 경로를 찾아가기 번거롭기 때문.
- 설치단계에서 환경변수는 필수로 추가해줘야한다. 
#### cmd
```cmd
conda --version
conda create -n py39_64 python=3.8 anaconda
conda env list
```

- [Pycharm Install](https://www.jetbrains.com/ko-kr/pycharm/download/download-thanks.html?platform=windows&code=PCC)

```python
import matplotlib.pyplot as plt
form sklearn.neighbors import KNeighborsClassfier

bream_length = [25.4, 26.3, 26.5, 29.0, 29.0, 29.7, 29.7, 30.0, 30.0, 30.7, 31.0, 31.0, 31.5, 32.0, 32.0, 32.0, 33.0, 33.0, 33.5, 33.5, 34.0, 
34.0, 34.5, 35.0, 35.0, 35.0, 35.0, 36.0, 36.0, 37.0, 38.5, 38.5, 39.5, 41.0, 41.0]
bream_weight = [242.0, 290.0, 340.0, 363.0, 430.0, 450.0, 500.0, 390.0, 450.0, 500.0, 475.0, 500.0, 500.0, 340.0, 600.0, 600.0, 700.0, 
700.0, 610.0, 650.0, 575.0, 685.0, 620.0, 680.0, 700.0, 725.0, 720.0, 714.0, 850.0, 1000.0, 920.0, 955.0, 925.0, 975.0, 950.0]

smelt_length = [9.8, 10.5, 10.6, 11.0, 11.2, 11.3, 11.8, 11.8, 12.0, 12.2, 12.4, 13.0, 14.3, 15.0]
smelt_weight = [6.7, 7.5, 7.0, 9.7, 9.8, 8.7, 10.0, 9.9, 9.8, 12.2, 13.4, 12.2, 19.7, 19.9]

length= bream_length + smelt_length
weight= bream_weight + smelt_weight

fish_data= [[1, w] for 1, w in zip(length, weight)]
fish_target= [1]*35 + [0] * 14

kn= KNeighborsClassifier()
kn.fit(fish_data, fish_target)
kn.score(fish_data, fish_target)

kn.predict([[30, 600]])
array([1])

kn49= KNeighborsClassifier(n_neighbors= 49)
kn49.fit(fish_data, fish_target)
kn49.score(fish_data, fish_target)
print(35/49)

ply.scatter(bream_length, bream_weight)
ply.scatter(smelt_length, smelt_weight)
plt.show()
```
