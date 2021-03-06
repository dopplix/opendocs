# Qt 개발환경 구축

## 개요

Qt는 C++ 기반의 라이브러리로써 UI 뿐 아니라 프로그래밍 시 필요한 각종 도구들을 집약해 놓은 프레임워크(네트워크, 병렬처리, 이미지 등)

Qt는 C++ 기반으로 작동하므로 C++ 컴파일러가 필요

컴파일러는 사람이 읽을 수 있는 프로그램 코드를 컴퓨터가 읽을 수 있는 언어로 변환해주는 도구임

C++ 컴파일러 중 대표적인 Microsoft Visual C++ Compiler(이하 MSVC)를 설치 할 것

MSVC는 Microsoft Visual Studio를 설치하면 자동으로 설치됨

## Microsofut Visual Studio 설치

- Visual Studio Community 버젼을 설치
  
  - Visual Studio의 무료 버젼임
  
  https://visualstudio.microsoft.com/ko/vs/community/

- cpp 참고 : ntu.edu.sg/home/ehchua/programming/cpp/cp0_Introduction.html

- C++을 사용한 데스크톱 개발 선택

  - 우측의 옵션은 Qt Creator와 연동하기 위한 최소의 옵션
  
![2](https://user-images.githubusercontent.com/31100072/91376985-6015db80-e859-11ea-80ab-eb4c4168bb83.PNG)

- 이후의 옵션은 모두 Default로 설치 진행

![3](https://user-images.githubusercontent.com/31100072/91376986-6015db80-e859-11ea-8501-b43027eb783d.PNG)

## Qt Creator 설치

- Qt Opensource 버젼 다운로드
  
  https://www.qt.io/download-qt-installer

- E-mail 등록 및 계정 설정

![4](https://user-images.githubusercontent.com/31100072/91376988-60ae7200-e859-11ea-8f39-93cf76aefd26.PNG)

- 설치 진행

![5](https://user-images.githubusercontent.com/31100072/91376989-60ae7200-e859-11ea-833d-b6a664ca1620.PNG)

- 경로 설정

![6](https://user-images.githubusercontent.com/31100072/91376992-61470880-e859-11ea-89f6-8e5d6239586c.PNG)

- 다음의 옵션을 선택

  - TODO: 각 모듈에 대한 설명
  
![7](https://user-images.githubusercontent.com/31100072/91376993-61470880-e859-11ea-9e29-91787ce6d716.PNG)

- 라이센스 동의

![8](https://user-images.githubusercontent.com/31100072/91376994-61df9f00-e859-11ea-9b44-9838e5384fcf.PNG)

> 2020-08-26 현재 위와 같이 설치 시 MSVC 14.2와 Qt 5.15가 설치되어 별도의 설정을 하지 않아도 Qt Creator에서 MSVC가 자동으로 연동 됨
