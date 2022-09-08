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
