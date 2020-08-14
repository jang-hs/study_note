# **sampling & resampling**


## 개요

### 샘플링과 리샘플링 모두 예측 모델링 과정에서 필요

### 샘플링

- 모집단 변수를 추정하기 위해 관측치를 모으는 과정

### 리샘플링

- 데이터 샘플을 경제적으로 사용하여 정확도를 향상시키고 모집단 파라미터의 불확실성을 정량화 하는 방법

## 통계적 샘플링

### 데이터의 각 row는 관측치

### 모든 가능한 관측치를 사용할 수 없는 이유들

- 더 많은 관측은 어렵거나 비용이 많이 들 수 있음

- 모든 관측치를 모으는 것은 어려울 수 있음

- 미래에 추가적인 관측이 생성될 수 있음

### 샘플링은 전체 모집단에 대해 무언가를 추정할 수 있도록 모집단의 일부를 선택하는 것으로 구성

### 샘플링 방법

- 통계적 샘플링은 모집단의 특성을 추정하는 목적으로 모집단의 하위 집합을 선택하는 과정

- 완전한 데이터(전체)로 작업하는 것에 비해 비용절감과 빠른 속도의 이점이 있음

- 데이터 샘플을 수집하기 전에 고려할 점

  - Sample Goal - 표본을 사용하여 추정하려는 모집단의 특성

  - Populatiom - 이론적으로 관측 가능한 범위 또는 영역

  - Selection Criteria - 표본에서 관측/비관측 하는 방법론

  - Sample size - 샘플을 구성할 관측치 수

- 머신러닝에서 사용 가능성 있는 세가지 유형의 샘플링

  - Simple Random Sampling(SRS): 균일 확률로 무작위 추출

  - Systematic Sampling: 균일한 간격과 같은 체계적인 규칙을 가지고 추출

  - Stratified Sampling: 사전에 정의된 범주(계층) 내에서 추출 됨

### Sampling Errors

- 선택 편향 - 표본 추출과정에서 치우치게 추출되는 경우

- 표집 오류 - 관측치 추출의 무작위성에 의해 발생 

- 관측 또는 측정 방법의 체계적 오류와 다른 유형의 오류들

- 추정하고자 하는 모집단 특성에 영향을 미칠 수 있음.

- 요약통계, 시각화 검토 등을 통해 확인

- 표본 추출과 표본 추출을 통한 모집단에 대한 결론 도출에서 모두 주의해야 함

## 통계적 리샘플링

### 추정치의 변동성 또는 불확실성에 대한 생각이 거의 없는 모집단 매개 변수의 단일 추정치만 존재

- 해결법 중 하나 - 데이터 샘플에서 모집단의 파라미터를 여러번 추정하는 것(리샘플링)

### 데이터를 경제적으로 사용하여 모수를 추정. 추정값들의 평균을 사용하거나 신뢰구간을 추가할 수 있음

### 수학적 지식이 거의 필요하지 않은 쉬운 방법

### (단점) 계산 비용,강력한 추정치를 개발하기 위해 수십, 수백, 수천 번의 리샘플이 필요할 수 있음

### 통계적 샘플링 방법과 차이

- 프로세스를 여러번 반복

- 부분 표본과 추정된 모집단 모수가 독립적으로 분포되어 있지 않음(paired statistical tests 가 필요할 수 있음)

### 일반적으로 사용되는 두가지 리샘플링 방법

- k-fold cross-validation

  - 데이터를 k개의 그룹으로 분할하여 각 그룹은 test세트로 사용될 기회가 주어짐. k-1개로 학습, 1개로 검증을 k번 반복

- bootstrap

  - 복원추출을 통해 리샘플링을 수행

  - 모수 추정의 일반적이고 간단한 방법
