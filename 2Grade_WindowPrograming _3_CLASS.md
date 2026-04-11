# C# 프로그래밍 - 4주차 정리

## 📚 학습 내용
- 복합 대입 연산자
- 증감 연산자
- 자료형 검사
- var 키워드
- 입력
- 자료형 변환

### 복합 대입 연산자
- 자료형에 적용하는 기본 연산자와 = 연산자를 함께 사용
  - a += 10은 a = a + 10을 뜻함
- 1. 숫자에 적용하는 복합 대입 연산자
- 
| 연산자 | 설명 |
|--------|------|
| += | 숫자 덧셈 후 대입 연산자 | 
| -= | 숫자 뺄셈 후 대입 연산자 |
| *= | 숫자 곱셈 후 대입 연산자 |
| /= | 숫자 나눗셈 후 대입 연산자 |
| %= | 숫자 나머지 연산 후 대입 연산자 |
- 2. 문자열에 적용하는 복합 대입 연산자
- 
| 연산자 | 설명 |
|--------|------|
| += | 문자열 연결 후 대입 연산자 |

#### 예제 2-37 : 숫자와 관련된 복합 대입 연산자
```
static void Main(string[] args)
{
   int output = 0;

   output += 52; // output = output + 52; 
   output += 273; // output = output + 273; 
   output += 103; // output = output + 103; 

   Console.WriteLine(output);
}

- 결과
428
```

#### 예제 2-39 : 문자와 관련된 복합 대입 연산자
```
static void Main(string[] args)
{
   string output = "hello";
   output += "world"; // output = output + "world";
   output += "!"; // output = output + "!";

   Console.WriteLine(output);
}

- 결과
hello world !
```

### 증감 연산자
- 단항 연산자로 변수 앞과 뒤에 ++기호와 --기호 붙여 만듦
- 
| 연산자 | 설명 |
|--------|------|
| [변수]++ | 기존 변수의 값에 1을 더합니다(후위) |
| ++[변수] | 기존 변수의 값에 1을 더합니다(전위) |
| [변수]-- | 기존 변수의 값에 1을 뺍니다(후위) |
| --[변수] | 기존 변수의 값에 1을 뺍니다(전위) |
- _전위_[변수]_후위_
- 전위(Prefix)
  - 해당 문자을 실행하기 전에 값을 변경
  - 예) Console.WriteLine(++number)
    - ==> 변수 number 1을 더한 후, Console.WriteLine(number);을 실행
    - ==> number += 1; Console.WriteLine(number);과 같음
- 후위(Postfix)
  - 문장을 실행한 이후에 값을 변경
  - 예) Console.WriteLine(number++)
    - ==> Console.WriteLine(number)를 실행한 우, 변수 number 1을 더함
    - ==> Console.WriteLine(number); number += 1;과 같음

#### 예제 2-41 : 증감 연산자
```
static void Main(string[] args)
{
   int number = 10;

   number++;
   Console.WriteLine(number);

   number--;
   Console.WriteLine(number);
}

- 결과
11
10
```

#### 예제 2-42 : 증감 연산자와 전위와 후위
```
static void Main(string[] args)
{
   int number = 10;

   Console.WriteLine(number);
   Console.WriteLine(number++);
   Console.WriteLine(number--);
   Console.WriteLine(number);
}

- 결과
10
10
11
10
```

#### 예제 2-43 : 증감 연산자의 전위와 후위
```
static void Main(string[] args)
{
   int number = 10;

   Console.WriteLine(number);
   Console.WriteLine(++number);
   Console.WriteLine(--number);
   Console.WriteLine(number);
}

- 결과
10
11
10
10
```

### 자료형 검사
- 자료형 검사 방법
  - 방법1 : 마우스를 사용한 자료형 확인(마우스 가져다 대기)
  - 방법2 : 프로그램 내부에서 자료형 출력(GetType() 메서드 사용)
-
| 메서드 | 설명 |
|--------|------|
| GetType() | 해당 변수의 자료형을 추출함 |

#### 예제 2-47 : GetType()메서드 활용
```
static void Main(string[] args)
{
   int _int = 273;
   long _long = 522531033265L;
   float _float = 52.273F;
   double _double = 52.273;
   char _char = '글';
   string _string = "문자열";

   Console.WriteLine(_int.GetType());
   Console.WriteLine(_long.GetType());
   Console.WriteLine(_float.GetType());
   Console.WriteLine(_double.GetType());
   Console.WriteLine(_char.GetType());
   Console.WriteLine(_string.GetType());
}

- 결과
System.Int32
System.Int64
System.Single
System.Double
System.Char
System.String
```

#### 에제 2-48 : 직접적인 GetType()메서드 활용
```
static void Main(string[] args)
{
    Console.WriteLine((273).GetType());
    Console.WriteLine((522531033265L).GetType());
    Console.WriteLine((52.273F).GetType());
    Console.WriteLine((52.273).GetType());
    Console.WriteLine(('자').GetType());
    Console.WriteLine(("문자열").GetType());
}

- 결과
System.Int32
System.Int64
System.Single
System.Double
System.Char
System.String
```

### var 키워드
- C#에서는 var키워드 변수의 자료형을 자동으로 지정할 수 있음
  - 변수 선언 시, 초기화할 때 자료형이 자동 지정
- 
| var 키워드 | 설명 |
|------------|------|
| var | 자료형을 자동으로 지정합니다 |
```
static void Main(string[] args)
{
   var number = 100;
```
- var키워드의 제약
  - 한 번 지정된 자료형은 계속 유지
  - int 자료형으로 선언된 변수를 string 자료형으로 바꾸는 것은 불가능
```
var number = 10.2; // 실수
number = "변경"; // 문자열
```
#### var 키워드 추가 사용 조건
- 지역 변수로 선언
  - 지역 변수 : 메서드 내부에서 선언되어 있는 변수
```
class Program
{
   var global = 52; // 인스턴스 변수

   static void Main(string[] args)
   {
       var local = 273; // 지역 변수
   }
}
```
  - 변수를 선언과 동시에 초기화
```
static void Main(string[] args)
{
   var number = 20;
}
```
- var number; // 초기화 안되있어서 오류 남

- (참고) var 키워드 선언
  - 정수 선언 시
    - var number = 100; 입력, int 자료형으로 선언
  - 실수 선언 시
    - var number = 10.0; 입력, double 자료형으로 선언
  - long 자료형, float 자료형 선언 시
    - 숫자 뒤에 L, F 등 기호 붙여야 함

#### 예제 2-54 : var키워드를 사용한 다양한 자료형 선언
```
static void Main(string[] args)
{
   var numberA = 100L; // long 자료형
   var numberB = 100.0; // double 자료형
   var numberC = 100.0F; // float 자료형
}
```

### 입력
- C#에서 사용자의 입력을 받을 때 Console.WriteLine() 메서드를 사용
  - 입력 메서드
- 
| 메서드 이름 | 설명 |
|------------|-------|
| Console.ReadLine() | 사용자로부터 한 줄의 문자열을 입력 받습니다 |
- 문자열 입력과 출력
  - Console.ReadLine()메서드는 문자열만 입력 가능
    - 입력 메서드의 반환형 : 자동완성 기능 확인 시, string으로 표시
```
Console.ReadLine()
                 ↳ 표준 입력 스트림에서 다음 줄의 문자를 읽습니다.
```
  - 숫자를 입력 받아 더하는 등의 코드를 만들려면 문자열을 숫자로 바꾸는 방법 필요

#### 2-56 : 문자열 입력과 출력
```
static void Main(string[] args)
{
   string input = Console.ReadLine(); // ReadLine()메서드를 사용한 결과는 string 자료형이므로 string 변수에 저장
   Console.WriteLine("input: " + input);
}

- 결과
아무 것이나 입력
input: 아무 것이나 입력
```

### 자료형 변환
- 자료형 변환이란, 한 자료형을 다른 자료형으로 바꾸는것
```
static void Main(string[] args)
{
   long longnumber = 214783647L + 214783647L; // int의 크기보다 큼
   int intNumber = longNumber; // 데이터 손실
   Console.WriteLine(intNumber);
}
```

#### 강제 자료형 변환
- 자료형 변환 실패 : 데이터 손실 (longNumber 값의 크기 > int의 자료형 크기)
```
static void Main(string[] args)
{
   long Number = 214783647L + 214783647L;
   int intNumber = longNumber;
   Console.Write()
}
```
```
강제 자료형 변환 예시:
- 데이터 손실은 남
- 바꾸려는 자료형의 크기보다 작으면 데이터 손실 ❌, 명시적 형변환 ✅
var a = (int)10.0;
var b = (float)10;
var c = (double)10;
```
```
강제 자료형 변환 데이터 손실 발생하지 않는 예시:
static void Main(string[] args)
{
   long longNumber = 52273;
   int intNumber = (int)longNumber;
   Console.WriteLine(intNumber);
}
```

#### 예제 2-59 : 강제 자료형 변환
```
static void Main(string[] args)
{
   long longNumber = 214783647L + 214783647L;
   int intNumber = (int)longNumber; // long자료형을 int자료형으로 명시적 형변환 = 데이터 손실
   Console.WriteLine(intnumber);
}

- 결과
-2
```

#### 예제 2-61 : 숫자 손상
```
static void Main(string[] args)
{
   long longNumber = 214783647L + 214783647L;
   int longToInt = (int)longnumber; // long형을 int형으로 형변환 데이터 손실이 일어날 수 있음
   Console.WriteLine(longToInt);

   double doubleNumber = 52.27310332;
   int doubleToInt = (int)doubleNumber; // double형을 int형으로 형변환 데이터 손실이 일어날 수 있음
   Console.WriteLine(doubleToInt);
}

- 결과
-2
52
```

#### 자동 자료형 변환
- 
| 기존 자료형 | 자동 변환되는 자료형 |
|-------------|----------------------|
| int(4Byte) | long(8Byte), float(4Byte), double(8Byte) |
| long(8Byte) | float(4byte), double(8Byte) |
| char(2Byte) | int(4Byte), long(8Byte), float(4Byte), double(8Byte) |
| float(4Byte) | double(8Byte) |

#### 예제 2-62 : 자동 자료형 변환
```
static void Main(string[] args)
{
   int intNumber = 2147483647; // int 최댓값으로 초기화

   long intToLong = intNumber; // 자동 형변환
   Console.WriteLine(intToLong);

   double intToDouble = intNumber; // 자동 형변환
   Console.WriteLine(intToDouble);
}

- 결과
214783647
214783647
```

#### 다른 자료형을 숫자로 변환
- 문자열을 숫자로 변환하는 메서드
  - 다른 자료형을 int, long, float, double 자료형으로 변환
- 
| 메서드 이름 | 설명 |
|------------|-------|
| int.Parse() | 다른 자료형을 int 자료형으로 변경 |
| long.Parse() | 다른 자료형을 long 자료형으로 변경 |
| float.Parse() | 다른 자료형을 float 자료형으로 변경 |
| double.Parse() | 다른 자료형을 double 자료형으로 변경 |

#### 예제 2-64 : 문자열을 숫자로 변환
```
static void Main(string[] args)
{
   Console.WriteLine(int.Parse("52"));
   Console.WriteLine(long.Parse("273"));
   Console.WriteLine(float.Parse("52.273")); // 실수로 바꾸려면 "실수"문자열만
   Console.WriteLine(double.Parse("103.32")); // 실수로 바꾸려면 "실수"문자열만
   // 문자열을 숫자로 변환

   Console.WriteLine(int.Parse("52").GetType());
   Console.WriteLine(long.Parse("273").GetType());
   Console.WriteLine(float.Parse("52.273").GetType());
   Console.WriteLine(double.Parse("103.32").GetType());
   // 문자열을 숫자로 변환한 후 자료형의 타입을 확인
}

- 결과
52
273
52.273
103.32
System.Int32
System.Int64
System.Single
System.Double
```
- Parse()메서드를 사용할 때 해당 자료형으로 변환 불가능한 문자
```
예시 : 숫자로 변환할 수 없는 문자열을 변환하는 경우
Console.WriteLine(int.Parse("52.273"));
Console.WriteLine(int.Parse("abc"));
// 형식이 맞아야 함
```

#### 다른 자료형을 문자열로 변환
- ToString() 메서드
  - 다른 자료형을 문자열로 변환할 때 사용하는 메서드
- 
| 메서드 | 설명 |
|--------|------|
| ToString() | 문자열로 변환 |
```
예시:
(10).ToString() : int자료형을 문자열로 변환
(52.273).ToString() : double자료형을 문자열로 변환
```

#### 예제2-66 : 기본 자료형을 문자열로 변환
```
static void Main(string[] args)
{
   Console.WriteLine((52).ToString());
   Console.WriteLine((52.273).ToString());
   Console.WriteLine(('a').ToString());
   Console.WriteLine((true).ToString());
   Console.WriteLine((false).ToString());
   // 정수, 실수, 문자, 불 자료형을 문자열로 변환

   Console.WriteLine((52).ToString().GetType());
   Console.WriteLine((52.273).ToString().GetType());
   Console.WriteLine(('a').ToString().GetType());
   Console.WriteLine((true).ToString().GetType());
   Console.WriteLine((false).ToString().GetType());
   // 변환 후 자료형 타입 변환
}

- 결과
52
52.273
a
True
False
System.String
System.String
System.String
System.String
System.String
```

#### 예제 2-67 : 소수점 제거
```
static void Main(string[] args)
{
   double number = 52.273103;
   Console.WriteLine(number.ToString("0.0"));
   Console.WriteLine(number.ToString("0.00"));
   Console.WriteLine(number.ToString("0.000"));
   Console.WriteLine(number.ToString("0.0000"));
   // 잘려진 소수점 부분은 반올림됨
}

- 결과
52.3
52.27
52.273
52.2731
```

#### 예제 2-68 : 숫자와 문자열 덧셈
```
static void Main(string[] args)
{
   Console.WriteLine(52 + 273); // 숫자끼리 덧셈연산 실행

   Console.WriteLine("52" + 273);
   Console.WriteLine(52 + "273");
   Console.WriteLine("52" + "273");
   // 문자열끼리, 또는 문자열과 숫자간 문자열 연결 연산 수행
}

- 결과
325
52273
52273
52273
```
pg39 부터
