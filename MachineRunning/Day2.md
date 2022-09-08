## 지도 학습과 비지도 학습
#### 지도 학습 (Supervised Learning)
- 학습 데이터 그것에 대응되는 답이 필요하다.
- ex: 개와 고양이의 사진들, 각 사진들에 대응되는 정답 (1번 사진: 개, 2번 사진: 고양이 등...)
- 훈련 데이터: 입력(학습데이터) + 정답(Target, 목표값)

#### 비지도 학습(Unsupervised Learning)
- 학습 데이터는 있지만 목표값이 주어지지 않음.
- K-Means 등 알고리즘을 이용하여 목표값 생성.  

![image](https://user-images.githubusercontent.com/79950504/189032434-3924c4c6-0181-451f-abf2-6c664a3a0d3d.png)

<br>

## 훈련 세트와 테스트 데이터
#### 훈련세트
- 학습을 위한 학습 데이터 및 타겟
- 입력에서 출력으로 연결하는 모델의 정확도를 개선하기 위한 목적의 데이터.
- 테스트 세트와 중복되지 않음.

#### 테스트 세트
- 훈련 결과를 확인하기 위한 입력 데이터 및 타겟.
- 테스트 세트는 학습에 사용하지 않음.
- 훈련 세트에 대한 학습 결과와 유사한 수준의 정확도가 도출되어야 함.  

![image](https://user-images.githubusercontent.com/79950504/189033939-355f071d-a552-4347-a8d3-4667e58db756.png)

<br>

## 테스트 세트에서 평가
![image](https://user-images.githubusercontent.com/79950504/189034052-aa938a58-53f5-4ae0-843e-20ae02e8aea6.png)
```python
from sklearn.neighbors import KNeighborsClassifier

kn= KNeighborsClassifier()
kn= kn.fit(train_input, train_target)

kn.score(test_input, test_target)
0.0
```

<br>

## 샘플링의 편향
#### 잘못된 훈련 데이터
- 훈련 세트와 테스트 세트의 데이터 특성이 완전이 배타적
- A 데이터에 대한 학습만을 실시.
- Model은 B를 구분할 정보가 없음 (= 훈련 세트가 편향됨)

#### 올바른 훈련 데이터
- 훈련 세트와 테스트 세트는 구분하려는 데이터가 유사한 비율로 섞여 있어야한다.

<br>

## Numpy 사용하기
``` python
import numpy as np

input_arr= np.array(fish_data)
target_arr= np.array(fish_target)

print(input_arr)
```
- np.array(): List를 Array로 변경시켜준다.
- Numpy array가 되면 Vector 연산이 가능해지며 다차원 배열 처리가 수월해진다.
- 함수 실행은 대부분 C언어 처리되어 빠르다.

<br>

## 데이터 섞기
```python
np.random.seed(42) # seed(값)을 지정하면 같은 random이지만 같은 sequence를 얻을 수 있음

index= np.arange(49)
np.random.suffle(index)

[13 15 16 45 47 97 33 43 23 32 12 54 67 72 39 10 39 47 75 88 92 ...]

train_input= input_arr[index[:35]]   # index를 랜덤으로 생성하며 A, B가 구분되어 있는
train_target= target_arr[index[:35]] # 데이터를 섞어준다.
```

<br>

## 데이터 나누고 섞어주기
```python
test_input= input_arr[index[35:]]
test_target= target_arr[index[35:]]

import matplotlib.pyploy as plt

plt.scatter(train_input[:, 0], train_input[:, 1])
plt.scatter(test_input[:, 0], test_input[:, 1])

plt.xlabel('length')
plt.ylabel('weight')
plt.show()
```


<br>

##  Numpy로 데이터 준비
```Python
fish_data= np.column_stack((fish_length, fish_weight))
[[25.4 252.] [26.3 290.] [26.5 340.] [29. 363.] [29. 430.]]

fish_target= np.concatenate((np.ones(35), np,zeros(14)))
[1. 1. 1. 1. 1. 1. 1. 1. 1. 1. 1. 1. 1. 1. 1. 1. 1. 1. 1. 1. 1. 1. 1. 1.
1. 1. 1. 1. 1. 1. 1. 1. 1. 1.1. 0. 0.0. 0. 0. 0. 0. 0. 0. 0. 0. 0. 0. 0. 0.]
```

## 사이킷런으로 데이터 나누기
```python
from sklearn.model_selection import train_test_split

train_input, test_input, train_target, test_target= train_test_split(fish_data, fish_target, stratify= fish_target, random_state=42)
```

#### 수상한 도미
```python
from sklearn.neighbors import KNeighborsClassifier

kn= KNeighborsClassifier()
kn.fit(train_input, train_target)
kn.score(test_input, test_target)
1.0

print(kn.predict([[25, 150]]))
[0.]

distancees, indexes= kn.kneighbors([[25, 150]])
plt.scatter(train_input[:0], train_input[:1])
plt.scatter(25, 150, marker= '^')
plt.scatter(train_input[indexes, 0], train_input[indexes, 1], marker= 'D')
plt.xlabel('length')
plt.ylabel('weight')
plt.show()
```

#### 기준 맞추기
```python
plt.scatter(train_input[:, 0], train_input[:, 1])
plt.scatter(25, 150, marker= '^')
plt.scatter(train_inpit[indexes, 0], train_input[indexes, 1], marker= 'D')
plt.xlim((0, 1000))
plt.xlabel('length')
plt.ylabel('weight')
plt.show()
```

#### 표준 점수로 바꾸기
```python
mean= np.mean(train_input, axis= 0)
std= np.std(train_input, axis= 0)

print(maen, std)[27.29722222 454.09722222] [9.98244253 323.29893931]
train_scaled= (train_input - mean) / std
```

#### 수상한 도미 다시 표현
```python
new= ([25, 150] - mean) / std

plt.scatter(train_scaled[:, 0], train_scaled[:, 1])
plt.scatter(new[0], new[1], marker= '^')
plt.xlabel('length')
plt.ylabel('weight')
plt.show()
```

#### 전처리 데이터 훈련 모델
```python
kn.fit(train_scaled, train_target)
test_scaled= (test_input - mean) / std
kn.score(test_scaled, test_target)
1.0

print(kn.predict([new]))
[1.]

distances, indexes= kn.kneighbors([new])

plt.scatter(train_scaled[:, 0], train_scaled[:, 1])
plt.scatter(new[0], new[1], marker= '^')
plt.scatter(train_scaled[idexes, 0], train_scaled[indexes, 1], marker= 'D')
plt.xlabel('length')
plt.ylabel('weight')
plt.show()
```

<br>

## 전체코드
```python
import matplotlib.pyplot as plt
import numpy as np
from sklearn.neighbors import KNeighborsClassifier

bream_data_size=60 #도미
smelt_data_size=20 #빙어

bream_length = np.random.randn(1,bream_data_size)*5+35 #평균 0 표준편차 1
bream_weight = bream_length*20+np.random.randn(1,bream_data_size)*20

smelt_length= np.random.randn(1,smelt_data_size)*2+12
smelt_weight= smelt_length+np.random.randn(1,smelt_data_size)*2

plt.figure(1)
plt.scatter(bream_length, bream_weight)
plt.scatter(smelt_length, smelt_weight)
plt.xlabel('length')
plt.ylabel('weight')
plt.show()

length=np.concatenate((bream_length,smelt_length),axis=1)
weight=np.concatenate((bream_weight,smelt_weight),axis=1)
#(1,80)

fish_data = np.concatenate((length,weight),axis=0).transpose()#입력
fish_target = np.array([1]*bream_data_size + [0]*smelt_data_size)#출력
#(80,2)

np.random.seed(42)
index=np.arange(bream_data_size+smelt_data_size)
np.random.shuffle(index) #60개도미+20개빙어 ==> 마구마구 섞임

train_input=fish_data[index[0:60]] #학습용 데이터
train_output=fish_target[index[0:60]]
# 학습 데이터로 학습을 시킨 모델에 학습 데이터로 테스트 ==> 최악
test_input=fish_data[index[60:]] #테스트 데이터
test_output=fish_target[index[60:]]

kn = KNeighborsClassifier() #학습 알고리즘
kn.fit(train_input, train_output) #컴퓨터가 학습 Mapping
print(kn.score(test_input, test_output)) # 잘 된다.
print('결과는:', kn.predict([[25, 300]]))
plt.figure(3)
plt.scatter(bream_length, bream_weight)
plt.scatter(smelt_length, smelt_weight)
plt.scatter(15, 15, marker='^')

plt.xlabel('length')
plt.ylabel('weight')
plt.show()
```
