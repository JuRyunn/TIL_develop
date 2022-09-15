# 회귀 (Regression) 

<br>

## 상관성 있는 데이터에 근거한 예측
#### 회귀 (Regression)
- 상관성이 있는 복수 개의 데이터에 기준에 근거하여, 부족한 데이터가 주어졌을 때 기존 데이터들과 오류가 최소화된 다른 값을 찾아낸다.
- 상관성: 두 개 이상의 데이터가 비례 또는 단조 증가/감소 관계에 있을 때.
- 상관성의 예: 키와 몸무게, 같은 아파트 단지 내에서 주택 가격과 주택 크기.
![image](https://user-images.githubusercontent.com/79950504/190313426-0318ce23-099d-4e85-ba94-bd08fba9e965.png)  
- 책의 예: 길이, 높이, 두께, 무게 의 정보가 주어짐 / 길이, 높이, 두께를 통해서 무게를 예측해 볼 수 있음.

<br>

## K- 최근접 이웃 회귀
![image](https://user-images.githubusercontent.com/79950504/190313878-0277240b-70e4-4229-b1b4-d7bd955523cb.png)  
#### 지도 학습의 결과
- 분류: 학습 데이터 분류 중 가장 근접한 분류를 선택.
- 회귀: 학습 데이터와 일관되게 값을 예측. (여기서 예측은 직관의 영역이 아니라 학습데이터와 수학적 관계가 있음)

#### K- 최근접 이웃 알고리즘 활용
- 분류: 예측하려는 샘플에 가장 가까운 k 개의 학습 데이터를 선택하고 다수결로 분류를 결정.
- 회귀: 학습 데이터가 동일한 분류로만 주어졌을 때주변 k 개의 데이터의 평균으로 값을 예측해 볼 수 있음.

<br>

## 학습데이터 준비
```python
import numpy as np
import matplotlib.pyplot as plt
from sklearn.model_selection import train_test_split
from sklearn.neighbors import KNeighborsRegressor
from sklearn.metrics import mean_absolute_error

data_size=100
perch_length=np.random.randint(80,440,(1,data_size))/10 #(1,100)
perch_weight=perch_length**2-20*perch_length+110+np.random.randn(1,data_size)*50 #(1,100)

plt.scatter(perch_length, perch_weight)
plt.xlabel('length')
plt.ylabel('weight')
plt.show()


train_input, test_input, train_target, test_target = train_test_split(
    perch_length.T, perch_weight.T, random_state=42)

print("학습데이터Shape: ", train_input.shape,"테스트데이터Shape: ", test_input.shape)

knr = KNeighborsRegressor()
knr.fit(train_input, train_target)
knr.score(test_input, test_target)

test_prediction = knr.predict(test_input)

mae = mean_absolute_error(test_target, test_prediction)

print(mae)
print(knr.score(train_input, train_target))

knr.n_neighbors = 3
knr.fit(train_input, train_target)

print(knr.score(train_input, train_target))
print(knr.score(test_input, test_target))
```

<br>

## 과대적합과 과소적합
#### 학습과 테스트
- 일반적으로 학습데이터에 대한 모델의 예측 정확도가 높음. (학습 데이터로 학습했기 때문)
- 테스트 데이터에 대해서 정확도가 떨어지는 것이 일반적임.

#### 과대적합: 학습 데이터 예측 >> 테스트 데이터 예측
- 결과가 크게 다르다면 학습 데이터와 테스트 데이터의 특성이 다른 것.
- Shuffle이나 추가적인 데이터 수집이 필요.

#### 과소적합: 학습 데이터 예측 < 테스트 데이터 예측 << 1
- 모델이 매우 단순한 경우나 학습/데이터 수가 부족한 경우.

<br>

## 이웃 개수의 조정
#### 이웃개수
```python
knr.n_neighbors= 3
knr.fit(train_input, train_target)

print(knr.score(train_input, train_target))
0.9804899950518966

print(knr.score(test_input, test_target))
0.974645996398761
```
![image](https://user-images.githubusercontent.com/79950504/190320011-bbf3c2bf-4804-4d23-9058-5cb468f274ff.png)  
- 증가: 전체 데이터 결과를 반영.
- 감소: 주변부 특징에 민감.

<br>

# 선형회귀

<br>


## 선형회귀가 필요한 상황
#### K- 최근접이웃 회귀 모델의 문제점
- 학습 데이터로 주어진 7~45cm에 정확한 모델.
- 70cm 길이의 샘플이 주어지면? -> (최근점 학습 데이터는 45cm 근처에 있음, 결국 45cm 무게로 예측을 하게 되는 문제점)
- 학습 데이터로 주어지지 않은 범위의 샘플이 들어오면 큰 오차 발생.

#### 단조증가/감소의 관계가 있다면?
- 학습 데이터로 주어지지 않은 범위에 대한 예측도 필요.
- 무게=15*길이-37 (y=ax+b) 형태로 비례식을 만들어 줌.
- 이 때, 예측과 타겟의 오차가 최소화 되는 a와 b를 찾아줌.

<br>

## 학습 데이터 값 범위를 넘어서는 데이터
![image](https://user-images.githubusercontent.com/79950504/190322207-a171bd40-f762-4538-873a-8d4d21ae5afe.png)  

```python
distances, indexes= knr.kneighbors([[50]])

plt.scatter(train_input, train_target)
plt.scatter(train_input[indexes], train_target[indexes], maker= 'D')
plt.scatter(50, 1033, marker= '^')
plt.show()
```

#### 선형회귀의 결과
![image](https://user-images.githubusercontent.com/79950504/190322963-fe5b1cc5-60ab-43ce-8658-9b1b0b5f1cc2.png)  

<br>

## 선형회귀에 사용되는 함수
```python
from sklearn.linear_model import LinearRegression

lr= LinearRegression()
lr.fit(train_input, train_target)

print(lr.predict([[50]])
[1241.83860323]

print(lr.coef_, lr.intercept_)
[39.01714496] -709.0186449535477
```

#### 선형회귀 결과 확인
![image](https://user-images.githubusercontent.com/79950504/190324535-04652866-573c-46ea-b38b-54eeb86ad9a6.png)  

```python
plt.scatter(train_target, train_target)
plt.plot([15, 50], [15*lr.coef_+lr.intercept_, 50 * lr.coef_ + lr.intercept])

plt.scatter(50, 1241.8, marker= '^')
plt.show()

print(lr.score(train_input, train_target))
print(lr.score(test_input, test_target))
```

#### 다항회귀
![image](https://user-images.githubusercontent.com/79950504/190326565-3831c8c0-efb2-48ff-a6a4-45d720c76609.png)  
```python
train_poly= np.column_stack((train_input ** 2, train_input))
train_poly= np.column_stack((train_input ** 2, train_input))
```
- 2차 함수 사용.

#### 다항회귀의 결과
![image](https://user-images.githubusercontent.com/79950504/190327136-c9814d78-0c07-40d8-9e78-858a0f3936bb.png)  

```python
lr= LinearRegression()
lr.fit(train_poly, train_target)

print(lr.predict([[50**2], 50]))
print(lr.coef_, lr.intercept_)

point= np.arange(15, 50)

plt.scatter(train_input, train_target)
plt.plot(point, 1.01 * point ** 2 - 21.6 * point + 116.05)

plt.scatter([50], [1574], marker= '^')
plt.show()

print(lr.score(train_poly, train_target))
print(lr.score(test_poly, test_target))
```

