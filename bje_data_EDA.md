### 들어가기에 앞서 개념 정리 
* 지도학습 : 문제와 정답을 모두 알려주고 공부시키는 방법
    ex) 예측, 분류(범주형), 회귀(수치형)
* 분류(Classification): 승/패, 생존여부 등과 같이 범주형 데이터를 결과 예측 할 떄 사용한다.
* 회귀(Regressing): 몸무게, 아파트 가격과 같이 수치형 데이터를 에측할 때 사용한다.
* Mean Absolute Error(MAE): 실제 값과 예측 값 사이의 절대 값을 변환해 평균을 구한 것
* Root Mean Squared Error(RMSE): 오차 제곱의 평균값이 제곱근

# EDA 과정 데이터 파악

### 1. sales_train
- 2935849 entries × 6 columns
-    Column          Dtype  
---  ------          -----  
	 0   date            object : 매출 날짜
	 1   date_block_num  int64  : 번호 매겨진 매출 발생 월
	 2   shop_id         int64  : 가게 ID
	 3   item_id         int64  : 상품 ID
	 4   item_price      float64: 상품 가격
	 5   item_cnt_day    float64: 상품 
                            
### 2. shops
- 60 entries x 2 columns
---  ------     --------------  ----- 
	  0   shop_name  60 non-null     object: 가게명(상호명)
	  1   shop_id    60 non-null     int64 : 가게 ID

### 3. items
- 22170 entries x 3 columns
---  ------            --------------  ----- 
	 0   item_name         22170 non-null  object : 상품 이름
	 1   item_id           22170 non-null  int64  : 상품 ID
	 2   item_category_id  22170 non-null  int64  : 상품 카테고리 ID

 ### 4. item_categories
- 84 entries x 2 columns
---  ------              --------------  ----- 
	 0   item_category_name  84 non-null     object : 상품 카테고리 이름
	 1   item_category_id    84 non-null     int64  : 상품 카테고리 ID

 ### 5. test
 - 214200 entries x 3 columns
---  ------   --------------   -----
	 0   ID       214200 non-null  int64 : 테스트 ID
	 1   shop_id  214200 non-null  int64 : 가게 ID
	 2   item_id  214200 non-null  int64 : 상품 ID

 ### 6. submission
 - 214200 entries x 2 columns
---  ------          --------------   -----  
 	0   ID              214200 non-null  int64   : 승인 ID
 	1   item_cnt_month  214200 non-null  float64 : 상품 

 ### 6개 테이블 정리
 - Null 값 존재하지 않음
 - 많은 양의 데이터, 월별로 요약할 필요
 - 월별 매출액 계산 필드 필요

## 데이터 양상 시각화 코드
#### 1. 월별 총 상품 판매량 막대그래프

![image](https://github.com/eeoooo/mini_project/assets/133926006/3a7b049e-088d-49a1-97a7-84cd77731e19)

#### 2. 상품 카테고리별 총 상품 판매량 막대그래프

![image](https://github.com/eeoooo/mini_project/assets/133926006/5202d73f-1114-49d8-985b-1e4cfc0db42b)

#### 3. 가게별 총 상품 판매량 막대그래프

![image](https://github.com/eeoooo/mini_project/assets/133926006/dae24ce5-2905-482a-bc0c-a7766dce5177)

* 개인적 견해: 추세가 보이는건 월별 총 상품 판매량 막대그래프

## 데이터 전처리


## 어떤 판매량 예측?
#### 1. 월별 총 판매 금액 예측
- 월 ID / 가게 ID / 상품 ID / 상품 금액 / 총 판매 수량 / 총 판매 금액

#### 2. 월별 상품별 총 판매 금액 예측
- 월 ID / 상품 ID / 상품 금액 / 총 판매 수량 / 총 판매 금액 

#### 3. 상품 카테고리별 판매 예측
- 월 ID / 상품 카테고리 ID / 상품 ID / 상품 금액 / 총 판매 수량 / 총 판매 금액

#### 4. 가게별 판매 매출
- 월 ID / 가게 ID / 상품 ID / 상품 금액 / 총 판매 수량 / 총 판매 금액

#### 5. 계절별 판매 매출

#### 월별 총 판매 금액 예측을 하는게 어떨까..?

## 어떤 기준으로 평가?(회귀/시계열 데이터)
#### 회귀
- MAE (Mean Absolue Error): 실제 값과 예측 값의 차이를 절댓값으로 변환해 평균한 것
- MSE (Mean Squared Error): 실제 값과 예측 값의 차이를 제곱해 평균한 것
- RMSE (Root Mean Squared Error):
  * MSE 값은 오류의 제곱을 구하므로 실제 오류 평균보다 더 커지는 특성이 있어 MSE에 루트를 씌운 RMSE 값을 쓰는 것입니다.
- MSLE (Mean Squared Log Error):
  * MSE에 로그를 적용해준 지표입니다.
  * log(y)가 아니라 log(y+1), y=0일 때, log(y)는 마이너스 무한대이므로 이를 보정해주기 위해 +1을 한 것.
- RMSLE (Root Mean Squared Log Error): RMSE에 로그를 적용해준 지표
- R² (R Sqaure):
  * 분산 기반으로 예측 성능을 평가합니다. 1에 가까울수록 예측 정확도가 높음
  * R² = 예측값 Variance / 실제값 Variance

#### 참고)분류 평가지표
- 정확도(precision)
- 재현율
- F1 함수

## 어떤 알고리즘을 사용하여 예측?

#### 1. 결정트리(Decision Tree)

#### 2. 랜덤 포레스트(Random Forest)

### 베이스라인 모델

#### 3. XGBOOST


#### 4. LightGBM
- Leaf-wise를 사용하면 훨씬 더 빠르게 optimal을 찾을 수 있음
- 길이가 너무 커지면 overfitting될 가능성이 높아  Level을 제한하여 최대한 모델 키우기
- 월별 패턴 파악: tree based로 예측이 용이할 것으로 보임
- 
	| [LightGBM] | [Info] | Start training from score 0.299125 |
	|----|---|---|
  	[50]|	training's rmse: 1.14777|	valid_1's rmse: 1.06755|
  	[100]|	training's rmse: 1.11425|	valid_1's rmse: 1.0386|
  	[150]|	training's rmse: 1.09673|	valid_1's rmse: 1.02671|
  	[200]|	training's rmse: 1.08573|	valid_1's rmse: 1.02027|
  	[250]|	training's rmse: 1.07722|	valid_1's rmse: 1.01661|
  	[300]|	training's rmse: 1.0698	|	valid_1's rmse: 1.0138|
  	[350]|	training's rmse: 1.06317|	valid_1's rmse: 1.01084|
  	[400]|	training's rmse: 1.05734|	valid_1's rmse: 1.00936|
  	[450]|	training's rmse: 1.05224|	valid_1's rmse: 1.00818|
  	[500]|	training's rmse: 1.04792|	valid_1's rmse: 1.00722|


#### 5. CatBOOST
 - 최근 가장 많이 사용되는 알고리즘 중 하나
