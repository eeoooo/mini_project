## ✔️데이터 파악


### 1. sales_train <br>
`2935849개 columns- 6개`       
|컬럼명|type|설명|
|----|---|---|
|date|object|날짜를 일, 월, 년 순|
|date_block_num|int|2013년 1월은 0, 2월은 1 총 33개까지 년과 월을 숫자로 표시|
|shop_id|int|상점ID|
|item_id|int|상품ID|
|item_price|float|상품 가격(소수점으로 표시)|
|item_cnt_day|float|일일판매? 1.0, -1.0으로 표시|





### 2. items <br>
`22170개, columns- 3개`
|컬럼명|type|설명|
|----|---|---|
|item_name|object|상품명 - 러시아어로 되어있고 매우 길다.|
|item_id|int|상품ID인데, sales_train에 상품ID와 다른 점은 번호랑 같이 내려간다는 점?|
|item_category_id|int|상품분류ID|




### 3. item_categories <br>
`84개, columns- 2개`
|컬럼명|type|설명|
|----|---|---|
|item_category_name|object|상품 분류 이름|
|item_category_id|int|위 items에 item_category_id와 다른 점은 번호 나열하듯이?|





### 4. sample_submission <br>
`214200개, columns- 2개`
|컬럼명|type|설명|
|----|---|---|
|ID|int|번호랑 같이 나열|
|item_cnt_month|float|상품 월별 판매?|




### 5. shops <br>
`60개, columns- 2개`
|컬럼명|type|설명|
|----|---|---|
|shop_name|object|가게이름|
|shop_id|int|번호대로 나열|





### sales_test <br>
`214200개, columns- 3개`
|컬럼명|type|설명|
|----|---|---|
|ID|int|번호순으로 나열|
|shop_id |int|상점ID - 5와 45로 구성?|
|item_id|int|상품ID - describe로 확인 했을 때, 최저는 30 최고 22167|



## ✔️ 1~5 까지 데이터를 어떻게 합쳐야할까?
  👉🏻 데이터파일 - 컬럼명
  items-item_id, item_categories-item_category_id, sample_submission-ID, shops-shop_id 
  다른 컬럼들과 다르게 번호대로 쭉 나열 되는거 보면, 이런 컬럼들은 drop 해도 될거 같다.
  
  👉🏻 autoML돌리기 위해 인터넷에 있는 데이터 합치기를 참고했음.

  
## ✔️ 사용할 모델
  👉🏻 `pycaret.regression` 회귀분석 예측을 선택
   target - 'item_cnt_day' 
   <br>
          * 월별 금액 <br>
          * 총 판매금액 

  👉🏻 회귀모델의 성능 평가 지표 <br>
    * MAE(Mean Absolute Error) : 모델의 예측값과 실제값의 차이의 절대값의 평균 <br>
    &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;
    절대값을 취하기 때문에 가장 직관적으로 알 수 있는 지표
  
   * MSE(Mean Squared Error) : 제곱을 하기 때문에 특이치(Outlier)에 민감
   * RMSE(Root Mean Squared Error) : 일반적으로 많이 쓰이는 회귀모델 성능분석지표(MAE와 함께)
   * R2 : 값이 1에 가까울 수록 성능이 좋음
   * RMSLE : 상대적 error 측정, 
   * MAPE(Mean Absolute Percentage Error) = 평균 절대 비율 오차 : 직관적, 에러율 비교 쉬움

<hr/>

     **0에 가까울 수록 좋은 성능 : MSE, MAE, RMSE, RMSLE**
     
     **1에 가까울 수록 좋은 성능 : R2**
