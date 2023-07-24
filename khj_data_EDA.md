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



## 
