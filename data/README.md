# EDA 전처리 
## 1차 전처리
- txt 파일을 csv 파일로 변환하였다.

### Data columns 확인
```
> busan_19.columns
Out[] : 
Index(['examin_year', 'exmprs_no', 'age', 'sex', 'ctprvn_code', 'pbhlth_code',
       'spot_no', 'hshld_code', 'mbhld_code', 'dong_ty_code',
       ...
       'hwa_05z1', 'hwa_06z1', 'fea_01z2', 'fea_09z1', 'soa_01z1', 'soa_06z1',
       'soa_07z1', 'sob_01z1', 'sob_02z1', 'sod_02z2'],
      dtype='object', length=280)
```

## 2차 전처리

### 비만 관련 칼럼 찾기
> 보건소 번호, 주택유형, 세대유형, 기초생활수급자 여부, 가구소득, 현재 흡연여부, 음주빈도,나이, 성별, 걷기 일수,저염선호 - 평상시 소금섭취 수준, 본인인지체형, 체중조절 시도경험, 키, 체중 주관적 스트레스 수준, 우울감 경험, 자살생각 경험, 고혈압 의사진단여부, 당뇨병 의사진단여부 경제활동여부, 혼인상태 등

### 2008 ~ 2018년까지의 공통 칼럼들 (비만 관련)
> 보건소 번호, 만나이, 성별, 주택유형, 세대유형, 기초생활수급자 여부, 가구소득, 현재 흡연 여부, 연간 음주 빈도, 격렬한 신체활동 일수(09~17), 중등도 신체활동 일수(09~17),걷기 실천 일수, 주간 아침식사 일수(10~), 평상시 소금섭취 수준-저염선호(~17), 본인인지체형, 체중조절 경험여부, 키, 몸무게, 수면시간, 주관적 스트레스 수준, 우울감 경험 여부, 고혈압 현재 치료 여부(~17), 당뇨병 현재 치료 여부(~17), 관절염 현재 치료 여부(~17), 혼인상태 <br>
> 'bogun_cd','age','sex','apt_t','fma_19z1','fma_04z1','fma_24z1','sma_03z2','drb_01z2',
'pha_04z1','pha_07z1','phb_01z1','nua_01z1','nub_01z1','oba_01z1','obb_01z1','oba_02z1',
'oba_03z1','mtc_01z1','mta_01z1','mtb_01z1','hya_06z1','dia_06z1','ara_22z1','sod_02z1'
**10 ~ 17년 데이터 사용시 원하는 칼럼 모두 사용가능**

## 종속변수 생성
### BMI 지수 적용
BMI=몸무게/((키/100)\*\*2)
```py
def BMI(A):
    A['Obesity']=A['oba_03z1']/((A['oba_02z1']/100)**2)
```

### 비만여부 다항변수 처리
```py
def Oba(x):
    if x>=25: return 3
    elif x<18.5: return 1
    else: return 2
```

### 전체작업 함수 (기존의 키, 몸무게 칼럼도 제거)
```py
def Change_Oba(A):
    BMI(A)
    A['Obesity'] = A['Obesity'].apply(Oba)
    del A['oba_03z1']
    del A['oba_02z1']
```

## 10-13년과 14-17년 칼럼의 동일화
```py
def change_col(A):
  A["sod_02z1"] = A["sod_02z2"]
  del A["sod_02z2"]
```