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