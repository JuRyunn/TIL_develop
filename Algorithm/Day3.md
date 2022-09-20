## 억지기법 (Brute-force)
- 컴퓨터의 계산 능력을 이용하여 수학적 혹은 논리적으로 해결될 수 없는 문제를 해결하는 방법.
- 문제의 정의를 바탕으로한 가장 직접적인 방법.

#### 억지기법의 중요성
- 해결하지 못하는 것보다는 단순하게라도 해결하는것이 훨씬 좋다. 또한 쉬운 문제를 어렵게 풀 필요는 없다.
- - 매우 광범위한 문제에 적용할 수 있는 알고리즘 설계 기법이다.
- 입력의 크기가 작은 경우 충분히 빠를 수 있으며 점근적으로 더 효율적인 알고리즘보다 실제로 더 빠를 수 있다.
- 더 효율적인 알고리즘의 설계와 분석을 위한 이론적인 기반이 된다.

<br>

## 선택정렬
![image](https://user-images.githubusercontent.com/79950504/191140407-53a60e11-de9b-42cc-8863-7836de11b7d5.png)  
- 입력 리스트에서 가장 작은 항목을 찾고 이것을 꺼내 정렬된 리스트에 순서대로 저장한다.

```python
# 선택정렬

def selection_sort(A):
  n= len(A)
    for i in range (i+1, n):
      if(A[j] < A[least]):
        least= j
      A[i], A[least]= A[least], A[i]
      printStep(A, i + 1);
```

```python
# 선택정렬

data= [5, 3, , 4, 9, 1, 6, 2, 7]
print("Original : ", data)
selection_sort(data)
print("Selection : ", data)
```

#### 복잡도 분석
- 입력의 크기: 리스트의 전체 항목수 n
- 기본연산: 비교연산 A[j] < A[least]
- 입력 구성에 따른 차이: 입력에 상관없이 항상 일정한 횟수의 비교 연산 필요






- 
