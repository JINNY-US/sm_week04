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

## 스마트 모바일 프로그래밍 설계 주제 

### 4. 어디 가게

커플 혹은 친구들끼리 놀러갈 때나 여행할 때 주변에 놀만한 곳, 맛있는 음식이 있는 곳을 찾기 힘들 때를 대비하여 정해진 예산과 지역, 목적을 입력하여 주변에서 가장 가까운 곳, 혹은 목적과 가장 유사한 곳을 추천해주는 앱입니다.   

### (1) 기능과 특징 

1. 지역과 목적(ex. 홍대 or 영화, 음식점)을 입력하면 사용자의 주변에 목적과 유사한 가게들을 추천합니다.
2. 사람들이 많이 사용한다고 생각하는 음식점, 카페, 옷가게, 영화관으로 설정했으며 이후에 더 추가될수도 있습니다.
3. 사용 가능한 예산과 인원, 시간대, 해시태그 기능을 사용하여 사용자의 목적과 유사한 추천목록을 제공합니다. 또한, 가능하다면 예약하기 기능도 넣어서 대기시간 없이 즐길 수 있도록 할 예정입니다.
4. 각 분야에 따라 게시판을 생성하여 유저들 간의 소통이 활발하게 이루어지도록 만들 예정입니다. (ex. 맛집 추천, 영화 리뷰, 같이 밥 먹을 사람 구하기 등)
5. 추천탭 상단에 가게의 광고를 추가하여 홍보할 수 있는 수단을 만들 예정입니다. 
6. 리뷰 기능을 넣어 가게의 상태와 서비스 등을 평가할 수 있습니다.
7. GPS를 사용하여 거리를 측정하고 가는 길을 표시합니다.

### (2) 앱 로고 및 배경   

![어플 2차 최종(확정)](https://user-images.githubusercontent.com/57963888/111958828-0e081080-8b31-11eb-92ba-2386b7edae8f.png)
![배경 최종(확정)](https://user-images.githubusercontent.com/57963888/111959121-63dcb880-8b31-11eb-85d9-a2c3607e9139.png)   

### (3) 대략적인 데이터 테이블

1. 회원 테이블   
- 이름 char (10)   
- 닉네임 char (15)
- 아이디 char (20)   
- 비밀번호 char (20) : textPassword   
- 이메일1 char (10)   
- 이메일2 char (20) : comboBox(선택가능)   
- 이메일 char (25) : 이메일1@이메일2 ex) 201921036@smu.ac.kr   
- 업주여부 bool : radioButton   
- 나이 int : 주점, 술집 필터링 용도   

2. 가게 테이블   
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

3. 게시판 테이블   
- 작성자 이름 : 회원 테이블의 닉네임
- 작성자 ID : 회원 테이블의 아이디
- 제목 


4. 후기 테이블   



