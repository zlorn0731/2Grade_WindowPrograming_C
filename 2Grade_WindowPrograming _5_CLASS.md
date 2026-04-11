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
- while



