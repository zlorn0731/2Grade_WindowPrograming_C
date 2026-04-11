# C# 프로그래밍 - 5주차 정리

## 📚 학습 내용
- if 조건문
- if-else 조건문
- 중첩 조건문
- if else if 조건문
- switch 조건문
- 삼항연산자

### 제어문의 이해
- 
| 구문 | 제어 명령 |
|------|-----------|
| 조건문 | if문, if-else문, 중첩 조건문, if else if문, switch문 |
| 반복문 | for문, 역for문, while문, do~while문, foreach문, 중첩 반복문 |
| 보조 제어문 | break문, continue문 |

### 조건문 
- 조건에 따라 판단해서 원하는 문장만 수행하고자 할 때 사용
- if, if-else, 중첩, if else if, switch 조건문 등

### if 조건문
- if문은 주어진 조건을 만족하는 경우에만 특정 문장을 수행하도록 하는 제어문
  - 조건(boolean 표현식)의 결과가 참이면 if문 바로 다음에 나오는 문장을 수행
  - 결과가 거짓이면 이 문장을 수행하지 않고 바로 다음 문장을 수행
  - 즉, 특정 문장을 수행할지 여부를 결정
```
if (조건[불 표현식])
{
   // 조건에 만족하면 수행되는 문장;
}
[다음 문장]
```
- if문의 순서도
```
    [문장]
      ↓
    <조건>→→→→참→→→→[조건에 만족하면 수행되는 문장]
      ↓거짓←←←←←←←←←←←←←←←←←←←←←←←↲
  [다음 문장]
```
- (예제)if문을 사용해서 절댓값을 구하는 프로그램
```
[정수값을 결정]
      ↓
  <음수인가?>→→→→참→→→→[부호를 변경]
      ↓거짓←←←←←←←←←←←←←←←←↲
 [변수를 출력]
```

#### 예제 3-1 : 홀수 짝수 구분하기
```
namespace week4wp
{
    internal class Program
    {
        static void Main(string[] args)
        {
            Console.Write("숫자 입력: ");
            int input = int.Parse(Console.ReadLine());

            if(input % 2 == 0)
            {
                Console.WriteLine("짝수입니다!");
            }
            if(input % 2 == 1) 
            {
                Console.WriteLine("홀수입니다!");
            }
        }
    }
}

- 결과
숫자 입력: 52273
홀수입니다!
```

#### 예제 3-2 : 중괄호 사용
```
// 중괄호 사용 방식(1)
if (true)
{

}

// 중괄호 사용 방식(2)
if (true) {

}
```

#### 예제 3-3 : 현재 시간 구하기
```
namespace week4wp
{
    internal class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine(DateTime.Now.Year);
            Console.WriteLine(DateTime.Now.Month);
            Console.WriteLine(DateTime.Now.Day);
            Console.WriteLine(DateTime.Now.Hour);
            Console.WriteLine(DateTime.Now.Minute);
            Console.WriteLine(DateTime.Now.Second);
        }
    }
}

- 결과
2026
04
11
19
5
44
```

#### 예제 3-4 : 오전과 오후 구분하기
```
namespace week4wp
{
    internal class Program
    {
        static void Main(string[] args)
        {
            if(DateTime.Now.Hour < 12)
            {
                Console.WriteLine("오전입니다.");
            }
            if(DateTime.Now.Hour >= 12)
            {
                Console.WriteLine("오후입니다.");
            }
        }
    }
}

- 결과
오후입니다.
```

### if-else 조건문
- if-else문은 2가지 경우 중 한 가지만 선택할 때 사용되는 제어문
  - if문 계열 중 가장 많이 사용하는 방식
  - 2가지로 분명하게 나뉠 때 응용
  - 문장이 여러 줄이면 중괄호 반드시 사용
```
[문장]
if (조건[불 표현식])
{
   // 조건에 만족할 때(불 표현식이 참일 때) 수행되는 문장;
}
else
{
   // 조건에 만족하지 않을 때(불 표현식이 거짓일 때) 수행되는 문장;
}
[다음 문장]
```
- if-else문의 순서도
```
                                   [문장]
                                      ↓
[조건에 만족할 때 수행되는 문장]←←←←←←<조건>→→→→→→[조건에 만족할 때 수행되는 문장]
               ↳→→→→→→→→→→→→→→→→→→→→→→→←←←←←←←←←←←←←←←←←←←←←←←↲
                                      ↓
                                 [다음 문장]
```
- if-else문 사용해 주어진 정수형 데이터의 짝수/홀수를 판별하는 프로그램
```
                                [정수값 입력]
                                      ↓
                     [홀수다.]←←←←←←<조건>→→→→→→[짝수다.]
                        ↳→→→→→→→→→→→→→←←←←←←←←←←←←←↲
                                      ↓
                                 [다음 문장]
```

#### 예제 3-5 : 홀수 짝수 구분하기
```
namespace week4wp
{
    internal class Program
    {
        static void Main(string[] args)
        {
            Console.Write("숫자 입력: ");
            int input = int.Parse(Console.ReadLine());

            if(input % 2 == 0)
            {
                Console.WriteLine("짝수입니다!");
            }
            else
            {
                Console.WriteLine("홀수입니다!");
            }
        }
    }
}

- 결과
52272
짝수입니다!
```

#### 예제 3-6 : 오전과 오후 구분하기
```
namespace week4wp
{
    internal class Program
    {
        static void Main(string[] args)
        {
            if(DateTime.Now.Hour < 12)
            {
                Console.WriteLine("오전입니다.");
            }
            else
            {
                Console.WriteLine("오후입니다.");
            }
        }
    }
}

- 결과
오후입니다.
```

### 중첩 조건문
- 조건문 안에 조건문을 중첩해 사용하는 형태의 제어문
  - if-else문은 참, 거짓을 선택하는 과정에서 한 번만 사용
  - 이에 반해, 경우의 수가 둘이 아닌 셋 이상에서 하나를 선택해야 할 경우에 if-else문을 중첩해서 사용
```
if (조건1[불 표현식])
{
  if (조건2[불 표현식])
  {
     문장1;
  }
  else
  {
     문장2;
  }
}
else
{
  if (조건3[불 표현식])
  {
     문장3;
  }
  else
  {
     문장4;
  }
}
[다음 문장]
```
- 중첩 조건문의 순서도
```
<조건1>→→→→→→→→→→→→→→→→거짓→→→→→→→→→→→→→→↓  
  ↓참                                   ↓ 
<조건2>→→→→→거짓→→→→→→→→↓             <조건3>→→→→→→거짓→→→→→↓
  ↓참                  ↓                ↓                  ↓
[문장1]             [문장2]             ↓참                ↓
  ↓                    ↓             [문장3]            [문장4]
  ↓                    ↓                ↓                 ↓
  ↓                    ↓                ↓                 ↓
  ↓                    ↓                ↓                 ↓
[다음 문장]←←←←←←←←←←←←←←←←←←←←←←←←←←←←←←←←←←←←←←←←←←←←←←←←↓
```

#### 예제 3-7 : 중첩 조건문 활용
```
namespace week4wp
{
    internal class Program
    {
        static void Main(string[] args)
        {
            if(DateTime.Now.Hour < 11)
            {
                Console.WriteLine("아침 먹을 시간입니다.");
            }
            else
            {
                if(DateTime.Now.Hour < 15)
                {
                    Console.WriteLine("점심 먹을 시간입니다.");
                }
                else
                {
                    Console.WriteLine("저녁 먹을 시간입니다.");
                }
            }
        }
    }
}

- 결과
저녁 먹을 시간입니다.
```

### if else if 조건문
- 중첩 조건문에서 중괄호 생략 시 만들어지는 조건문
```
if (조건1[불 표현식])
{
   조건1에 만족 할 때 처리할 문장1;
}
else if (조건2[불 표현식])
{
   조건1에 만족하지 않지만 조건2에 만족할 때 처리할 문장2;
else if (조건3[불 표현식])
{
   조건1~2에 만족하지 않지만 조건3에 만족할 때 처리할 문장3;
}
else
{
   위에서 언급한 모든 조건에 대해서 만족하지 않을 때 처리할 문장4;
}
[다음 문장]
```
- if else if문 순서도
```
<조건1>→→→→→→거짓→→→→→→→↓  
  ↓참                  ↓                  
  ↓                 <조건2>→→→→거짓→→→→→↓
  ↓                    ↓             <조건3>→→→→→→거짓→→→→↓
  ↓참                  ↓참              ↓                ↓
[문장1]             [문장2]             ↓참               ↓
  ↓                    ↓             [문장3]           [문장4]
  ↓                    ↓               ↓                 ↓
  ↓                    ↓               ↓                 ↓
  ↓                    ↓               ↓                 ↓
[다음 문장]←←←←←←←←←←←←←←←←←←←←←←←←←←←←←←←←←←←←←←←←←←←←←←←↓
```

#### 예제 3-8 : if else if 조건문
```
namespace week4wp
{
    internal class Program
    {
        static void Main(string[] args)
        {
            if (DateTime.Now.Hour < 11)
            {
                Console.WriteLine("아침 먹을 시간입니다.");
            }
            else if (DateTime.Now.Hour < 15)
            {
                Console.WriteLine("점심 먹을 시간입니다.");
            }
            else
            {
                Console.WriteLine("저녁 먹을 시간입니다.");
            }
        }
    }
}

- 결과
저녁 먹을 시간입니다.
```

### 논리 연산자와 조건문
```
double score = 2.0;
if ( 4.0 < score < 4.5) { }

// 오류 코드
```

#### 예제 3-9 : 논리 연산자와 조건문
```
namespace week4wp
{
    internal class Program
    {
        static void Main(string[] args)
        {
            Console.Write("학점을 입력하시오: ");
            double score = double.Parse(Console.ReadLine());


            if (score == 4.5)
            {
                Console.WriteLine("신");
            }
            else if (4.2 <= score && score < 4.5)
            {
                Console.WriteLine("교수님의 사랑");
            }
            else if (3.5 <= score && score < 4.2)
            {
                Console.WriteLine("현 체제의 수호자");
            }
            else if (2.8 <= score && score < 3.5)
            {
                Console.WriteLine("일반인");
            }
            else if (2.3 <= score && score < 2.8)
            {
                Console.WriteLine("일탈을 꿈꾸는 소시민");
            }
            else if (1.75 <= score && score < 2.3)
            {
                Console.WriteLine("오락문화의 선구자");
            }
            else if (1.0 <= score && score < 1.75)
            {
                Console.WriteLine("불가촉천민");
            }
            else if (0.5 <= score && score <1.0)
            {
                Console.WriteLine("자벌레");
            }
            else if (0 < score && score <0.5)
            {
                Console.WriteLine("플랑크톤");
            }
            else
            {
                Console.WriteLine("시대를 앞서가는 혁명의 씨앗");
            }

        }
    }
}

- 결과
학점을 입력하시오:

```

#### 예제 3-10 : 조건문 간단 사용
```
namespace week4wp
{
    internal class Program
    {
        static void Main(string[] args)
        {
            Console.Write("학점을 입력하시오: ");
            double score = double.Parse(Console.ReadLine());


            if (score == 4.5)
            {
                Console.WriteLine("신");
            }
            else if (4.2 <= score)
            {
                Console.WriteLine("교수님의 사랑");
            }
            else if (3.5 <= score)
            {
                Console.WriteLine("현 체제의 수호자");
            }
            else if (2.8 <= score)
            {
                Console.WriteLine("일반인");
            }
            else if (2.3 <= score)
            {
                Console.WriteLine("일탈을 꿈꾸는 소시민");
            }
            else if (1.75 <= score)
            {
                Console.WriteLine("오락문화의 선구자");
            }
            else if (1.0 <= score)
            {
                Console.WriteLine("불가촉천민");
            }
            else if (0.5 <= score)
            {
                Console.WriteLine("자벌레");
            }
            else if (0 < score)
            {
                Console.WriteLine("플랑크톤");
            }
            else
            {
                Console.WriteLine("시대를 앞서가는 혁명의 씨앗");
            }

        }
    }
}

- 결과
학점을 입력하시오:

```

### switch 조건문
- switch문은 if else if문과 같은 용도로 쓰임
  - if else if문이 참이나 거짓의 결과를 문장의 행태로 수행하는 반면 switch문은
    정수식에 따라 분기함 (조건에 맞는 cas문으로 분기)
    - break 키워드는 switch 조건문 또는 반복문을 빠져나갈 때 사용
    - switch 조건문 괄호 안에는 비교할 값 입력, 입력값을 기준으로 특정 코드 실행
    - 입력한 표현식과 case 키워드 옆의 표현식 같으면, 키워드 다음 문장을 차례로 실행
```
문장1;

switch (비교할 값[정수식])
{
   case 값1: 문장2; [break;]
   case 값2: 문장3; [break;]
   case 값3: 문장4; [break;]
   ....
   [default:] 문장 n;
}
다음 문장;
```
- switch문의 순서도
```
                  [문장]
                     ↓
          ↓←←←←←←←<정수식>→→→→→→→↓ 
          ↓          ↓          ↓
       [문장2]     [문장3]    [문장n]
          ↓          ↓          ↓
          ↓→→→→→→→→→→↓←←←←←←←←←←↓
                     ↓
                [다음 문장]
```
- switch문은 if else if문과 같은 용도로 쓰임
  - switch문에서는 break문을 생략할 수 있는데, break문이 없으면 if문에서 논리합 연산자(||)와 유사한 기능을 수행하므로 코드가 간단해 짐
```
switch (비교할 값)
{
   case 값:
       문장
       break;
   case 값:
       문장
       break;
   default:
       문장
       break;
}
```

#### 예제 3-11 : switch 조건문
```
namespace week4wp
{
    internal class Program
    {
        static void Main(string[] args)
        {
            Console.Write("숫자를 입력하세요: ");
            int input = int.Parse(Console.ReadLine());

            switch (input % 2)
            {
                case 0:
                    Console.WriteLine("짝수입니다.");
                    break;
                case 1:
                    Console.WriteLine("홀수입니다.");
                    break;
            }
        }
    }
}

- 결과
273
홀수입니다.
```

#### 예제 3-12 : break 키워드를 사용하지 않는 switch 조건문
```
namespace week4wp
{
    internal class Program
    {
        static void Main(string[] args)
        {
            Console.Write("이번 달은 몇 월인가요: ");
            int input = int.Parse(Console.ReadLine());

            switch (input)
            {
                case 12:
                case 1:
                case 2:
                    Console.WriteLine("겨울입니다.");
                    break;
                case 3:
                case 4:
                case 5:
                    Console.WriteLine("봄입니다.");
                    break;
                case 6:
                case 7:
                case 8:
                    Console.WriteLine("여름입니다.");
                    break;
                case 9:
                case 10:
                case 11:
                    Console.WriteLine("가을입니다.");
                    break;
                default:
                    Console.WriteLine("대체 어떤 행성에 살고 계신가요?");
                    break;
            }
        }
    }
}

- 결과
이번 달은 몇 월인가요: 12
겨울입니다.
```

### 삼항 연산자
- if문, switch문 이외에도 조건을 구분할 때 사용 가능한 연산자
  - 연산자이지만 프로그램의 진행을 조건에 따라 변화시킬 수 있음
```
[불 표현식] ? [참] : [거짓]
```

#### 예제 3-13 : 삼항 연산자
```
// 참과 거짓 위치에 불 자료형 사용
Console.WriteLine(number % 2 == 0 ? true : false);

// 참과 거짓 위치에 문자열 자료형 사용
Console.WriteLine(number % 2 == 0 ? "짝수" : "홀수");
```

#### 예제 3-14 : 삼항 연산자를 이용한 자연수 판별
```
namespace week4wp
{
    internal class Program
    {
        static void Main(string[] args)
        {
            // 변수를 선언
            string input = Console.ReadLine();
            int number = int.Parse(input);

            // 조건 구분
            Console.WriteLine(number > 0 ? "자연수입니다" : "자연수가 아닙니다");
        }
    }
}

- 결과
-52273
자연수가 아닙니다
```

### 응용 예제

#### 응용 예제 3-1 : 입력 받아 조건 분활
- string.Contains() 메서드
  - Contains() 메서드의 반환(리턴)형은 bool타입
  - 반환이 bool자료형이라면 if 조건문의 불_표현식에 사용할 수 있음
- 간단하게 입력 받고 입력에 안녕이라는 글자가 들어있으면 안녕하세요...! 출력
```
간단하게 입력 받고 입력에 안녕이라는 글자가 들어있으면 안녕하세요...! 출력

namespace week4wp
{
    internal class Program
    {
        static void Main(string[] args)
        {
            Console.Write("입력: ");
            string line = Console.ReadLine();

            if (line.Contains("안녕"))
            {
                Console.WriteLine("안녕하세요...!");
            }
            else
            {
                Console.WriteLine("^^");
            }
        }
    }
}

- 결과
입력: 안녕안녕..!
안녕하세요...!
```

#### 응용 예제 3-2 : 키 입력 구분
- ReadKey() 메서드
  - if 조건문과 switch 조건문 중 일반적으로 if 조건문 사용
  - 다만, 고정된 값을 많이 비교해야 할 때 switch조건문을 사용하는 것이 일반적
  - 대표적으로 키 입력을 구분하는 경우 switch 조건문 사용
  - Key 속성은 ConsoleKey 자료형
  - ConsoleKey 자료형은 "입력할 수 있는 키의 모음"
- ReadKey() 메서드는 ConsoleKeyInfo 객체를 받게 되는데, 이 객체 내부의 Key 속성을 사용하면 어떤 키를 입력했는지 알 수 있음
```
키보드의 화살표 키를 인식하고 switch 조건문을 사용해 분기

namespace week4wp
{
    internal class Program
    {
        static void Main(string[] args)
        {
            ConsoleKeyInfo info = Console.ReadKey();
            switch(info.Key)
            {
                case ConsoleKey.UpArrow:
                    Console.WriteLine("위쪽으로 이동");
                    break;
                case ConsoleKey.RightArrow:
                    Console.WriteLine("오른쪽으로 이동");
                    break;
                case ConsoleKey.LeftArrow:
                    Console.WriteLine("왼쪽으로 이동");
                    break;
                case ConsoleKey.DownArrow:
                    Console.WriteLine("아래쪽으로 이동");
                    break;
                default:
                    Console.WriteLine("다른 키를 눌렀습니다");
                    break;
            }
        }
    }
}
```

##### ✍️작성자: 박지안
##### 🐧실습 환경: Visual Studio 2022
##### 🗓️ 작업일: 2026-04-11
