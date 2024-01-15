# BCSD_Interview
BCSD비기너 코스 회고 깃 저장소
각자 본인의 브랜치를 만든뒤, 포크를 따서 pr을 날린다. (main으로 pr x, 본인의 레포로 pr날리기)
# BCSD_Interview
BCSD비기너 코스 회고 깃 저장소
각자 본인의 브랜치를 만든뒤, 포크를 따서 pr을 날린다. (main으로 pr x, 본인의 레포로 pr날리기)

# 열람실 예약 프로그램

## 기능

- 로그인
- 회원가입
- 열람실 선택
  - 좌석 선택 &rarr; 3시간
    - 사용 
    - 변경
    - 취소
    - 연장

## 화면

- [ ] 로그인
- [ ] 회원가입
- [ ] 메인 화면(사용자, 사용 현황, 좌석 선택, 사용 종료)
  - [ ] 열람실 선택
    - [ ] 1열람실
    - [ ] 2열람실
    - [ ] 3열람실
    
![image](https://github.com/dradnats1012/BCSD_Interview/assets/112807640/75241149-5100-4286-802a-834bc32e8625)


## 테이블

![image](https://github.com/dradnats1012/BCSD_Interview/assets/112807640/84530d7f-f47e-49ba-8438-b13aee3a7e3f)


## 동작 

### 열람실 선택 
  - [ ] 선택된 __열람실 번호__ 저장
  - [ ] 해당 열람실 화면으로 전환

### 좌석 선택(3시간)
  - [ ] 선행 조건
    - [ ] seats 테이블에서 User의 school_id를 검색했을 때 없음
  - [ ] 결과
    - [ ] 선택한 좌석 번호 __seat_id__ 추가
    - [ ] __room_Id__ 에 열람실 선택에서 저장한 번호 추가
    - [ ] __school_id__ 추가
    - [ ] __start_time__ 에 현재 시간 추가
    - [ ] __end_time__ 에  (현재 시간 + 3시간) 추가
    - [ ] __is_used__ 를 true로 변경
    
### 좌석 변경 
  - [ ] 선행 조건
    - [ ] 해당 __seat_id__ 의 __is_used__ 가 false
    - [ ] 변경하려는 __seat_id__ 의 __is_used__ 가 false
  - [ ] 결과
    - [ ] 기존 좌석 __사용 종료__
    - [ ] 변경하려는 좌석의 __school_id__를 User의 __school_id__로 변경
    - [ ] __start_time__ 에 현재 시간 추가
    - [ ] __end_time__ 에  (현재 시간 + 3시간) 추가
    - [ ] __is_used__ 를 true로 변경
    - [ ] 기존 좌석의 __is_used__ false로 변경
    
### 좌석 취소
  - [ ] 선행 조건
    - [ ] seats 테이블에서 User의 __school_id__ 를 검색했을 때 있음
  - [ ] 결과 
    - [ ] 해당 좌석 __사용 종료__
    
### 좌석 연장
  - [ ] 선행 조건
    - [ ] seats 테이블에서 User의 __school_id__ 를 검색했을 때 있음
  - [ ] 결과
    - [ ] 해당 좌석의 __end_time__ +3시간

### 좌석 사용 종료
  - Case
    - [ ] __remain_time__ 이 0이 될 경우
    - [ ] __좌석 취소__ 할 경우
    - [ ] __좌석 변경__ 할 경우 기존 좌석 사용 종료
  - [ ] 선행 조건
    - [ ] 취소하려는 좌석의 __is_used__가 true
    - [ ] User의 __school_id__ 와 좌석의 __school_id__ 가 같아야 함
  - [ ] 결과
    - [ ] 좌석의 __school_id__ 비우기
    - [ ] __start_time__, __end_time__, __remain_time__ 비우기
    - [ ] __is_used__ false로 변경
    - [ ] __room_id__ 비우기


## 일정
- 1/15 ~ 1/21
  - 열람실 선택, 좌석 선택 구현
- 1/22 ~ 1/28
  - 좌석 사용 종료, 좌석 취소, 좌석 변경, 좌석 연장 구현 
- 1/29 ~ 2/04
  - 로그인, 회원가입, 화면 구현
