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

#### 예제 2-17 : 숫자와 관련된 복합 대입 연산자
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

#### 예제 2-18 : 문자와 관련된 복합 대입 연산자
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

#### 예제 2-19 : 증감 연산자
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

#### 예제 2-20 : 증감 연산자와 전위와 후위
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

#### 예제 2-2
