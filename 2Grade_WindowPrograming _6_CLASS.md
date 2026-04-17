# C# 프로그래밍 - 7주차 정리

## 📚 학습 내용
- 클래스 개요
- 클래스 사용
- 클래스 생성
- 클래스의 변수
- 추상화

### 클래스 개요
- 클래스
  - 객체 지향 언어, 원하는 새로운 자료형 정의
```
(예시) 주차관리시스템

- 필요한 변수
int carNumber; // 차량 번호
int inTime; // 입차 시간
int outTime; // 출차 시간

- 3대를 관리해야 한다면?
int carNumberA;
int inTimeA;
int outTimeA;
int carNumberB;
int inTimeB;
int outTimeB;
int carNumberC;
int inTimeC;
int outTimeC;

- 관리 차량이 여러 대라면?
int[] CarNumbers = new int[10];
int[] inTimes = new int[10];
int[] outTimes = new int[10];
```
