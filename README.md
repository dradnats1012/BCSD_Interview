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

![image](https://github.com/dradnats1012/BCSD_Interview/assets/112807640/b8be80cd-38af-44c0-a092-a65cdfdda1c4)

## 동작 

### 열람실 선택 
  - [ ] 선택된 __열람실 번호__ 저장
  - [ ] 해당 열람실 화면으로 전환

### 좌석 선택(3시간)
  - [x] 선행 조건
    - [x] seats 테이블에서 User의 school_id를 검색했을 때 없음
    - [x] 선택하려는 좌석의 is_used 가 false

  - [x] 결과
    - [x] 선택한 좌석 번호 __seat_id__ 추가
    - [x] __room_Id__ 에 열람실 선택에서 저장한 번호 추가
    - [x] __school_id__ 추가
    - [x] __start_time__ 에 현재 시간 추가
    - [x] __end_time__ 에  (현재 시간 + 3시간) 추가
    - [x] __is_used__ 를 true로 변경
    - [ ] 해당 room의 usedSeats와 remainSeats update
    
### 좌석 변경 
  - [x] 선행 조건
    - [x] seats 테이블에서 User의 school_id를 검색했을 때 없음
    - [x] 변경하려는 좌석의 __is_used__ 가 false
        
  - [x] 결과
    - [x] 기존 좌석 __사용 종료__
    - [x] 변경하려는 좌석의 __school_id__를 User의 __school_id__로 변경
    - [x] __start_time__ 에 현재 시간 추가
    - [x] __end_time__ 에  (현재 시간 + 3시간) 추가
    - [x] __is_used__ 를 true로 변경
    - [x] 기존 좌석의 __is_used__ false로 변경
    
### 좌석 취소
  - [ ] 선행 조건
    - [ ] seats 테이블에서 User의 __school_id__ 를 검색했을 때 있음
  - [x] 결과 
    - [x] 해당 좌석 __사용 종료__
    - [ ] 해당 room의 usedSeats와 remainSeats update
    
### 좌석 연장
  - [ ] 선행 조건
    - [ ] seats 테이블에서 User의 __school_id__ 를 검색했을 때 있음
  - [ ] 결과
    - [ ] 해당 좌석의 __end_time__ +3시간

### 좌석 사용 종료
  - Case
    - [ ] __remain_time__ 이 0이 될 경우
    - [x] __좌석 취소__ 할 경우
    - [x] __좌석 변경__ 할 경우 기존 좌석 사용 종료
  - [x] 선행 조건
    - [x] 취소하려는 좌석의 __is_used__가 true
    - [x] User의 __school_id__ 와 좌석의 __school_id__ 가 같아야 함
  - [x] 결과
    - [x] 좌석의 __school_id__ 비우기
    - [x] __start_time__, __end_time__, __remain_time__ 비우기
    - [x] __is_used__ false로 변경
    - [x] __room_id__ 비우기


## 일정
- 1/15 ~ 1/21
  - 테이블 생성, MVC 패턴 구조 설계, 열람실 선택, 좌석 선택 구현
- 1/22 ~ 1/28
  - 좌석 사용 종료, 좌석 취소, 좌석 변경, 좌석 연장 구현 
- 1/29 ~ 2/04
  - 로그인, 회원가입, 화면 구현
