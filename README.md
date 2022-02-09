# 인수테스트 TODO
##  1단계 - 노선 관리 기능 구현 
- [X] 인수테스트 작성
- [X] 기능구현
    - [X] 지하철 노선 목록 조회
    - [X] 지하철 노선 조회
    - [X] 지하철 노선 수정
    - [X] 지하철 노선 삭제

## 2단계 - 인수 테스트 리팩터링
- [X] 지하철 역 이름 중복 금지 기능 
  - [X] 인수 테스트 
  - [X] 기능 구현 
- [X] 노선 이름 중복 금지 기능
  - [X] 인수 테스트
  - [X] 기능 구현 
- [X] 인수 테스트 리팩터링
  - [X] 노선 인수 테스트 
  - [X] 지하철역 인수 테스트 
  
## 3단계 - 지하철 구간 관리
- [X] README에 인수 조건 정의 
- [ ] 지하철 구간 정의
- [ ] 지하철 노선
  - [X] 등록시 상행종점/하행종점/distance 함꼐 등록
    - [ ] 존재하지 않는 station이면 예외처리
    - [ ] 상행 종점의 id >= 하행 종점 id이면 예외처리
    - [ ] distance 0 이하면 예외
  - [ ] 구간 등록
    - [x] 등록
    - [ ] 존재하지 않는 역 exception
    - [ ] 존재하지 않는 노선 exception
  - [ ] 구간제거
  - [ ] 조회시 역목록 함께 응답
  
### Feature: 지하철 구간 관리 기능
- Scenario : 지하철 구간 등록 (done)
  - Given: 지하철 노선 생성을 요청하고
  - When: 지하철 구간 생성을 요청하면
  - Then: 지하철 구간 생성이 성공한다.

- Scenario: 지하철 구간 등록 실패 (done)
  - Given: 지하철 노선 생성을 요청하고
  - When: 노선의 역 중, 하행 종점역 외의 역을 새 구간의 상행역으로 지정하고
  - When: 구간 생성요청시 
  - Then: 구간 생성이 실패한다.
  
- Scenario: 지하철 구간 등록 실패
  - Given: 지하철 노선 생성을 요청하고
  - When: 노선에 이미 등록된 역을 새 구간의 하행역으로 지정하고
  - When: 구간 생성요청시
  - Then: 구간 생성이 실패한다.
  

- Scenario : 지하철 구간 제거
  - Given: 지하철 노선 생성을 요청하고
  - Given: 지하철 구간을 생성을 요청하고
  - When: 지하철 구간 삭제 요청시
  - Then: 구간 삭제 성공한다. 
  

- Scenario: 지하철 구간 제거 실패
  - Given: 지하철 노선 생성을 요청하고
  - Given: 지하철 구간 생성을 요청하고
  - Given: 새로운 지하철 구간 생성을 요청하고
  - When: 마지막 구간 이외의 구간을 제거 요청하면
  - Then: 구간 삭제 실패한다.


- Scenario: 지하철 구간 제거 실패
  - Given: 지하철 노선 생성을 요청하고
  - Given: 지하철 구간 생성을 요청하고
  - When: 구간을 제거 요청하면
  - Then: 구간 삭제 실패한다.


- Scenario : 지하철 역 목록 조회
  - Given: 지하철 노선 생성을 요청하고
  - Given: 지하철 구간 생성을 요청하고
  - When: 지하철 노선을 조회하면
  - Then: 지하철 역이 구간 순서대로 조회된다.
