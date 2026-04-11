# C# 프로그래밍 - 5주차 정리

## 📚 학습 내용
- 반복문과 배열
- while 반복문
- do while 반복문
- for 반복문
- 역 for 반복문
- foreach 반복문
- 중첩 반복문
- break 키워드
- continue 키워드

### 반복문과 배열 이해하기
- 반복문
  - 복사해서 붙여 넣기를 사용한 반복
```
예제 4-1

static void Main(string[] args)
{
   Console.WriteLine("출력");
   Console.WriteLine("출력");
   Console.WriteLine("출력");
   Console.WriteLine("출력");
   Console.WriteLine("출력");
}
```
  - 반복문을 사용한 반복
```
예제 4-2

static void Main(string[] args)
{
   for (int i = 0; i < 1000; i++)
   {
       Console.WriteLine("출력");
   }
}
```
- 기본적인 배열 생성 방법
  - 배열 선언형식과 요소
    - 배열은 동일한 유형이면서 여러 개의 자료를 한꺼번에 처리하기 위한 자료형
```
- 배열의 선언형식
자료형[] 이름 = {자료, 자료}

- 배열의 요소
배열[인덱스]
```

#### 예제 4-3 : 기본적인 배열 생성 방법
```
static void Main(string[] args)
{
   int[] intArray = { 52, 273, 32, 65, 103 };
   long[] longArray = { 52, 273, 32, 65, 103 };
   float[] floatArray = { 1.0F, 2.0F, 3.0F, 4.0F, 5.0F };
   double[] doubleArray = { 1.0, 2.0, 3.0, 4.0, 5.0 };
   char[] charArray = { '가', '나', '다', '라' };
   string[] stringArray = { "윤인성", "연하진", "윤아린" };
}
```

#### 예제 4-4 : 배열 생성하고 요소에 접근
```
static void Main(string[] args)
{
   int[] intArray = { 52, 273, 32, 65, 103 }; // 배열을 생성

   intArray[0] = 0; // 배열의 요소 변경

   // 요소를 출력
   Console.WriteLine(intArray[0]);
   Console.WriteLine(intArray[1]);
   Console.WriteLine(intArray[2]);
   Console.WriteLine(intArray[3]);
}

- 결과
0
273
32
65
```

### (참고)Length 속성
- 배열의 요소 개수(배열의 길이) 확인

#### 예제 4-5 : 배열의 Length 속성
```
static void Main(string args[])
{
   // 배열 생성
   int[] intArray = { 52, 273, 32, 65, 103 };

   // 배열의 길이를 출력
   Console.WriteLine(intArray.Length);
}

- 결과
5
```

### (참고) IndexOutOfRangeException
- 배열의 범위를 벗어나는 인덱스에 접근


#### 예제 4-6 : 배열의 범위를 벗어나는 인덱스에 접근
```
static void Main(string[] args)
{
   // 배열 생성
   int[] intArray = { 52, 273, 32, 65, 103 };

   // 요소를 출력
   Console.WriteLine(intArray[5]);
}

- 결과
오류
```

### 원하는 크기의 배열 생성 방법
- 배열 생성시 요소 값을 넣지 않고 원하는 개수의 배열 공간만 만들기
  - 이때 배열 초기화는 자료형의 기본값 즉, 숫자는 0, 문자열은 빈 문자열로 생성
  - 이후에 알아보는 객체는 null로 초기화
```
int[] array = new int[100];
```

#### 예제 4-8 : 특정한 크기의 배열 생성
- 100개의 공간을 갖는 int 자료형의 배열 생성하기
```
namespace week4wp
{
    internal class Program
    {
        static void Main(string[] args)
        {
            int[] intArray = new int[100]; // 배열 생성

            // 배열의 처음과 마지막 요소를 출력
            Console.WriteLine(intArray[0]);
            Console.WriteLine(intArray[99]);
        }
    }
}

- 결과
0
0
```

### while 반복문
- 가장 기본적인 반복문
- if 조건문과 형식 비슷하나, 불 표현식이 참인 동안 중괄호 안의 문장 계속 실행
  - '...하는 동안' 이라는 의미
  - 즉, 조건이 만족하는 동안 문장을 반복 수행함
```
while (조건[불 표현식])
{
   // 불 표현식이 참인 동안 실행할 문장;
}
[다음 문장]
```
- 무한루프 코드
  - 조건이 변하지 않으면 무한반복되므로 반드시 조건을 거짓으로 만드는 문장 포함

#### 예제 4-9 : 무한 반복
```
static void Main(string[] args)
{
   while (true)
   {
       Console.WriteLine("무한 반복");
   }
}
```

#### 예제 4-10 : while 반복문
```
namespace week4wp
{
    internal class Program
    {
        static void Main(string[] args)
        {
            int i = 0; // 변수 선언
            int[] intArray = { 52, 273, 32, 65, 103 };

            while (i < intArray.Length) // 반복 수 = 5가 되는 순간 false : while 빠져나옴
            {
                Console.WriteLine(i + "번째 출력:" + intArray[i]); // 출력  

                i++; // 탈출을 위해 변수를 더함
            }
        }
    }
}

- 결과
0번째 출력:52
1번쨰 출력:273
2번째 출력:32
3번째 출력:65
4번째 출력:103
```

### do while 반복문
- while 반복문과 유사하나 while문 앞에 do라는 지정어가 추가되고 조건 비교 부분이 마지막에 위치
- 반복되는 문장을 일단 한 번은 실행하고 그 다음에 조건을 검사해 조건이 참이면 계속 반복하고 거짓이면 while문을 빠져나옴
  - while문은 조건이 거짓이면 한 번도 실행하지 않는 반면,
  - do while문은 조건 검사를 나중에 하므로 조건이 거짓이더라도 한 번은 실행
```
do {
   // 불 표현식이 참인 동안 실행할 문장;
} while (조건[불 표현식])
```

#### 예제 4-11 : do while 반복문 활용
```
namespace week4wp
{
    internal class Program
    {
        static void Main(string[] args)
        {
            string input;
            do
            {
                Console.Write("입력(exit를 입력하면 종료): ");
                input = Console.ReadLine();
            } while (input != "exit");
        }
    }
}

- 결과
입력(exit를 입력하면 종료): ㅇㅂㅇ
입력(exit를 입력하면 종료): ㅇㅅㅇ
입력(exit를 입력하면 종료): exit
```

### for 반복문
- 원하는 횟수만큼 반복하기 : <초기식>,<조건식>,<증감식(종결식)>,<문장>으로 구성
- 맨 먼저 초기식 실행 후 조건식 확인
  - <초기식>,<조건식>,<증감식(종결식)>은 세미콜론(;)으로 구분
```
for(<초기식>;<조건식>;<증감식(종결식)>)
{
   문장;
}

for ( int i = 0; i < [반복 횟수]; i++ )
{

}
```
- for 반복문 실행 단계
```
for(<초기식>;<조건식>;<증감식(종결식)>)
      (1)      (2)       (4)

<다음 문장>;         <문장>;
   (5)                (3)

1. 먼저 <초기식>에서 제어변수를 초기화하고
2. <조건식>에서 조건이 참인지 거짓인지를 검사함
3. <조건식>이 참이면 블록 안의 <문장>을 수행하고,
4. <종결식>에 따라 제어변수를 증가시키거나 감소시킴
2. <종결식>에 의해 변경된 값이 적용된 <조건식>이 참인지 검사함
5. 제어변수의 값을 적용한 <조건식>이 거짓이면 <문장>을 수행하지 않고 for문을 빠져 나와서 <다음 문장>이 수행
```

#### 예제 4-12 : for 반복문으로 덧셈
```
namespace week4wp
{
    internal class Program
    {
        static void Main(string[] args)
        {
            int output = 0;

            for (int i = 0; i <= 100; i++) 
            {
                output += i;
            }
            Console.WriteLine(output);
        }
    }
}

- 결과
5050
```

#### 예제 4-13 : for 반복문으로 곱셈
```
namespace week4wp
{
    internal class Program
    {
        static void Main(string[] args)
        {
            long output = 1; // 곱셈의 크기가 커질 수 있으니 int보다 많으 값을 가질 수 있는 long
                          // 초기 값을 0으로 두면 뭘 곱해도 0이니 1로 설정
            for (int i = 1; i <= 20; i++) 
            {
                output *= i;
            }
            Console.WriteLine(output);
        }
    }
}

- 결과
2432902008176640000
```

#### 예제 4-14 : 한글 전부 출력
```
static void Main(string[] args)
{
   for (int  i = '가'; i <= '힣'; i++)
   {
      Console.Write(char(i));
   }
}

- 결과
가
...
힣
```

### (참고) 외부 요인으로 조건 변경
- 시간을 사용한 반복문 이탈
  - for 반복문 많이 사용, while 반복문은 외부 요인으로 조건 변경 되는 경우 사용

#### 예제 4-15 : 시간을 사용한 반복문 이탈
```
namespace week4wp
{
    internal class Program
    {
        static void Main(string[] args)
        {
            long start = DateTime.Now.Ticks;
            long count = 0;

            // 10000000Tick = 1초
            while (start + (10000000) > DateTime.Now.Ticks)
            {
                count++;
            }

            Console.WriteLine(count + "만큼 반복했습니다.");
        }
    }
}

- 결과
32087913만큼 반복했습니다.
```

### 역 for 반복문
- 배열 반복을 뒤에서부터 실행 하는 경우 사용
```
for (int i = length -1; i >= 0; i--)
{

}
```

#### 예제 4-16 : 역 for 반복문
```
namespace week4wp
{
    internal class Program
    {
        static void Main(string[] args)
        {
            int[] intArray = { 1, 2, 3, 4, 5, 6 };

            for (int i = intArray.Length - 1; i >= 0; i--)
            {
                Console.WriteLine(intArray[i]);
            }
        }
    }
}

- 결과
6
5
4
3
2
1
```

### foreach 반복문
- 반복문을 컬렉션에 쉽게 적용할 때 사용
  - 컬레션 : 여러 개체가 모여서 집합을 이룬 것
```
foreach (자료형 변수 in 컬렉션)
{

}

for (int i = 0; i < 컬렉션.길이; i++)
{
   자료형 변수 = 컬렉션[i];
}
```

#### 예제 4-17 : foreach 반복문과 배열
```
namespace week4wp
{
    internal class Program
    {
        static void Main(string[] args)
        {
            string[] array = { "사과", "배", "포도", "딸기", "바나나" };

            foreach(string item in array)
            {
                Console.WriteLine(item);
            }
        }
    }
}

- 결과
사과
배
포도
딸기
바나나
```

#### 예제 4-18 : foreach 반복문과 var 키워드
- var 키워드 : 자료형을 자동 지정 (C#에서 일반적)
```
namespace week4wp
{
    internal class Program
    {
        static void Main(string[] args)
        {
            string[] array = { "사과", "배", "포도", "딸기", "바나나" };

            foreach(var item in array)
            {
                Console.WriteLine(item);
            }
        }
    }
}

- 결과
사과
배
포도
딸기
바나나
```

### 중첩 반복문
- 반복문을 여러 번 중첩해서 사용하는 형태의 반복문

#### 예제 4-20 : 별 피라미드(1)
- 1차원(한 줄) 출력 시, 반복문은 한 겹
- 2차원(면) 출력 시, 반복문은 두 겹
```
namespace week4wp
{
    internal class Program
    {
        static void Main(string[] args)
        {
            for (int i = 0; i < 10; i++) 
            {
                for (int j = 0; j < i + 1; j++) // i + 1 ⭐
                    Console.Write('*');
                Console.Write('\n');
            }
        }
    }
}

- 결과
*
**
***
****
*****
******
*******
********
*********
**********
```

#### 예제 4-21 : 별 피라미드(2)
```
namespace week4wp
{
    internal class Program
    {
        static void Main(string[] args)
        {
            for (int i = 0; i < 10; i++) 
            {
                for (int j = 0; j < 10 - i; j++)
                    Console.Write(' ');
                for (int j = 0; j < i + 1; j++) 
                    Console.Write('*');
                Console.WriteLine('\n');
            }
        }
    }
}

- 결과
          *

         **

        ***

       ****

      *****

     ******

    *******

   ********

  *********

 **********
```

### break 키워드
- switch 조건문 또는 반복문을 벗어날 때 사용하는 키워드
- switch문, for문, while문, do while문의 제어를 벗어나기 위해 사용할 수 있음
- 무한 반복문은 내부에서 break 키워드를 사용해야 벗어날 수 있음
```
for (초기식;조건식;증감식)
{
   문장1;
  if(조건식)
       break;
   문장2;
}
문장3;
```

#### 예제 4-22 : break 키워드
- 짝수를 입력하면 break 키워드로 반복문 벗어나고, 홀수 입력하면 무한반복하며 입력 요구하기
```
namespace week4wp
{
    internal class Program
    {
        static void Main(string[] args)
        {
            while (true)
            {
                Console.Write("숫자를 입력해주세요(짝수를 입력하면 종료): ");
                int input = int.Parse(Console.ReadLine());
                if (input % 2 == 0)
                {
                    break;
                }
            }
        }
    }
}

- 결과
숫자를 입력해주세요(짝수를 입력하면 종료): 31
숫자를 입력해주세요(짝수를 입력하면 종료): 51
숫자를 입력해주세요(짝수를 입력하면 종료): 61
숫자를 입력해주세요(짝수를 입력하면 종료): 52
```

#### (참고) 원하는 반복문 벗어나기
- goto 키워드
#### 예제 4-23 : goto 키워드
```
namespace week4wp
{
    internal class Program
    {
        static void Main(string[] args)
        {
            for (int i = 0; i < 10; i++)
            {
                Console.WriteLine("외부 반복문");
                for (int j = 0; j < 10; j++)
                {
                    Console.WriteLine("내부 반복문");
                    goto doNotUse;
                }
            }
        doNotUse:
            Console.WriteLine("goto 키워드");
        }
    }
}

- 결과
외부 반복문
내부 반복문
goto 반복문
```

### continue 키워드
- 반복문 내부에서 현재 반복을 멈추고 다음 반복을 진행하게 하는 키워드

#### 예제 4-24 : continue 키워드
- 변수 i가 짝수일 때 continue 키워드로 현재 반복을 멈추고 다음 반복을 진행하기
- 즉, 짝수는 출력하지 않고 홀수만 출력하기
```
namespace week4wp
{
    internal class Program
    {
        static void Main(string[] args)
        {
            for (int i = 1; i < 10; i++) 
            {
                if (i % 2 == 0)
                {
                    continue;
                }
                Console.WriteLine(i);
            }
        }
    }
}

- 결과
1
3
5
7
9
```
6주차 응용예제 부터 정리 요함
