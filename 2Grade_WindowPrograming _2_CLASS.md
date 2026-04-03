# C# 프로그래밍 - 3주차 정리

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
-
| 키워드 | 키워드 | 키워드 | 키워드 |
|-----------|------------|----------|----------|
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

  - 컨텍스트(문맥) 키워드 -> 특정 위치에서만 키워드로 작동
#### (컨텍스트 키워드)
- 

| 키워드 | 키워드 | 키워드 | 키워드 | 키워드 |
|-----------|------------|------------|-----------|----------|
| add       | and        | alias      | ascending | args     |
| async     | await      | by         | descending| dynamic  |
| equals    | file       | from       | get       | global   |
| group     | init       | into       | join      | let      |
| managed   | nameof     | nint       | not       | notnull  |
| nuint     | on         | or         | orderby   | partial  |
| record    | remove     | required   | scoped    | select   |
| set       | unmanaged  | value      | var       | when     |
| where     | with       | yield      |           |          |


- 식별자
  - 이름을 붙일 때 사용하는 단어
  - C#에서의 변수와 메서드 이름 식별자 규칙
    - 키워드 X
    - 특수 문자는 _만 O
    - 숫자로 시작 X
    - 공백은 입력 X
#### (식별자 규칙)
- 
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


- 식별자 구분
  - 괄호가 있는 식별자는 메서드 : Console.WriteLine("Hello C# Programing"); -> WriteLine(메서드)
  - 이외의 것은 변수 : Math.PI; -> PI(변수)
  - 메서드 괄호 안에 매개변수(Parameter) : Math.Floor(10, 1); -> (10, 1)(파라미터)

- 주석
  - 한 줄 주석 : //
  - 여러 줄 주석 : /**/
 
### 출력
- 방법1 : Console 클래스의 WriteLine() 메서드 사용
```
Console.WriteLine(출력하고_싶은_대상);
```
- 방법2 : Write() 메서드 사용

- 기본
```
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace week5wp
{
    internal class Program
    {
        static void Main(string[] args)
        {

        }
    }
}
```
```
예제 2-1 : C# 기본 출력 익히기
static void Main(string[] args)
{
   Console.WriteLine("Hello C# Programing .. !");
}

- 결과
Hello C# Programing .. !
```

### 기본 자료형
#### 정수
  - 정수는 가장 기본적인 자료형
  - 273, 52, -103, 0처럼 하나하나 셀 수 있는 숫자
  - 소수점이 없는 숫자
```
예제 2-2 : 정수 생성
static void Main(string[] args)
{
   Console.WriteLine(52);
}

- 결과
52
```
- 기본적인 사칙 연산자
- 
| 연산자 | 설명 |
|-------|-------|
| + | 덧셈 |
| - | 뺄셈 |
| * | 곱셈 |
| / | 나눗셈 몫 |
| % | 나눗셈 나머지 |
```
예제 2-3 : 정수 덧셈 연산자
static void Main(string[] args)
{
   Console.WriteLine(52 + 273);
}

- 결과
325
```
```
예제 2-4 : 연산자 우선순위
static void Main(string[] args)
{
   Console.WriteLine(5 + 2 * 3);
}

- 결과
11
```
```
예제 2-5 : 나머지 연산자
static void Main(string[] args)
{
   Console.WriteLine(10 % 5);
   Console.WriteLine(7 % 3);
}

- 결과
0
1
```
- 정수 연산 시 주의 사항
  - 정수 연산 결과는 정수
  - 예시) 10/4는 2.5가 아니라 2
```
정수 + 정수 = 정수
정수 - 정수 = 정수
정수 * 정수 = 정수
정수 / 정수 = 정수
정수 % 정수 = 정수
```
```
예제 2-6 : 정수와 연산자
static void Main(string[] args)
{
   Console.WriteLine(1 + 2);
   Console.WriteLine(1 - 2);
   Console.WriteLine(1 * 2);
   Console.WriteLine(1 / 2); // 결과는 정수
   Console.WriteLine(1 % 2);
}

- 결과
3
-1
2
0
1
```
- 나머지 연산자의 부호는 왼쪽 피연산자와 부호를 따름
```
예제 2-7 : 음수와 나머지 연산자
static void Main(string[] args)
{
   Console.WriteLine(4 % 3);
   Console.WriteLine(-4 % 3);
   Console.WriteLine(4 % -3);
   Console.WriteLine(-4 % -3);
}

- 결과
1
-1
1
-1
```
#### 실수
- 소수점(.) 사용
- 연산자(+, -, *, /)로 사칙연산 가능
  - 나머지 연산자(%)도 사용은 가능하나 결과 예측이 어려워 비추천
```
예제 2-8 : 실수
static void Main(string[] args)
{
   Console.WriteLine(52.273);
}

- 결과
52.273
```
```
예제 2-9 : 정수와 실수
static void Main(string[] args)
{
   Console.WriteLine(0); // 정수
   Console.WriteLine(0.0); // 실수
}
```
```
예제 2-10 : 실수와 사칙 연산자
static void Main(string[] args)
{
   Console.WriteLine(1.0 + 2.0);
   Console.WriteLine(1.0 -2.0);
   Console.WriteLine(1.0 * 2.0);
   Console.WriteLine(1.0 / 2.0); // 결과는 실수로 출력
}

- 결과
3
-1
2
0.5
```
#### 문자
- 문자(Character)란, 글자 하나를 나타내는 자료형
  - 작은 따음표('')로 글자를 감싸서 만듦 // 예시) 'a'
  - C#은 알파벳 뿐만 아니라 모든 나라의 문자 표현 가능
```
예제 2-12 : 문자
static void Main(string[] args)
{
   Console.WriteLine('A');
   Console.WriteLine('가');
   Console.WriteLine('나');
}

- 결과
A
가
나
```
#### 문자열
- 문자열 : 문자의 집합
  - 큰 따음표("")를 사용해 문자열을 생성
  - 예) "abcdefg", "Hello World", "안녕하세요"
```
예제 2-13 : 문자열
static void Main(string[] args)
{
   Console.WriteLine("안녕하세요");
}

- 결과
안녕하세요
```
- 이스케이프 문자
  - 특수 기능을 수행
  - 문자열 내에서 (문자의 하나로) 큰따음표를 사용하고 싶을 때 문자열 내부에 "\"를 사용
- 자주 사용되는 이스케이프 문자
- 
| 이스케이프 문자 | 설명 | 이스케이프 문자 | 설명 |
|---------------|------|----------------|--------|
| \t | 수평 탭 | \\ | 역 슬래시 |
| \n | 행 바꿈 | \* | 큰따음표 |
```
예제 2-14 : 이스케이프 문자
static void Main(string[] args)
{
   Console.WriteLine("한빛\t아카데미");
   Console.WriteLine("한빛\n아카데미");
   Console.WriteLine("\"\"\"");
}

- 결과
한빛    아카데미
한빛
아카데미
"""
```
- 문자열 연결 연산자
- 
| 연산자 | 설명 |
|-------|-------|
| + | 문자열 연결 연산자 |
```
예제 2-15 : 문자열 연결 연산자
static void Main(string[] args)
{
   Console.WriteLine("가나다" + "라마" + "바사아" + "자차카타" + "파하");
}

- 결과
가나다라마바사아자차카타파하
```
- 문자열 선택 괄호
- 
| 연산자 | 설명 |
|-------|-------|
| 문자열[숫자] | 문자 선택 괄호 |
```
예제 2-16 : 문자 선택
static void Main(string[] args)
{
   Console.WriteLine("안녕하세요[0]");
   Console.WriteLine("안녕하세요[1]");
   Console.WriteLine("안녕하세요[3]");
}

- 결과
안
녕
세
```
- 문자열은 + 연산자 가능, 문자는 불가능
```
예제 2-18 : 문자 덧셈
static void Main(string[] args)
{
   Console.WriteLine('가' + '힣'); // 문자도 내부적으로 숫자 코드값을 갖고 있음 (아스키코드 값)
}

- 결과
99235
```
#### 불
- 불(bool)은 참과 거짓을 표현할 때 사용
  - true, false 두 가지 값만 존재
```
예제 2-19 : 불
static void Main(string[] args)
{
   Console.WriteLine(true);
   Console.WriteLine(false);
}
```
- 비교 연산자
  - 크기를 비교하는 연산자로 그 결과를 참과 거짓으로 표현
  - 왼쪽과 오른쪽 중 어떤 쪽이 더 큰지에 따라 참과 거짓을 쉽게 구별할 수 있음
- 
| 연산자 | 설명 |
|-------|------|
| == | 같다 |
| != | 다르다 |
| > | 왼쪽 피연산자가 크다 |
| < | 오른쪽 피연산자가 크다 |
| >= | 왼쪽 피연산자가 크거나 같다 |
| <= | 오른쪽 피연산자가 크거나 같다 |
```
예제 2-20 : 불과 비교 연산자
static void Main(string[] args)
{
   Console.WriteLine(52 < 273);
   Console.WriteLine(52 > 273);
}

- 결과
True
False
```
- 논리 연산자
  - 불 끼리는 논리 연산자를 사용
- 
| 연산자 | 설명 |
|-------|------|
| ! | 논리 부정 연산자 NOT |
| || | 논리합 연산자 OR |
| && | 논리곱 연산자 AND |

- 논리 부정 연산 NOT
  - 숫자의 부호를 반대로 만드는 - 연산자와 같은 형태로 사용
```
예제 2-21 : 논리 부정 연산자
static void Main(string[] args)
{
   Console.WriteLine(!true);
   Console.WriteLine(!false);
   Console.WriteLine(!(52 < 273));
   Console.WriteLine(!(52 > 273));
}

- 결과
False
True
False
True
```
- 논리합 연산자 OR
  - 두 개의 피연산자 중에 하나만 true이면 전체가 true가 됨
- 
| 왼쪽 피연산자 | 오른쪽 피연산자 | 결과 |
|--------------|---------------|--------|
| true | true | true |
| true | false | true |
| false | true | true |
| false | false | false |

- 논리곱 연산자 AND
  - 두 개의 피연산자 모두 true여야만 전체가 true가 됨
- 
| 왼쪽 피연산자 | 오른쪽 피연산자 | 결과 |
|--------------|---------------|--------|
| true | true | true |
| true | false | false |
| false | true | false |
| false | false | false |

- 불
  - 범위 판단과 관련된 부분에서 논리 연산자를 가장 많이 사용
```
3시와 8시 사이라는 조건 표현 시,
3 < 현재 시각 < 8 표현은 오류
```
```
int number = 10;
Console.WriteLine(3 < number < 8); // 오류
```
```
예제 2-22 : 불과 논리 연산자
static void Main(string[] args)
{
   // 현재 시간 오전 5시로 생각
   Console.WriteLine(DateTime.Now.Hour < 3 || 8 < DateTime.Now.Hour); // 현재 시간이 3시 이전 또는 8시 이후인지 조건 확인
   Console.WriteLine(3 < DateTime.Now.Hour && DateTime.Now.Hour < 8); // 현재 시간이 3시와 8시 사이인지 조건 확인
}

- 결과
False
True
```

### 변수
- 변수는 값을 저장할 때 사용하는 식별자
  - 숫자 뿐만 아니라 모든 자료형 저장
- 변수 사용 단계
  - 1. 변수 선언 : 변수를 만듦
  - 2. 변수에 값 할당 : 변수에 값을 넣음
```
double pi = 3.141592
자료형 이름     값
```
#### 정수 자료형
- 가장 많이 사용하는 정수 자료형
- 
| 키워드 | 설명 |
|-------|------|
| int | 4바이트의 정수 |
| long | 8바이트의 정수 |
```
int a = 10
long b = 20
```
```
예제 2-23 : 정수 변수 생성
static void Main(string[] args)
{
   int a = 273;
   int b = 52;
   Console.WriteLine(a + b); 
   Console.WriteLine(a - b);
   Console.WriteLine(a * b); 
   Console.WriteLine(a / b); // 몫
   Console.WriteLine(a % b); // 나머지
}

- 결과
325
221
14196
5
13
```
- int 자료형
  - 정수를 만들 때 사용
  - 크기 : 4Byte(8Bit)
  - 범위 : 2³²개의 숫자(-2,147,483,648 ~ 2,147,483,647)
- 오버플로우 : int 자료형의 범위를 넘어 현상
```
예제 2-24 : 오버플로우
 static void Main(string[] args)
{
   int a = 2147483640;
   int b = 52273;
   Console.WriteLine(a + b); // 결과값이 표현 가능한 범위를 초과
}

- 결과
-2147431383
```
```
예제 2-25 : 오버플로우
 static void Main(string[] args)
{
   int a = 2000000000;
   int b = 1000000000;
   Console.WriteLine(a + b); // 결과값이 표현 가능한 범위를 초과
}

- 결과
-1293967296
```
```
예제 2-26 : 자료형 변환을 사용한 해결 방법
 static void Main(string[] args)
{
   uint unsignedA = 2000000000;
   uint unsignedB = 1000000000;
   Console.WriteLine(unsignedA + unsignedB);
}

- 결과
3000000000
```
- unsigned 자료형
  - 음수 사용을 위한 자료형
  - unit, ulong 키워드 사용
```
예제 2-27 : unit, ulong 자료형
 static void Main(string[] args)
{
   uint unsignedInt = 4147483647;
   ulong unsignedLong = 11223372036854775808;
   Console.WriteLine(unsignedInt);
   Console.WriteLine(unsignedLong);
}

- 결과
4147483647
11223372036854775808
```
- MaxValue, MinValue
```
예제 2-28 : int 자료형의 최댓값과 최솟값
 static void Main(string[] args)
{
   Console.WriteLine(int.MaxValue);
   Console.WriteLine(int.MinValue);
}

- 결과
2147483647
-2147483648
```
```
예제 2-29 : long 자료형의 최댓값과 최솟값
 static void Main(string[] args)
{
   Console.WriteLine(long.MaxValue);
   Console.WriteLine(long.MinValue);
}

- 결과
9223372036854775807
-9223372036854775808
```
#### 실수 자료형
- 실수 자료형은 실수 변수를 만들 때 사용
- 
| 키워드 | 설명 |
|-------|-------|
| float | 4바이트의 실수 |
| double | 8바이트의 실수 |
```
예제 2-30 : 실수 변수 생성
 static void Main(string[] args)
{
   double a = 52.273;
   double b = 103.32;

   Console.WriteLine(a + b);
   Console.WriteLine(a - b);
   Console.WriteLine(a * b);
   Console.WriteLine(a / b);
}

- 결과
155.593
-51.047
5400.84636
0.50593302361595
```
#### 문자 자료형
- 문자 변수를 만들 때 사용하는 자료형
- 
| 키워드 | 설명 |
|-------|-------|
| char | 문자 |
```
예제 2-31 : 문자 변수 생성
 static void Main(string[] args)
{
   char a = 'a';
   Console.WriteLine(a);
}

- 결과
a
```
- sizeof 연산자와 char 자료형의 크기
  - sizeof(자료형)
```
예제 2-32 : sizeof 연산자
 static void Main(string[] args)
{
   Console.WriteLine("int: ", + sizeof(int));
   Console.WriteLine("long: ", + sizeof(long));
   Console.WriteLine("float: ", + sizeof(float));
   Console.WriteLine("double: ", + sizeof(double);
   Console.WriteLine("char: ", + sizeof(char));
}

- 결과
int: 4
long: 8
float: 4
double: 8
char: 2
```
- 문자 자료형과 연산자
  - 문자 자료형은 문자열 자료형보다 정수에 가까움(연산가능)
```
예제 2-33 : 문자 자료형과 연산자
 static void Main(string[] args)
{
   char a = 'a';
   char b = 'b';

   Console.WriteLine(a + b);
   Console.WriteLine(a - b);
   Console.WriteLine(a * b);
   Console.WriteLine(a / b);
   Console.WriteLine(a % b);
}

- 결과
195
-1
9506
0
97
```
#### 문자열 자료형
- 문자열 변수를 선언할 때 사용하는 자료형
- 
| 키워드 | 설명 |
|-------|------|
| string | 문자열 자료형 |
```
예제 2-34 : 문자열 변수 생성
 static void Main(string[] args)
{
   string message = "안녕하세요";

   Console.WriteLine(message + "!");
   Console.WriteLine(message[0]);
   Console.WriteLine(message[1]);
   Console.WriteLine(message[2]);
}

- 결과
안녕하세요!
안
녕
하
```
- sizeof 연산자와 string 자료형
  - string 자료형은 sizeof 연산자로 자료형의 크기를 구할 수 없음
```
예제 2-35 : sizeof 연산자와 string 자료형
 static void Main(string[] args)
{
   Console.WriteLine("string: " + sizeof(string)); // 오류
}
```
- 
| 기본 자료형 | 원형 | 기본 자료형 | 원형 |
|------------|------|------------|-------|
| int | struct System.Int32 | float | struct System.Single |
| long | struct System.Int64 | double | struct System.Double |
| char | struct System.Char | bool | struct System.Boolean |
| string | class System.String |  |  |
- string만 struct로 시작하지 않고 class로 시작

#### 불 자료형
- 불 변수를 선언할 때 사용하는 자료형
- 
| 키워드 | 설명 |
|-------|-------|
| bool | 불 자료형 |
```
예제 2-36 : 불 변수 생성
 static void Main(string[] args)
{
   bool one = 10 < 0;
   bool other = 20 > 100;

   Console.WriteLine(one);
   Console.WriteLine(other);
}

- 결과
False
False
```

### ✍️작성자: 박지안
### 🐧실습 환경: Visual Studio 2022
### 🗓️ 작업일: 2026-04-03
