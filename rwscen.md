# KIDI-ESG Pro를 이용한 보증준비금 시나리오 산출

- 보증준비금 시나리오는 다음 7종으로 구성됨

  - 채권 시나리오
    
    1. 국내 단기채권형 펀드 시나리오
    
    2. 국내 채권형 펀드 시나리오
    
  - 주식 시나리오
  
    1. 국내 주식형 시나리오

    2. 국내 배당주식형 시나리오

    3. 해외 선진국주식형 시나리오

    4. 해외 개도국주식형 시나리오

  - 일반계정 보증준비금 평가를 위한 무위험 수익률 시나리오

- 모수추정 과정의 이해를 위해 엑셀을 통해 모수를 추정

  [모수추정 엑셀 다운로드](https://github.com/dopplix/opendocs/raw/master/calib.xlsx "calib")

- 모수추정 방법은 다음의 보고서를 참고

  [모수추정 방법 문서 다운로드](https://github.com/dopplix/opendocs/raw/master/report.pdf "report")
  
# 채권 시나리오

- 보증준비금 채권 시나리오는 MEV모형을 사용하며 과거 데이터를 사용하여 산출하며 모수 추정방식은 보고서의 43페이지를 참고

![26](https://user-images.githubusercontent.com/31100072/90069239-ff50b400-dd2c-11ea-9eff-b3597d1d5a40.png)

## 데이터 수집

- 데이터 출처: 금융투자협회 채권정보센터 http://kofiabond.or.kr/

- 시가평가 - 채권시가평가기준수익률

![7](https://user-images.githubusercontent.com/31100072/89998764-eb736680-dcc8-11ea-9905-55899dd97045.png)

- 날짜 입력 후 "조회" 버튼 클릭

![8](https://user-images.githubusercontent.com/31100072/89999165-65a3eb00-dcc9-11ea-9f33-ee23c500106b.png)

- 데이터 수집

![9](https://user-images.githubusercontent.com/31100072/89998783-f0d0b100-dcc8-11ea-9ccf-c0f0a3e3d793.png)

- 엑셀 입력

![5](https://user-images.githubusercontent.com/31100072/89999647-098d9680-dcca-11ea-9e6e-884c275aa1a7.png)

## 시나리오 산출

- 위험중립모듈 실행

![1](https://user-images.githubusercontent.com/31100072/89999857-5cffe480-dcca-11ea-9dcd-3ea6f8f55c9f.PNG)

- 금리모형 모수 추가

  각 금리에 해당하는 금리모형 모수 추가
  
  - 모형 : IR_MEV모형
  
  - 모수집합 이름
    
    1. KTB3M
    
    2. KTB5Y
    
    3. PFB3Y
    
![2](https://user-images.githubusercontent.com/31100072/90000053-9f292600-dcca-11ea-8382-4cff0cc0c724.PNG)

- 난수 생성

  각 금리에 해당하는 난수 추가
  
  - 난수 생성방법: KIDI Random Number
  
  - Select
  
    1. KTB 3m
    
    2. KTB 5Y
    
    3. PFB 3Y

- 시나리오 모수 입력

  모수 산출 엑셀에서 생성된 모수를 입력
  
  - 엑셀
  
  ![4](https://user-images.githubusercontent.com/31100072/90000401-165eba00-dccb-11ea-8a9a-cf27aae68286.png)
  
  - ESG

  ![6](https://user-images.githubusercontent.com/31100072/90000285-ec0cfc80-dcca-11ea-9443-008529ae7fb3.PNG)
  
- 금리 시나리오 생성
  
  모수집합과 난수의 이름을 맞추어 각 시나리오를 생성
  
![10](https://user-images.githubusercontent.com/31100072/90001038-e5cb5000-dccb-11ea-84c0-fa11ac4910df.PNG)

- 채권 시나리오 생성

  모수집합과 난수의 이름을 맞추어 각 시나리오를 생성 
  
  - 듀레이션
  
    1. KTB 3M: 0.25
    
    2. KTB 5Y: 3.8
    
    3. PFB 3Y: 2.5
    
![11](https://user-images.githubusercontent.com/31100072/90001048-e95ed700-dccb-11ea-89ea-c3978f78ad9f.PNG)

- 채권펀드 시나리오 생성

  1. 국내단기채권형: 위에서 산출한 KTB 3M에 해당하는 채권 시나리오
  
  2. 국내채권형: 엑셀을 사용해 각 셀을 KTB5Y x 0.4 + PFB3Y x 0.6으로 병합

# 주식 시나리오

- 보증준비금의 주식 시나리오는 LN모형을 사용하며 모수 추정 방식은 보고서의 44-47페이지를 참고

![27](https://user-images.githubusercontent.com/31100072/90069734-adf4f480-dd2d-11ea-8aa0-ce303a4d0fe6.png)
![28](https://user-images.githubusercontent.com/31100072/90069741-b0efe500-dd2d-11ea-9c59-b272eb6c21cf.PNG)
![29](https://user-images.githubusercontent.com/31100072/90069749-b2211200-dd2d-11ea-8af1-63b316f73126.PNG)
![30](https://user-images.githubusercontent.com/31100072/90069753-b3ead580-dd2d-11ea-9f02-e5df65612a7c.PNG)

## 데이터 수집

### 국내데이터

- 데이터 출처: 한국거래소 http://www.krx.co.kr/

- 국내주식형 : KOSPI

![12](https://user-images.githubusercontent.com/31100072/90065456-46d44180-dd27-11ea-8381-65d68b589476.PNG)
![13](https://user-images.githubusercontent.com/31100072/90065460-48056e80-dd27-11ea-84f8-ab30b3d20012.PNG)
![14](https://user-images.githubusercontent.com/31100072/90065463-49cf3200-dd27-11ea-9eef-a02e6c10f42b.PNG)

- 국내배당주식형: KOSPI 배당성장 50

![15](https://user-images.githubusercontent.com/31100072/90065468-4b005f00-dd27-11ea-8130-d4af29c27e2a.PNG)
![16](https://user-images.githubusercontent.com/31100072/90065478-4d62b900-dd27-11ea-9919-e0898c0a339f.PNG)
![17](https://user-images.githubusercontent.com/31100072/90065760-b5190400-dd27-11ea-9b04-70d3cee4bc47.PNG)

### 해외데이터

- 블룸버그 티커

  - 해외선진국형: GDDUWI
  
  - 해외개도국형: GDUEEGF

### 데이터 입력

![18](https://user-images.githubusercontent.com/31100072/90065927-f5788200-dd27-11ea-8dea-f5c5a0fbe381.PNG)


## 시나리오 산출

- 모수집합 추가 후 이름 입력

  - 국내주식형: KOSPI
  
  - 국내배당주식형: GD50

  - 해외선진국형: WORLD

  - 해외개도국형: EM

![20](https://user-images.githubusercontent.com/31100072/90067080-8ef46380-dd29-11ea-9c73-a34ee71c6d45.png)

- 각 데이터에 해당하는 난수 불러오기

![21](https://user-images.githubusercontent.com/31100072/90067091-91ef5400-dd29-11ea-83b4-830b55327c69.png)

- 모수추정 엑셀로부터 산출된 모수 입력

![19](https://user-images.githubusercontent.com/31100072/90067450-16da6d80-dd2a-11ea-983b-a91fd5997d4b.png)
![22](https://user-images.githubusercontent.com/31100072/90067110-974c9e80-dd29-11ea-9250-83a3af454f6e.png)

- 각 데이터에 해당하는 난수 선택 후 시나리오 생성

![23](https://user-images.githubusercontent.com/31100072/90067131-99aef880-dd29-11ea-82d8-3756c150d587.png)

- 생성결과 

![24](https://user-images.githubusercontent.com/31100072/90067139-9c115280-dd29-11ea-9ae0-be28975c9e2a.png)

# 일반계정 보증준비금 무위험수익률 시나리오

- 채권시나리오 산출 시 생성한 국고5년 금리시나리오를 저장

![25](https://user-images.githubusercontent.com/31100072/90067785-936d4c00-dd2a-11ea-8d07-5c18b1793326.png)

