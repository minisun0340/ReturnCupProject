# 카페 일회용 컵(플라스틱 컵) 보증금 반환기
### 융합프로젝트(IoT, AI, Bigdata, Cloud) in MultiCampus

#### 팀
BeanCup
#### 팀원
IoT : 김민선, 허소연
AI : 김태호, 석병길, 이창훈, 장성원
Bigdata : 강지우, 이영준
Cloud : 여동엽

### 프로젝트 설명
#### 1. 프로젝트 주제
일회용컵 보증금제를 보완할 수 있는 무인 회수기

#### 2. 주제 선정 배경 및 이유
##### 배경
* 2008년 한 번 시행되었으나 참여율 저조로 실패
* 연간 플라스틱컵 사용량 지속적 증가(2007년 대비 2022년 6배 상승)
* 회수율 5% 남짓, 자원 낭비, 환경 오염 악화
* 12/2 일회용컵 보증금 제도 재도입
##### 이유
정부가 제시하는 보증금 제도 방식은 
보증금 대상 사업자(카페 운영자)는 라벨 구입, 일회용컵에 부착, 소비자에게 판매
소비자는 보증금 포함 구매 금액을 지불, 보증금 대상 사업자 또는 무인회수기로 컵 반환, 보증금 반환

위의 과정에서 라벨 또한 자원 낭비이며, 사업자의 라벨 비용 부담 및 노동력 부담 등의 문제가 있다.
이를 해결하기 위해 빈컵 프로젝트에서는 라벨링을 쓰지 않고 AI를 활용하여 브랜드 이름 인식하고, IoT장비를 이용하여 자동 세척 기능을 포함한다. 

#### 3. 프로젝트 계획
<img width="400" alt="계획" src="https://user-images.githubusercontent.com/99372135/181041513-092ec814-4f74-4059-bd4f-05d5ea55b1bd.png">

#### 4. 아키텍처
<img width="400" alt="순서도" src="https://user-images.githubusercontent.com/99372135/181041607-215652b0-9d55-4ca7-a56a-85a3a36788c3.jpg">
<img width="400" alt="통신" src="https://user-images.githubusercontent.com/99372135/181041721-d64d92c4-c5f8-4834-8c39-82eed40b4d60.png">

 * IoT
  ** 웹
     - restAPI 구성하여 kiosk, 앱과 http 통신
  ** 앱(kiosk)
     - 컵 사진 표시
     - http통신을 통해 사용자 정보 가져오기
     - mqtt를 통해 라즈베리파이 #1,2 작동
  ** 앱(사용자용)
     - 사용자 가입
     - 적립 내역 확인
  ** 라즈베리파이 #1
     - pi camera, push button과 연결
     - mqtt통신으로 사진 전송
     - 상태 good/bad, 브랜드인식(starbucks, Ediya, Twosome) 가능한 AI모델 이식(tensorflow lite)
  ** 라즈베리파이 #2
     - arduino와 serial 통신
     - arduino에 워터펌프 연결하여 컵 세척
     - servo모터로 브랜드에 따라 컵 분류
 * AI
 * Bigdata
 * Cloud
 
#### 5. 테스트 시나리오
1. 키오스크의 시작하기 버튼을 누른다.
2. 안내 음성에 따라 뚜껑, 빨대, 홀더 등을 제거한다.
3. 화면에 브랜드가 인식되도록 가져다 댄 후 버튼을 누른다.
4. 인식된 브랜드와 실제 컵의 브랜드가 일치하면 확인 버튼을 누른다.
5. 안내음성에 따라 입구에 컵을 넣는다.
6. 키오스크에 휴대폰 번호를 입력한다.
7. 본인의 이름이 맞다면 확인 버튼을 누른다.
8. 포인트 적립 완료

#### 6. 시연 영상
![image](https://user-images.githubusercontent.com/99372135/181046362-23bc2d5b-b81b-476c-8b03-54cafc31dd6c.png)

Click [here](https://youtu.be/cPqC5afyG90)

