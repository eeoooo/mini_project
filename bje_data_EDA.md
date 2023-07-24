### 들어가기에 앞서 개념 정리 
지도학습 : 문제와 정답을 모두 알려주고 공부시키는 방법
    ex) 예측, 분류(범주형), 회귀(수치형)
* 분류(Classification): 승/패, 생존여부 등과 같이 범주형 데이터를 결과 예측 할 떄 사용한다.
* 회귀(Regressing): 몸무게, 아파트 가격과 같이 수치형 데이터를 에측할 때 사용한다.
* Mean Absolute Error(MAE): 실제 값과 예측 값 사이의 절대 값을 변환해 평균을 구한 것
* Root Mean Squared Error(RMSE): 오차 제곱의 평균값이 제곱근

#EDA 과정(1) 데이터 파악

### 1. sales_train
- 2935849 rows × 6 columns
-    Column          Dtype  
---  ------          -----  
 0   date            object : 매출 날짜
 1   date_block_num  int64  : 번호 매겨진 매출발생 월
 2   shop_id         int64  : 가게 ID
 3   item_id         int64  : 상품 ID
 4   item_price      float64: 상품 가격
 5   item_cnt_day    float64: 상품 
                            
### 2. shops
- 60 entries x 2 columns
-    Column     Non-Null Count  Dtype 
---  ------     --------------  ----- 
  0   shop_name  60 non-null     object: 가게명(상호명)
  1   shop_id    60 non-null     int64 : 가게 ID


  
