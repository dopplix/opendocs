# KIDI-ESG Pro를 용한 보증준비금 시나리오 산출

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

# 채권 시나리오

## 데이터 수집

- 금융투자협회 채권정보센터: http://kofiabond.or.kr/

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

  1. 국내단기채권형: 위에서 산출한 KTB 3M의 채권 시나리오와 동일
  
  2. 국내채권형: KTB5Y 시나리오와 PFB3Y 시나리오를 4:6으로 병합
  
    엑셀을 통해 각 셀을 KTB5Y x 0.4 + PFB3Y x 0.6을 계산
    
# 주식 시나리오



# 무위험수익률 시나리오
