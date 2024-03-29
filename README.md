# Section2-Project
### 발표 영상
[![Video Label](http://img.youtube.com/vi/90EY9-rjfoc/0.jpg)](https://youtu.be/90EY9-rjfoc)

# 🎯 해결하고자 하는 문제
## 🎯 Main : 새로운 환자의 설문조사 결과를 바탕으로 심장병의 유무를 파악한다. 

### 🎯 Sub :  심장병에 악영향을 미치는 요인과 심장병을 예방하는 요인을 파악 하고싶다.

## ☑️ 주제 선정 이유

* 한국인의 사망 원인 1위인 암에 이어 2위인 심장병은 (2010정도 까지 사망원인 2위 였던 뇌혈관질환은 감소한 반면) 지속적으로 상승하고 있어서 위험하다고 판단이 되고 있고 미국에서도 대부분의 인종의 주요 사망 원인 중 하나이다.(모든 사람에게 위험한 질환이다.)

* 3대 사인(암, 심장 질환, 폐렴)은 2020년 기준 전체 사인의 44.9%를 차지하고 있다. → 순환 계통 질환의 사망률 전년 대비 3.2% 증가

* 심장병의 유무를 판단해서 조기에 발견한다면 적절한 관리를 통해 사망확률이 낮아질 수 있는 질병이다.

* 따라서 심장병을 조기에 발견하고 가장 큰 악영향을 미치는 요인을 감지하고 예방하는 것은 의료에서 매우 중요하다.

## 💾 Data collection
* 심장병의 유무와 여러가지 지표에 대한 설문조사 결과를 바탕으로 만들어진 데이터셋이다.
* [데이터 출처 : kaggle](https://www.kaggle.com/datasets/kamilpytlak/personal-key-indicators-of-heart-disease)

## 💾 Data set 설명
## 심장 질환의 개인 주요 지표를 모아놓은 데이터셋이다.
* 🇺🇸 **미국의 설문조사 결과**를 토대로 만들어진 데이터셋이다.
* 원래 데이터 세트는 거의 300개 변수를 가지고 있는데 약 20개 변수로 축소된 어느정도 정제된 데이터 셋이다.
* shape = (319796, 18)

## 📋 feature 설명
* HeartDisease: 관상 동맥 심장 질환(CHD) 또는 심근 경색증(MI)이 있다고 보고한 적이 있는 응답자 (Y/N) <- target
* BMI: 체질량 지수(BMI)
* Smoking: 당신은 일생 동안 적어도 100개비의 담배를 피웠습니까? (Y/N) [참고: 5갑 = 100개비]
* AlcoholDrinking: 과음자(성인 남성은 주당 14잔 이상, 성인 여성은 주당 7잔 이상 음주) (Y/N)
* Stroke: (당신은) 뇌졸중이 있습니까? (Y/N)
* PhysicalHealth: 귀하의 신체적 질병과 부상을 포함한 신체적 건강을 생각해보면, 지난 30일 동안 귀하의 건강이 좋지 않았던 날은 며칠입니까? (0-30일)
* MentalHealth: 귀하의 정신건강을 생각해보면, 지난 30일 동안 귀하의 정신건강이 좋지 않은 날은 며칠입니까? (0-30일)
* DiffWalking: 걷거나 계단을 오르는데 심각한 어려움이 있습니까? (Y/N)
* Sex: 성별 ('Female', 'Male')
* AgeCategory: 연령범주 ('18-24', '25-29', '30-34', '35-39', '40-44', '45-49', '50-54', '55-59', '60-64', '65-69', '70-74', '75-79', '80 or older')
* Race: 인종 ('White', 'Black', 'Asian', 'American Indian/Alaskan Native', 'Hispanic', 'Other')
* Diabetic: (당신은) 당뇨병이 있습니까? ('Yes', 'No', 'No, borderline diabetes', 'Yes (during pregnancy)')
* PhysicalActivity: 지난 30일 동안 정규직 이외의 신체활동이나 운동을 했다. (Y/N)
* GenHealth: 일반적으로 당신의 건강은 어떤가? ('Excellent', 'Very good', 'Good', 'Fair', 'Poor')
* SleepTime : 귀하는 24시간 중 평균 몇 시간의 수면을 취하십니까? (1 ~ 24)
* Asthma: (당신은) 천식이 있습니까? (Y/N)
* KidneyDisease: 신장 결석, 방광 감염 또는 요실금을 제외하고 신장 질환이 있다는 말을 들은 적이 있습니까? (Y/N)
* SkinCancer: (당신은) 피부암이 있습니까? (Y/N)

## 🎯타겟 선정
* **HeartDisease** : 심장병의 유무
* 추가로 분석할 항목 : 새로운 환자의 설문조사 결과를 바탕으로 심장병에 악영향을 미치는 요인과 심장병을 예방하는 요인을 파악하는데 도움을 준다.

## 심장병의 유무 파악
* 분류문제 → 여러가지 모델을 만들고 성능을 비교해 볼 것이다.  
  * 결정트리 모델
  * 랜덤포레스트 모델
  * XGBoost 모델
  * LightGBM 모델  

* 성능평가 지표 : f1_beta_score   
  * 정밀도(Precision) VS 재현율(Recall)
  * 심장병이 아니라고 예측했는데 실제로 심장병인 경우 → 치명적이다!   
  * 심장병이라고 예측했는데 실제로는 심장병이 아닌 경우 → 추가 검사를 통해 정정하면 된다.   
  * 따라서 심장병의 유무를 판별하는 모델은 정밀도보다 **재현율(Recall)** 이 높아야 한다!

### 심장병에 악영향을 미치는 요인과 심장병을 예방하는 요인 파악
* 모델에 대한 설명 (XAI) → 모델이 결과를 예측할 때 각 특성이 미치는 영향을 파악하고 설명한다.
  * 특성중요도(Mean decrease impurity, MDI)
  * 순열중요도(Permutation Importance, Mean Decrease Accuracy,MDA)
  * PDP(Partial Dependence Plots)
  * SHAP 라이브러리
