# C# 프로그래밍 첫걸음 - 2주차 정리

## 📚 학습 내용
- 기본 용어
- 출력
- 기본 자료형
- 변수
- 실습

### 기본 용어
- 표현식
  - 값을 만들어 내는 간단한 코드
#### (예시)
```
273
10 + 20 + 30 * 2
"C# Programming"
```

- 문장(statement)
  - 표현식의 모임, 마지막 세미콜론(;) 추가
#### (예시)
```
273;
10 + 20 + 30 * 2;
var name = "박" + "지" + "안";
Console.Write("Hello C# Programming");
```

- 키워드(예약어)
  - 일반 키워드
#### (일반 키워드)
```
| new       | null       | object   | operator |
| out       | override   | params   | private  |
| protected | public     | readonly | ref      |
| return    | sbyte      | sealed   | short    |
| sizeof    | stackalloc | static   | string   |
| struct    | switch     | this     | throw    |
| TRUE      | try        | typeof   | unit     |
| ulong     | unchecked  | unsafe   | ushort   |    
| using     | virtual    | void     | volatile | 
| while     |            |          |          |
```
  - 컨텍스트(문맥) 키워드 -> 특정 위치에서만 키워드로 작동
#### (컨텍스트 키워드)
```
| add       | and        | alias      | ascending | args     |
| async     | await      | by         | descending| dynamic  |
| equals    | file       | from       | get       | global   |
| group     | init       | into       | join      | let      |
| managed   | nameof     | nint       | not       | notnull  |
| nuint     | on         | or         | orderby   | partial  |
| record    | remove     | required   | scoped    | select   |
| set       | unmanaged  | value      | var       | when     |
| where     | with       | yield      |           |          |
```

- 식별자
  - 이름을 붙일 때 사용하는 단어
  - C#에서의 변수와 메서드 이름 식별자 규칙
    - 키워드 X
    - 특수 문자는 _만 O
    - 숫자로 시작 X
    - 공백은 입력 X
#### (식별자 규칙)
```
| 구분 | 예시 | 설명 |
|------|------|------|
| ✅ 바른 예 | `int age = 20;` | 일반적인 변수 이름 (문제 없음) |
| ✅ 바른 예 | `int studentAge = 20;` | 여러 단어 → camelCase 사용 |
| ✅ 바른 예 | `int _count = 10;` | `_` 사용 가능 |
| ✅ 바른 예 | `void printResult()` | 메소드 이름 (소문자로 시작) |
| ✅ 바른 예 | `int number1 = 5;` | 숫자 포함 가능 (앞 제외) |

| ❌ 바르지 않은 예 | `int 1age = 20;` | 숫자로 시작 ❌ |
| ❌ 바르지 않은 예 | `int student age = 20;` | 공백 포함 ❌ |
| ❌ 바르지 않은 예 | `int int = 10;` | 키워드 사용 ❌ |
| ❌ 바르지 않은 예 | `int student-age = 20;` | 특수문자 사용 ❌ (`_`만 가능) |
| ❌ 바르지 않은 예 | `void Print Result()` | 공백 포함 ❌ |
```

- 식별자 구분
  - 괄호가 있는 식별자는 메서드 : Console.WriteLine("Hello C# Programing"); -> WriteLine(메서드)
  - 이외의 것은 변수 : Math.PI; -> PI(변수)
  - 메서드 괄호 안에 매개변수(Parameter) : Math.Floor(10, 1); -> (10, 1)(파라미터)

- 주석
  - 한 줄 주석 : //
  - 여러 줄 주석 : /**/
 
// 기본 용어 까지 끝 <- 지우기
