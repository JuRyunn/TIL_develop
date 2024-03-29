## 알고리즘 효율성 분석
#### 좋은 알고리즘
- 시간효율성(Time efficiency) / 공간효율성(Space efficiency)
- CPU 시간이나 메모리와 같은 컴퓨터의 자원들을 적게 사용하는 것이 좋은 알고리즘이다.
- 실행시간이 가장 중요하게 생각되며 알고리즘 효율성 평가의 기준이 된다.
- 임베디드 시스템과 같은 제한적인 하드웨어의 경우 메모리 사용량도 중요하다.

<br>

## 효율성 분석의 기초
```python
import time # time 모듈 호출

start= time.time() # 현재 시각을 start에 저장. (시작시각)
testAlgorithm(input) # 실행시간을 측정하려는 알고리즘 함수 호출.
end= time.time() # 현재 시각을 end에 저장. (종료시각).
print("실행시간= ", end-start) # 실제 실행시간 출력. (종료 - 시작)
```
#### 문제점?
- 같은 조건의 실행시간.
- SW 환경, 사용한 언어.
- 모든 데이터에 대해 연산하는가.
- 절대적 시간 측정 -> 이론적인 복잡도 분석.

<br>

## 알고리즘 복잡도 분석에서의 중요점
- 알고리즘에서 입력의 크기란 무엇인가
- 복잡도에 영향을 미치는 가장 핵심적인 기본 연산은 무엇인가.
- 입력의 크기가 증가함에 따라 처리시간은 어떤 형태로 증가하는가.
- 입력의 특성에 따라 알고리즘 효율성에는 어떤 차이가 있는가.

#### 입력의 크기
- 알고리즘의 효율성은 입력 크기의 함수 형태로 표현.
- 무엇이 입력의 크기를 나타내는지를 먼저 명확히 결정.
- ex: 리스트에서 특정값을 찾는 문제, x의 n 거듭제곱, 다항식의 연산...

#### 기본연산 (실행시간 측정의 단위)
![image](https://user-images.githubusercontent.com/79950504/189780603-887c4739-1ffb-40ff-a577-65c0bec25895.png)  
- 알고리즘에서 가장 중요한 연산.
- 이 연산이 실행되는 횟수만을 계산.
- ex: 다중 루프의 경우 가장 안쪽 루프에 있는 연산

<br>

#### 최선/최악/평균 효율성
![image](https://user-images.githubusercontent.com/79950504/189781184-3547875c-809a-46b8-b8e4-3937b9740e3c.png)  
- 입력의 종류 또는 구성에 따라 다른 특성의 실행시간.
- 최선의 경우 (best case): 실행시간이 가장 적은 경우로써 알고리즘 분석에서는 큰 의미가 없다.
- 평균적인 경우 (average case): 알고리즘의 모든 입력을 고려하고 각 입력이 바랭할 확률을 고려한 평균적인 실행시간을 의미하는데 정확하게 계산하기 어렵다.
- 최악의 경우 (worst case): 입력의 구성이 알고리즘의 실행시간을 가장 많이 요구하는 경우를 말하는데 가장 중요하게 사용된다.

![image](https://user-images.githubusercontent.com/79950504/189781552-d3feb183-9bf3-43dd-96bb-884ac295f40a.png)

```python
def sequential_search(A, key):
  for i in range(len(A)):
    if A[i] == key:
      return i
    return -1
```

<br>

## 점근적 성능 분성 방법
![image](https://user-images.githubusercontent.com/79950504/189782219-36ccf303-5a67-447e-9b17-da791751511f.png)  
- 차수가 가장 큰 항이 절대적인 영향

#### 점근적 표기 (asymptotic notation)
![image](https://user-images.githubusercontent.com/79950504/189782537-2059f859-26d6-4b39-931f-a8a2836dc580.png)  
- n이 무한대로 커질 경우 복잡도를 간단히 표현.
- 복잡도 함수를 최고 차항만을 계수 없이 취해 단순화.


#### 빅오 표기법
- 어떤 함수의 점근적 하한을 표시하는 방법.
![image](https://user-images.githubusercontent.com/79950504/189782979-bc985715-7bbd-4c9f-aa8b-641d742cbaa3.png)  











