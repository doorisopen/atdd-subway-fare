# 지하철 노선도 미션
[ATDD 강의](https://edu.nextstep.camp/c/R89PYi5H) 실습을 위한 지하철 노선도 애플리케이션

## 기능 구현 목록
* 노선에 추가 요금 정보를 추가한다.
* 경로 탐색 시, 추가 요금 노선을 이용하는 경우 운임 요금에 합산한다.
  * 단, 추가 요금이 존재하는 노선 중 가장 높은 금액의 추가 요금만 적용한다.
* 로그인한 사용자의 경우 연령별로 요금을 할인한다.
  * 청소년(13세 이상 ~ 19세 미만): 운임에서 350원을 공제한 금액의 20%할인
  * 어린이(6세 이상 ~ 13세 미만): 운임에서 350원을 공제한 금액의 50%할인

## 도전 미션 요구사항  
* 특정 시간 기준으로 가장 빨리 도착할 수 있는 경로를 조회하는 기능
* 경로가 여러 경로일 경우, 모든 경로의 도착시간을 구한 뒤 가장 빠른 경로를 응답
* 정차 시간은 무시
* 경로 조회 시 막차 시간을 넘기면 다음날 첫차 시간을 찾는다.
* 그 외 구현에 필요한 모든 제약 조건을 추가한다.

### 시나리오
1. 환승 미고려 

배경
- 2호선
  - 첫차시간: 05:00
  - 막차시간: 23:00
  - 간격: 10분
  - 역: 서초역---(3분)---강남역---(4분)---역삼역---(3분)---선릉역

요청
- 출발역 -> 도착역: 강남역 -> 선릉역
- 기준시간: 10:00


2. 환승 고려

배경
- 신분당선 추가
  - 첫차시간: 05:00
  - 막차시간: 23:00
  - 간격: 20분
  - 역: 강남역---(4분)---양재역
  
요청
- 출발역 -> 도착역: 서초역 -> 양재역
- 기준시간: 10:00


- 서초역은 종점
- 서초역---(3분)---강남역

## TODO
* [x] 요금(Fare) 객체 분리
* [x] 특정 시간 기준 최소 경로 탐색 객체 생성
  * 특정 시간 기준 가장 빠른 열차 시간 조회(노선(Line)이 해당 책임을 가진다.)
  * 배차 시간표 생성(Map<Integer, boolean[60]) 
* [x] 노선 정보("첫차시간", "막차시간", "간격") 추가
