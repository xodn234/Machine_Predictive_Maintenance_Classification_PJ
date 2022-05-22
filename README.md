### Project (2022.01.07 ~ 2022.01.12)
- - -
# 기계 불량 예측  유지보수 분류

### 주제 선정 과정
- 주제선정 이유
  - 소프트웨어와 하드웨어의 융합
    - 기술이 발전 될 수록 AI와 하드웨어의 결합은 더욱 늘어날 것이며 스스로 불량을 찾아 유지보수를 위한 목적으로 관련 데이터를 검색
- 왜 불량을 예측 해야 하는가?
  - 비용 및 시간 절감
    - 기계가 많으면 하나하나 점검 목록을 분류하고 불량을 찾는 시간과 비용이 많이 들어감
  - 안전 확보
    - 불량동작으로 인하여 기계가 오동작하는 시간이 길수록 위험 상황에 노출될 가능성이 크다. 

### 문제 인식 과정
- 불량예측은 무슨 문제인가? 
  - 기계 불량예측 문제는 정상과 불량을 예측 하기 때문에 분류 문제로 인식
- 베이스라인(분류 -최빈값)
  - 정상(0) 불량(1) - 타겟 비율
    - 0 : 0.9661
    - 1 : 0.0339 
- 어떤 평가지표를 사용할 것인가?
- ![image](https://user-images.githubusercontent.com/78893090/169688396-3f030691-c1a2-4bfb-b8dc-d075e9672013.png)
  - 정상(0)으로 예측 했지만 실제 불량(1) 이라면 위험성이 큼
  - 불량(1)이라고 예측 했지만 실제 정상(0) 이라면 점검의 기회
  - 불량을 파악하고 불량을 예측 하기위하여 `재현율(Recall)` 사용

### Feature Engineering
- ![image](https://user-images.githubusercontent.com/78893090/169688456-897c94e4-e5dd-49c2-87e6-2735dc584c41.png)
- Data Leakage 문제로 Failure Type 삭제 

### 시각화
- ![image](https://user-images.githubusercontent.com/78893090/169688511-4c3d7414-ce70-422c-9aae-4571b64bf25b.png)
- ![image](https://user-images.githubusercontent.com/78893090/169688520-8117891a-b01d-458b-abe3-c154eead95d2.png)

### 모델
- 기본 모델 비교
- ![image](https://user-images.githubusercontent.com/78893090/169688557-f28fabff-fc09-4bcd-bb3d-a2f1f1b81b55.png)
- 과적합의 문제를 해결하기 위해 RandomForest(bagging) 사용
- ![image](https://user-images.githubusercontent.com/78893090/169688635-83654afe-018a-4553-bdf7-63efe0eea232.png)
- 최적의 모델을 위해 15%이상은 불량(1)으로 판단
- ![image](https://user-images.githubusercontent.com/78893090/169688722-9b3da3b3-eb03-4fb0-a700-fabb88b43a3c.png)
- 적용된 모델
- ![image](https://user-images.githubusercontent.com/78893090/169688734-d7dc5d2c-0a4e-4aca-b1e1-7362b80bf5f6.png)

### 모델 해석
- 모든 데이터셋의 불량 여부 결정 과정
- ![image](https://user-images.githubusercontent.com/78893090/169688768-8671dde5-8f55-438e-89ec-e92d4a67a350.png)
- 각각의 데이터의 판단 요인 확인
- ![image](https://user-images.githubusercontent.com/78893090/169688825-096e95ae-9101-4109-bf01-a7f869525af5.png)

### 결론
- 불량으로 판단된 모델을 점검할 수 있으며 어떠한 요인으로 인하여 불량인지를 확인 할 수 있다. 

### 주요 스킬
- scikit-learn
