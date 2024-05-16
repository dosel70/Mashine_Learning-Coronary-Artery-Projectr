# 📈 고차원 이진 분류 분석 프로젝트  

## 관상동맥 질환 환자 예측 분류 분석 프로젝트
<img src="https://mdtoday.co.kr/news/data/20240220/p1065576020248453_227_thum.jpg">  

  ### 📌 데이터 세트 주제 
  - 나이, 성별, 신체 사이즈, BMI, Na 같은 신체 특성들을 활용하여 관상동맥질환의 치사량을 분석하겠습니다.
  #### 📌 Feature별 설명
  > 총 Column 개수가 55개인 고차원 데이터 입니다.
    
  ### ✏️ 고차원 데이터 관상동맥 질환 예측 분류 프로젝트 진행 방향성
  - [데이터 전처리 (결측치, 중복된 데이터, 이상치 등 제거 및 일반화 작업, 타겟데이터 오버샘플)](#전처리-작업)
  - [독립변수와 종속변수들의 상관관계 확인](#correlation-종속변수와의-상관관계-분석)
  - [분류 분석 실시 (1 ~ 7 Cycle)](#📌-전처리-완료)
  - [1 Cycle - lda 차원축소 후 RandomForest 분류 모델 분석 ](#1-Cycle)
  - [2 Cycle - pca 차원축소 후 RandomForest 분류 모델 분석 ](#2-Cycle)
  - [3 Cycle - 오차행렬 정리 및 그에 따른 임계치 조정 ](#3-Cycle)
  - [4 Cycle - lda 차원 축소 후 로지스틱 회귀 분석](#4-Cycle)
  - [5 Cycle - 오차행렬 정리 및 그에 따른 임계치 조정](#5-Cycle)
  - [최종 결론](#Total-Result)

## 데이터세트(csv파일 PNG) <USA House Price Predict>
<img src='https://github.com/dosel70/MachineLearning-Project/assets/143694489/019e4123-bf86-4a0b-963a-ac26599fe869' width="600px">

## 전처리 작업
- ✏️ 해당 데이터세트 에서는 결측치 및 중복된 데이터를 제거 후  범주형 데이터들은 대부분 이진데이터여서, LabelEncoding 작업을 하여서 수치형으로 바꿔주었습니다.  
<img src="https://github.com/dosel70/MachineLearning-Project/assets/143694489/d6208ea1-8f3e-47bd-aadb-09e7ca9283a3" width="600px">  

- LabelEncoding 작업 후 결과  
<img src="https://github.com/dosel70/MachineLearning-Project/assets/143694489/dcaca1de-41fb-4159-9949-6f1a90650017" width="600px">

## correlation 종속변수와의 상관관계 분석
<img src='https://github.com/dosel70/MachineLearning-Project/assets/143694489/e7d8da29-bc6a-4521-8530-340cd4fc3ff3' width="600px">  

위 이미지와 같이 Typical Chest Pain (전형적인 협심증)Feature가 가장 상관관계가 높았으며, 타겟 데이터에 대해 아예 연관성이 없는 Exertional CP라는 Feature는 제거해주었습니다.  

## 종속변수(Target데이터) 오버샘플링 시행  
<img src="https://github.com/dosel70/MachineLearning-Project/assets/143694489/5aeb59e2-60b6-4792-a601-df7e4d5aff2b" width="600px">

### 📌 전처리 완료  

## 1 Cycle  
> ### lda 차원축소 후 RandomForest 분류 모델 분석  

- lda 차원축소 데이터 프레임 생성  
<img src="https://github.com/dosel70/MachineLearning-Project/assets/143694489/55232732-eee7-41e0-b7b8-69d297c6858f" width="600px">  

- Pipeline을 통해 lda로 차원축소한 데이터와 RandomForest(bagging) 분류 모델 훈련   
<img src="https://github.com/dosel70/MachineLearning-Project/assets/143694489/f7422a27-f4e4-448f-9f8a-f62b43e3df4b" width="600px">  

- lda 차원축소를 사용한 RandomForest 분류 모델 성능 평가  
<img src="https://github.com/dosel70/MachineLearning-Project/assets/143694489/e159a1c2-3bb6-4854-822a-bbeaee433d32" width="600px">  

### 📃 1 Cycle Result
>  lda 차원축소로 RandomForest 분류 모델 평가 결과 86 %의 정확도와 0.77의 F1 Score를 보입니다.

## 2 Cycle
> ### pca 차원축소 후 RandomForest 분류 모델 분석  

- pca 차원축소 데이터 프레임 생성  
<img src="https://github.com/dosel70/MachineLearning-Project/assets/143694489/6004d292-a43a-4825-8cbc-660b5f33478d" width="600px">    
  
- 낮은 차원에서도 높은 데이터 보존율을 보입니다.

- Pipeline을 통해 pca 차원축소로 2차원으로 설정하고  RandomForest(bagging) 분류 모델 훈련   
<img src="https://github.com/dosel70/MachineLearning-Project/assets/143694489/f8334ef4-e692-463a-a9e1-5b999cc1bd8c" width="600px">  

- pca 차원축소를 사용한 RandomForest 분류 모델 성능 평가  
<img src="https://github.com/dosel70/MachineLearning-Project/assets/143694489/3ca45295-dbc2-4319-a526-e57e9f24f668" width="600px">      

> pca를 사용한 차원 축소 결과 83 %의 정확도와 0.70의 F1 Score를 보입니다.

- #### LDA vs PCA 성능 비교 시각화  
<img src="https://github.com/dosel70/MachineLearning-Project/assets/143694489/dcb03219-7b96-43aa-b832-104a784fda03" width="600px">

### 📃 2 Cycle Result
> 차원축소를 통해서 해당 분류 모델을 분석할 경우에는 확실히 LDA기법을 사용해서 차원 축소를 하는게 적합합니다.


## 3 Cycle
> ### lda 차원축소  RandomForest Classifier 으로 분석한 데이터의 임계치(Threshold) 조절 시행
>  오차행렬 정리 

<img src="https://github.com/dosel70/MachineLearning-Project/assets/143694489/1adb56c9-4a3f-4c54-b2f6-c7d7506e513c" width="800px" style="margin-bottom: 30px">  

- #### 🏆 FN에 해당하는 ERROR2의 경우가 더 치명적이기 때문에 임계치를 낮추어서 재현율을 높여야 합니다!

> **Threshold를 0.47로 낮추면 재현율(Recall)과 F1 Score 둘다 증가하는 것을 볼 수 있습니다.**

<img src="https://github.com/dosel70/MachineLearning-Project/assets/143694489/11c313d6-6962-44f3-adf1-21c13fd0cfa9" width="800px" style="margin-bottom: 10px">   

> Threshold : 0.47 결과    

<img src="https://github.com/dosel70/MachineLearning-Project/assets/143694489/b405b0cc-a4a1-4c1a-976c-8332ad11158a" width="800px" style="margin-bottom:10px"> 
  
> Threshold 값에 따른 precision, recall 변화 추이 시각화  

<img src="https://github.com/dosel70/MachineLearning-Project/assets/143694489/272e42d9-e3a2-45e6-914e-787344dbffe5" width="800px" style="margin-bottom:10px"> 

> **ROC Curve** 이미지  

<img src="https://github.com/dosel70/MachineLearning-Project/assets/143694489/d0b6a675-2230-4b62-947c-baeb118f9c25" width="800px">


### 📃 3 Cycle Result  

<img src="https://github.com/dosel70/MachineLearning-Project/assets/143694489/82d8087b-aafa-49dd-8b34-a6413c0bd163" width="800px">  


> #### LDA 로 차원축소를 하였을 때, bagging 분류모델 같은 경우 Threshold를 0.47로 낮춰주어야 최적의 결과를 얻을 수 있었습니다.

> #### 최종적으로 임계치를 0.47로 낮출 때 최적의 결과를 얻을 수 있었습니다.

## 4 Cycle
> ### 차원 축소 후 (LDA) 로지스틱 회귀 분석
<img src="https://github.com/dosel70/MachineLearning-Project/assets/143694489/dae49bb2-a722-4b41-8799-151e5b0a7ed7" width="600px">   

- lda 차원 축소 후 로지스틱 회귀 분석 평가 결과
  
<img src="https://github.com/dosel70/MachineLearning-Project/assets/143694489/b9199086-e67d-4ebd-bb60-e22de67e6126" width="600px">  

### 📃 4 Cycle Result
 
<img src="https://github.com/dosel70/MachineLearning-Project/assets/143694489/41c1b3b1-ce45-4273-a5c9-436bf1d43145" width="800px">  

> #### 기존 차원축소를 한 데이터에 Bagging 분류모델을 사용한 결과와 Logistic Regression모델을 사용한 결과를 비교 해보면

> Bagging 분류 모델의 성능이 더 좋은 것을 알 수 있습니다.

> 그러나 Logistic Regression 모델 또한 괜찮은 성능을 보이는 것을 알 수 있습니다.

## 5 Cycle  
> ### 오차행렬 정리 및 그에 따른 임계치 조정

- Threshold(임계치)에 따른 성능 점수 시각화 
<img src="https://github.com/dosel70/MachineLearning-Project/assets/143694489/5a2d66e0-9bbf-4136-b2bf-44e024e2863a" width="800px">
  
- Threshold 0.4 결과   
<img src="https://github.com/dosel70/MachineLearning-Project/assets/143694489/b5e3eff7-297a-430e-8657-98beaad752b5" width="800px">    

- Threshold에 따른 정밀도 , 재현율 추이 시각화  
<img src="https://github.com/dosel70/MachineLearning-Project/assets/143694489/51411870-7fd4-4264-8330-9e4c0406c6db" width="800px">    

- ROC curve 시각화 
<img src="https://github.com/dosel70/MachineLearning-Project/assets/143694489/c679a5c2-0381-4e30-a40d-9cf56c2cd7bd" width="800px">   

## Total Result
- ### ✨ 최종결론  
<img src="https://github.com/dosel70/MachineLearning-Project/assets/143694489/7fed9fce-49ad-404d-bb30-20d99cda117f" width="800px">  


- 로지스틱 회귀기법을 사용해서 lda 차원축소를 한 결과 임계치를 0.4로 낮출 경우 정확도 점수는 기존과 동일 하지만 나머지 F1 Score와 재현율이 높아지므로  

- 임계치를 0.4로 낮출 때 최적의 결과를 얻을 수 있었습니다.  

[맨위로 이동](#관상동맥-질환-환자-예측-분류-분석-프로젝트)

