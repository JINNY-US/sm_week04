# sm_week04
스마트모바일프로그램설계 4주차   

### 팀 구성   
스마트정보통신공학과 201621216 이준석   
스마트정보통신공학과 201921036 김경진   
스마트정보통신공학과 201921054 박유리   
스마트정보통신공학과 201921083 이혜정   
스마트정보통신공학과 201921104 홍수빈    
스마트정보통신공학과 201990009 미르자크메더브 사르더르    
   ***   
### 모든 항목은 변경되거나 삭제될 여지가 있습니다   
   ***   


## 어디가게

커플 혹은 친구들끼리 놀러갈 때나 여행할 때 주변에 놀만한 곳, 맛있는 음식이 있는 곳을 찾기 힘들 때를 대비하여 정해진 예산과 지역, 목적을 입력하여 주변에서 가장 가까운 곳, 혹은 목적과 가장 유사한 곳을 추천해주는 앱입니다.   

### (1) 기능과 특징 

1. 지역과 목적(ex. 홍대 or 영화, 음식점)을 입력하면 사용자의 주변에 목적과 유사한 가게들을 추천합니다.
2. 사람들이 많이 사용한다고 생각하는 음식점, 카페, 옷가게, 영화관으로 설정했으며 이후에 더 추가될수도 있습니다.
3. 사용 가능한 예산과 인원, 시간대, 해시태그 기능을 사용하여 사용자의 목적과 유사한 추천목록을 제공합니다. 또한, 가능하다면 예약하기 기능도 넣어서 대기시간 없이 즐길 수 있도록 할 예정입니다.
4. 각 분야에 따라 게시판을 생성하여 유저들 간의 소통이 활발하게 이루어지도록 만들 예정입니다. (ex. 맛집 추천, 영화 리뷰, 같이 밥 먹을 사람 구하기 등)
5. 추천탭 상단에 가게의 광고를 추가하여 홍보할 수 있는 수단을 만들 예정입니다.   
6. 리뷰 기능을 넣어 가게의 상태와 서비스 등을 평가할 수 있습니다.   
7. GPS를 사용하여 거리를 측정하고 가는 길을 표시합니다.   

***   

### (2) 앱 로고 및 배경   

![어플 2차 최종(확정)](https://user-images.githubusercontent.com/57963888/111958828-0e081080-8b31-11eb-92ba-2386b7edae8f.png)
![배경 최종(확정)](https://user-images.githubusercontent.com/57963888/111959121-63dcb880-8b31-11eb-85d9-a2c3607e9139.png)   

***   

### (3) 대략적인 데이터 테이블

#### 1. 회원 테이블   
- 이름 char (10)   
- 닉네임 char (15)   
- 아이디 char (20)   
- 비밀번호 char (20) : textPassword   
- 이메일1 char (10)   
- 이메일2 char (20) : comboBox(선택가능)   
- 이메일 char (25) : 이메일1@이메일2 ex) 201921036@smu.ac.kr   
- 업주여부 bool : radioButton   
- 나이 int : 주점, 술집 필터링 용도   

   

#### 2. 가게 테이블   
- 지역 : ~도, ~시   
- 가게 종류 : 옷가게, 식당, 카페, 영화관, 노래방, 화장품가게, 편의점, 팬시점 등   

> 옷가게 : 남성복, 여성복, 아동복   
> 식당 : 한식, 중식, 일식, 양식, 분식, 주점   

- 메뉴 평균 가격 : 범위를 옵션으로 설정   
- 상세주소 text not null
- 광고 여부 bool : radioButton
- 가게 설명 : 업주가 직접 작성   
- 영업시간
- 가게 이미지
- 가게 번호 not null auto_increment

   
   
#### 3. 게시판 테이블   
- 작성자 이름 : 회원 테이블의 닉네임   
- 작성자 ID : 회원 테이블의 아이디   
- 제목 char (200)   
- 내용 text not null   
- 작성 날짜 char (20)   
- 게시판 종류 : 음식점, 카페, 영화관, 옷가게 등   

      

#### 4. 후기 테이블   
- 작성자 이름 : 회원 테이블의 닉네임   
- 작성자 아이디 : 회원 테이블의 아이디   
- 제목 char (200)   
- 내용 text not null   
- 작성 날짜 char (20)   
- 별점 : 1~5까지 고를 수 있음
- 사진 첨부 : 선택 

***   

### (4) 기타 설정   

시간대 옵션   
-> 조건문으로 필터링   
-> 아침, 점심, 저녁으로 나누고 사용자가 선택하는 방법   
-> 시간대에 맞는 가게를 상단으로 올림   
ex) 저녁 선택 -> 주점, 노래방 등을 추천   
    점심 선택 -> 음식점, 옷가게 등을 추천   

시간대
- 오전 9시 ~ 오후 12시 (아침)   
-> 점심 식당, 카페, 영화관 추천   

- 오후 1시 ~ 오후 6시 (점심)   
-> 점심 식당, 카페, 옷가게, 영화관, 팬시점, 화장품 가게 추천   

- 오후 7시 ~ 오후 10시 (저녁)   
-> 저녁 식당, 카페, 영화관, 화장품 가게 추천   

- 오후 11시 ~ 오전 2시 (밤)   
-> 술집, 노래방    

- 설정 안 함
-> 모든 가게 (편의점 포함)

검색 기능   
-> 검색어 : textBox   
-> 시간대 : comboBox   
-> 위치 : comboBox   
-> 해시태그   
-> 예산(금액) : comboBox   
-> 가게 종류 : comboBox   
-> 나이 : 미성년자에게 술집을 추천하지 않음   

***   

### (5) 안드로이드 스튜디오와 데이터베이스 연동 가능한 서1   

#### 1. Amazon Web Services (AWS)   

아마존에서 제공하는 유료 서비스 : ( https://aws.amazon.com/ko/ )   

AWS (Amazon Web Service)는 전 세계적으로 분포한 데이터 센터에서 200개가 넘는 완벽한 기능의 서비스를 제공하는, 세계적으로 가장 포괄적이며, 널리 채택되고 있는 클라우드 플랫폼입니다.

 - 서버구축 : 웹서버를 마련하기 위해서는 EC2를 사용하여야 하는데 EC2는 Elastic Compute Cloud의 약어이며 웹 서비스 인터페이스를 사용해 다양한 운영 체제로 인스턴스를 시작하고, 이를 사용자 정의 애플리케이션 환경으로 로드하며, 네트워크의 액세스 권한을 관리하고, 원하는 수의 시스템을 사용해 이미지를 실행할 수 있는 진정한 가상 컴퓨팅 환경을 제공합니다.
 일단 1. 가입을 먼저 한 후에 2. AMI를 선택하고 3. 인스턴스 유형을 선택하고 4. 인스턴스 세부 정보를 구성합니다. 그 후 5. 스토리지와 태그를 추가하고 6. 보안그룹 작성을 하는데 이 때 한글로 작성을 하면 잘 안될 수도 있기 때문에 영어로 작성하는 것이 좋고 7. 인스턴스의 비밀번호와 같은 페어를 지정합니다. 그러면 EC2에서 웹서버를 구동하는데 이때 키페어가 사용되고 원격 데스크톱이 연결됩니다. 
인스턴스 가상서버는 서버만 가상으로 생성된 것 뿐 웹서버가 만들어 진 것이 아니기 때문에 8. 리눅스 서버에 접속을 하여 SSH 터미널에 접속하고 9. 콘솔에서 환경을 구축해주면 nginx 라는 웹서버가 설치되고 10. 웹서버 서비스 포트를 열어주고 규칙을 저장해주면 가상서버가 웹서버로 바뀝니다. 이 후 인스턴스 요약창에 퍼블릭 주소를 웹브라우저에 넣으면 웹페이지가 뜨는데 그때 뜨는 웹페이지는 가상서버 안에 있는 nignx 웹서버의 메인페이지입니다.
 
 - 장점 : 대시보드와 튜토리얼 같은 부분이 잘되어 있고 서울 쪽에 서버가 존재하기 때문에 한국 IP를 통해 작업이 가능하기 때문에 사용하는데 속도도 빠른 편입니다. 그리고 가상머신을 만들 때도 다른 서비스들보다 속도가 준수한 편이고 프로그램 제공이나 접속방법을 알려주는 등 기본적인 서비스 제공이 좋습니다. 또한 서버를 구축하는 것 뿐 아니라 서버를 폐지하는 것도 쉽고 서버의 규모를 마음대로 조절이 가능합니다. 
 
 - 단점 : 컴퓨터 성능 등 제약이 많다는 점이 AWS를 사용하는 데에 불편할 수 있습니다. 그리고 기존에 제공되는 기능 외에 모든 기능마다 비용이 청구가 되며 사실상 이용할 수 있는 기능은 한정적입니다. 하지만 사용한 만큼만의 리소스에 대해서만 비용을 지불할 수 있고 클라우드 컴퓨팅을 사용하면 소유하고 있는 인프라에서 작업을 수행할 때 보다 가변 비용이 낮습니다.

 - 기능 : Amazon EC2 베어 메탈 인스턴스에서는 애플리케이션이 기본 서버의 프로세서와 메모리에 직접 액세스할 수 있습니다. 이러한 인스턴스는 하드웨어 기능 세트에 액세스해야 하는 워크로드 또는 라이선스나 지원 요구 사항으로 인해 가상화되지 않은 환경에서 실행되어야 하는 애플리케이션에 적합합니다. 릿을 사용하면 단일 API 호출로 EC2 인스턴스 유형, 가용 영역 및 구매 모델에 걸쳐 컴퓨팅 파워를 프로비저닝하여 규모, 성능 및 비용을 최적화할 수 있습니다. 하이버네이트했다가 나중에 이 상태로 다시 시작할 수 있으며 대규모 부동 소수점 처리 능력이 필요한 고객은 최대 8개의 NVIDIA® V100 Tensor Core GPU가 탑재된 AWS의 차세대 범용 GPU 컴퓨팅 인스턴스인 Amazon EC2 P3 인스턴스의 이점을 활용할 수 있습니다. 또한 고밀도 HDD 스토리지 인스턴스와 높은 I/O 인스턴스가 도움이 되고 이러한 다양한 기능들이 장점이 되어 사용자에게 편리함을 줍니다.

AWS를 활용한 사례들에는 “넷플릭스”, “쿠키런”, “직방”, “아모레퍼시픽” 등 이와 같은 서비스들이 있습니다.


#### 2. Google Firebase   

구글에서 제공하는 무료 서비스 : ( https://firebase.google.com/?hl=ko )   

1.파이어베이스란?
파이어 베이스는 개발자가 운영체제에 상관없이 앱을 만들수 있도록 한 툴로
구글의 드라이브와 애널리틱스를 적용해서 어떤 기기에서나 개발할 수 있는 환경을 만들어 주고, 
사용자들의 이용횟수, 광고 효과, 문제 발생 빈도 등을 알려주는 개발자용 프로그램이다.

2.사용 및 연동 방법
1)https://firebase.google.com/ 에 접속 후 회원가입 또는 로그인한다. 
2)프로젝트를 추가한다. 
3)프로젝트 이름 애널리틱스 사용 설정을 해준다.
4)안드로이드 앱을 추가한다.
5)진행중인 안드로이드 프로젝트 이름을 입력해주고 앱 닉네임(선택), SHA-1(선택)을 입력한다. 
6) google-services.json파일을 다운받아  Project -> app 폴더 안에 넣어준다.
7) 다음과 같이 파이어베이스와 SDK를 연결해준다.

![image](https://user-images.githubusercontent.com/79883558/112839947-ba219c80-90d9-11eb-9324-5c26b57ef687.png)   


![image](https://user-images.githubusercontent.com/79883558/112839968-c1e14100-90d9-11eb-8a02-a06b1cd27cb7.png)   


8) 설치확인을 받는다.
9) 안드로이드 스튜디오에서 Tool > firebase Realtime에 들어가 Database > Save and retrieve data 클릭한다. 
이때 2번에 Add the Realtime Database to your app을 클릭해 Accept Changes를 눌러 변경을 해준다. 
1번과 2번 Connected가 뜬다면 끝이다. 

3. 주요기능
- 실시간
Firebase 실시간 데이터베이스는 일반적인 HTTP 요청이 아닌 동기화를 사용하므로 데이터가 변경될 때마다 연결된 모든 기기가 수 밀리초 내에 업데이트를 수신한다.
따라서 네트워크 코드를 작성할 필요 없이 몰입 가능한 협업 환경을 제공할 수 있습니다.
- 오프라인
Firebase 실시간 데이터베이스 SDK는 데이터를 디스크에 유지하므로 Firebase 앱은 오프라인일 때도 원활하게 작동한다.
네트워크에 다시 연결되면 클라이언트 기기가 놓쳤던 변경이 모두 수신되어 현재 서버 상태와 동기화된다.
-클라이언트 기기에서 액세스 가능
Firebase 실시간 데이터베이스를 휴대기기 또는 웹브라우저에서 직접 액세스할 수 있으므로 애플리케이션 서버가 필요없다. 
데이터를 읽거나 쓸 때 실행되는 표현식 기반 규칙인 Firebase 실시간 데이터베이스 보안 규칙을 통해 보안 및 데이터 검증을 제공한다.
-여러 데이터베이스에서 규모 조정
Firebase 실시간 데이터베이스에 Blaze 요금제를 적용하면 한 Firebase 프로젝트에서 여러 데이터베이스 인스턴스로 데이터를 분할하여 규모에 따라 유연하게 앱의 데이터 수요를 감당할 수 있다.
프로젝트에서 Firebase 인증하면 인증 작업을 간소화할 수 있다. 
각 데이터베이스 인스턴스에 대한 맞춤 Firebase 실시간 데이터베이스 규칙을 제공하여 각 데이터베이스의 데이터 액세스를 제어한다.

4. 장점
앱의 개발 기간을 단축시키고 ,앱 개발 난이도를 낮춰준다.
앱에서 많이 사용하는 기능 (인증, 클라우드 파이어스토어, 저장소, 호스팅 ,클라우드 메시징, 원격구성) 등을 API형태로 제공한다.

5. 단점
앱의 규모가 커지고 사용자가 급격히 증가하는 경우 비용적으로 부담이 될 수 있으며 서버를 직접 구축하는것이 아니기 때문에 백엔드 로직에 대한 수정 등에 있어 제한적인 부분이 있다.

***   

>유료 서비스를 사용하기에 부담스러운 면이 있어서 학과 지원비가 나온다면 AWS를 사용하고 아니라면 Firebase를 사용하겠습니다.   
