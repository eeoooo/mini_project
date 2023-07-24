# 이우윤 데이터 EDA

### sales_train

rows : 2935849개

cols : ['date', 'date_block_num', 'shop_id', 'item_id', 'item_price', 'item_cnt_day'] : 6개

	date  : ( 기간 어떻게 되는지 ?? )  :  (시계열 데이터임을 추측 가능)
	date_block_num : int : 33 종류 : (각각에 들어간 항목 개수는 우선순위 불분명)
	shop_id : int : 60 종류 : (각각에 들어간 항목 개수는 우선순위 불분명)
	item_id : int : 21807 종류 : (각각에 들어간 항목 개수는 우선순위 불분명)
	item_price : float : 19993 종류 
        item_cnt_day : float  : ( 뭔 내용 ?? )

### shops

rows : 60개

cols : [shop_name, shop_id] : 2개

	shop_name : 러시아어로 이루어진 문자열
			: 맨 앞이 지역이름인가 ? 
			: 공백, 특수문자를 포함함
	shop_id : 0 ~ 59 오름차순 정렬 인덱스 숫자

### items

rows : 22170개

cols : [item_name, item_id, item_category_id] : 3개 

	item_name : 러시아어로 이루어진 문자열
	item_id : 숫자변수 : 0~22169 오름차순 정렬 인덱스 숫자
	item_category_id : 숫자변수 : 84개
			: (value_counts 찍어봤을 때) id가 40 : 5035개 최대, id 79 : 1개 최소

### item_categories

rows: 84개 

cols : [item_categories_name, item_category_id] : 2개

	item_categories_name : 러시아어로 이루어진 문자열
	item_category_id : 0 ~ 83 오름차순 정럴 인덱스 숫자

### test

rows: 214200 개

cols : [ID, shop_id, item_id]

	ID : 숫자변수 : 0 ~ 214199 까지 오른차순 정렬 인덱스 숫자
	shop_id : 42개 종류 * 5100개씩
	item_id : 5100개 종류 * 42개씩

### submission

rows : 214200 개

cols : [ID, item_cnt_month]

	ID : 숫자변수 : 0 ~ 214199 까지 오름차순 정렬 인덱스 숫자
	item_cnt_month : 214200개 모두 0.5 값으로 이루어짐
