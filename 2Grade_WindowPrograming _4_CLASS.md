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
