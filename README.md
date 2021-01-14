# AI_project
 
## 일지
|Date|Description|Official source(참고 주소)|
|:---:|---| --- |
|01.07|Data request|[질병관리본부](https://chs.cdc.go.kr/chs/rdr/rdrInfoDownMain.do)에 자료 신청|
|01.11|1차 EDA 전처리||
|01.12|2차 EDA 전처리||
||[BMI 지수를 적용하고 10-13년도와 14-17년도까지의 칼럼 동일화](https://github.com/gini7752/AI_project/blob/main/data/README.md)||
|01.13|모델링||
||LinearRegression, RandomForest, DNN 모델 제작 |DNN 모델에서 에러 발생하여 미해결|
|01.14|DNN 모델 완성|종속변수의 클래스가 3개라서 분류 모델로 만들었는데 정확도가 낮음|
|||현재는 회귀 모델로 DNN 완성|
||Randomforest 모델 완성|상관관계가 가장 낮은 칼럼 하나를 제거하고 파라미터를 조정하고 정확도를 높임|