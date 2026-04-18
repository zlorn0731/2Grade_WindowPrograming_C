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
- 클래스
  - 하나의 객체가 갖는 모든 속성을 한꺼번에 묶어서 처리
  - 차량번호, 입차시간, 출차시간은 모두 하나의 자동차(객체)가 갖는 속성
  - 따라서 3개 속성을 한꺼번에 묶어서 처리할 수 있도록 int 자료형 3개를 저장하는 새로운 자료형을 사용자가 정의
    → 객체지향언어의 클래스 기능
```
(예시) 주차관리시스템

class Car
{
   int carNumber;
   int inTime;
   int outTime;
}

static void Main(string[] args)
{
   Car[] cars = new Car[10];
}
```
- 클래스
  - 속성을 나타내는 변수와 더불어 행위를 나타내는 메서드 포함
```
(예시) 주차관리시스템 - 메서드 사용 코드 포함

class Car
{
   int carNumber;
   DateTIme intTime;
   DateTime outTime;

   public void SetInTime() // 입차 시간 기록
   {
      this.inTime = DateTime.Now;
   }

   public void SetOutTime() // 출차 시간 기록
   {
      this.outTime = DateTime.Now;
   }
}

static void Main(string[] args)
{
   Car car = new Car();
   Car.SetInTime(); // Main 메서드 짧아짐 : 가독성 ↑
   Car.SetOutTime(); // Main 메서드 짧아짐 : 가독성 ↑
}
```
- 클래스와 인스턴스
```
대문자   소문자            클래스 이름과 동일  
 Car     car    =    new       Car()
클래스  인스턴스    new 키워드   생성자

(1) 클래스 : 사용자 정의 자료형
(2) 인스턴스(객체) : 클래스 자료형을 변수로 선언한 것
(3) 생성자 : 클래스 이름과 같은 메서드(클래스 이름 뒤에 괄호가 붙은 것)

- 클래스 이름 대문자로 시작(관례)
```

### 클래스 사용
- Random 클래스
  - 임의의 숫자 생성시 사용
```
(인스턴스 생성 방법)
Random random = new Random();
```

#### 예제 5-1 : Random 클래스를 사용한 임의의 정수 생성
```
namespace week7wp
{
    internal class Program
    {
        static void Main(string[] args)
        {
            Random random = new Random();

            Console.WriteLine(random.Next(10, 100)); // 지정된 범위 내의 임의의 정수를 반환
            Console.WriteLine(random.Next(10, 100));
            Console.WriteLine(random.Next(10, 100));
            Console.WriteLine(random.Next(10, 100));
            Console.WriteLine(random.Next(10, 100));
        }
    }
}

- 결과
84
39
85
47
19
```
- Random.Next 메서드
```
(오버로드)
Next() - 음수가 아닌 임의의 정수를 반환
Next(Int32) - 지정된 최댓값보다 작은 음수가 아닌 임의의 정수를 반환
Next(Int32, Int32) - 지정된 범위 내의 임의의 정수를 반환

(예시)
Console.WriteLine(random.Next());
Console.WriteLine(random.Next(50));
Console.WriteLine(random.Next(10, 100));
```

#### 예제 5-2 : Random 클래스를 사용한 임의의 실수 생성
```
namespace week7wp
{
    internal class Program
    {
        static void Main(string[] args)
        {
            Random random = new Random();

            Console.WriteLine(random.NextDouble()); // 0.0과 1.0사이의 난수를 반환 : 0.0 ≤ number < 1.0
            Console.WriteLine(random.NextDouble());
            Console.WriteLine(random.NextDouble());
            Console.WriteLine(random.NextDouble());
        } 
    }
}

- 결과
0.8749688181574229
0.2175316390076386
0.3856935823507519
0.08836585163370081
```

#### 예제 5-3 : 원하는 범위의 실수 난수 생성
```
namespace week7wp
{
    internal class Program
    {
        static void Main(string[] args)
        {
            Random random = new Random();

            Console.WriteLine(random.NextDouble() * 10);
            Console.WriteLine(random.NextDouble() * 10);
            Console.WriteLine(random.NextDouble() * 10);
            Console.WriteLine(random.NextDouble() * 10);

        }
    }
}

- 결과
9.508407164526126
4.832979633380145
0.6922545108025424
3.473931279628273
```

#### Random 클래스
- Random 클래스 메서드 사용
  - 인스턴스(random)을 생성한 후 인스턴스 뒤에 .을 찍고 메서드를 사용
```
random.Next(10)
random.Next(10, 100)
random.NextDouble()
```
- 인스턴스 멤버 : 인스턴스 뒤에 .을 찍고 사용하는 멤버를 말함.
```
해당 멤버가 변수이면, 인스턴스 변수
해당 멤버가 메서드라면, 인스턴스 메서드
해당 멤버가 속성이라면, 인스턴스 속성
```

#### List 클래스
- 배열과 유사하나, 크기가 가변적인 배열을 만듦
  - 배열은 크기가 고정
```
(namespace(전처리문) 참조 필요)
using System.Collections.Generic;

참조 오류 보조 기능 : [Ctrl] + [.]
```

#### 예제 5-4 : 배열 생성
```
static void Main(string[] args)
{
   int[] intArray = new int[10];
   long[] longArray = new long[10];
   string[] stringArray = new string[10];
}
```

#### 예제 5-5 : List 클래스의 인스턴스 생성
- 제네릭(Generic) : 클래스 선언 시 어떤 자료형인지 알려주기 위해 사용
  - 클래스명 뒤에 < >로 적용
```
static void Main(string[] args)
{
   // 인스턴스 생성
   List<int> list = new List<int>();
}
```

#### 예제 5-6 : 리스트 요소 추가
```
namespace week7wp
{
    internal class Program
    {
        static void Main(string[] args)
        {
            List<int> list = new List<int>(); // 변수 선언

            // 리스트 요소 추가 : Add()메서드
            list.Add(52);
            list.Add(273);
            list.Add(32);
            list.Add(64);

            // 반복 수행
            foreach (var item in list)
            {                                     ↱ Count 속성 : 리스트의 요소개수 가져옴 
                Console.WriteLine("Count: " + list.Count + "\titem: " + item);
            }
        }
    }
}

- 결과
Count: 4        item: 52
Count: 4        item: 273
Count: 4        item: 32
Count: 4        item: 64
```

#### 예제 5-7 : List 인스턴스 생성과 동시에 요소 추가
```
namespace week7wp
{
    internal class Program
    {
        static void Main(string[] args)
        {
            List<int> list = new List<int>() { 52, 273, 32, 64 };

            foreach (var item in list)
            {
                Console.WriteLine("Count: " + list.Count + "\titem: " + item);
            }
        }
    }
}

- 결과
Count: 4        item: 52
Count: 4        item: 273
Count: 4        item: 32
Count: 4        item: 64
```

#### 예제 5-8 : 리스트 요소 제거
```
namespace week7wp
{
    internal class Program
    {
        static void Main(string[] args)
        {
            List<int> list = new List<int>() { 52, 273, 32, 64 }; // 리스트 생성과 동시에 요소 추가 가능

            // list.Remove(list[3]); // 이렇게 써도 가능
            list.Remove(64); // Remove() 메서드 : 리스트 요소 제거

            foreach (var item in list)
            {
                Console.WriteLine("Count: " + list.Count + "\titem: " + item);
            }
        }
    }
}

- 결과
Count: 3        item: 52
Count: 3        item: 273
Count: 3        item: 32
```

#### Math 클래스
- 수학과 관련된 변수 또는 메서드 제공
- Math 클래스는 인스턴스를 만들지 않고 클래스명.멤버 형태로 바로 사용
- 
| 메서드 이름 | 설명 |
|------------|------|
| Abs(n) | 절대 값을 구함 |
| Ceiling(n) | 지정된 숫자보다 크거나 같은 최소 정수를 구함 |
| Floor(n) | 지정된 숫자보다 작거나 같은 최대 정수를 구함 |
| Max(n, n) | 두 개의 매개변수 중에서 큰 값을 구함 |
| Min(n, n) | 두 개의 매개변수 중에서 작은 값을 구함 |
| Round(n) | 반올림 |

#### 예제 5-9 : Math 클래스 활용
```
namespace week7wp
{
    internal class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine(Math.Abs(-52273));
            Console.WriteLine(Math.Ceiling(52.273));
            Console.WriteLine(Math.Floor(52.273));
            Console.WriteLine(Math.Max(52, 273));
            Console.WriteLine(Math.Min(52, 273));
            Console.WriteLine(Math.Round(52.273));
        }
    }
}

- 결과
52273
53
52
273
52
52
```

#### Math 클래스
- Math 클래스의 메서드 사용
  - 클래스 멤버 : 클래스명 뒤에 .을 찍고 사용하는 멤버를 말함
```
Math.PI
Math.Abs()
```
```
해당 멤버가 변수이면, 클래스 변수
해당 멤버가 메서드이면, 클래스 메서드
해당 멤버가 속성이면, 클래스 속성
```

### 클래스 생성
- 클래스 생성 형식
  - class 키워드 사용
  - 클래스 이름의 첫 글자는 주로 대문자 사용
```
class [클래스 이름]
{

}
```

#### 하나의 파일에 여러 개의 클래스 생성
- 가장 쉬운 클래스 셍성 방법
  - 파일 하나에 여러 개의 클래스를 생성하기
  - C# 콘솔 프로젝트 생성 시 C# 파일 (Program.cs)이
    기본 생성되면 이 파일 내부에 클래스 추가
    - 생성된 클래스 확인하기
```
namespace week7wp
{
    class FirstClass
    {

    }
    class SecondClass
    {

    }
    internal class Program
    {
        static void Main(string[] args)
        {
            
        }
    }
}
```

#### 클래스 내부에 클래스 생성
- 하나의 클래스 내부에 여러 개의 클래스 생성 가능
```
namespace week7wp
{
    internal class Program
    {
        class FirstClasss
        {

        }
        class SecondClass
        {

        }
        static void Main(string[] args) // Program클래스에 추가된 클래스는 Main 메서드 내부에서 사용 가능
        {
            
        }
    }
}
```

#### 서로 다른 파일에 클래스 생성
- 파일 하나에 클래스 하나를 넣고, 파일 이름과 맞추어 만드는 것이 일반적
- 파일의 이름과 클래스 이름이 달라도 상관없음
  - 일반적으로 Program.cs 파일에는 하나의 Program 클래스가 존재
```
using System;

namespace week7wp
{
    internal class Program
    {
        static void Main(string[] args)
        {

        }
    }
}
```
- (1) 마우스 오른쪽 클릭 [추가] - [새 항목] 또는 [클래스] 클릭
- (2) 새 파일 대화상자 실행되면, 클래스 이름을 입력하고 [추가] 버튼 클릭

### 클래스의 변수
- 인스턴스 변수 생성 방법
  - 인스턴스 변수는 [인스턴스].[변수 이름]의 형태로 사용
  - 소문자로 시작하여 여러 개를 만들 수 있음
  - 클래스 내부에 선언
```
[접근 제한자] [자료형] [이름]
```

#### 예제 5-11 : 인스턴스 변수 선언
```
class User
{
   public string name;
   public string password;
   public string address;
   public string phoneNumber;
   public DateTime regDate;
}
```

#### 예제 5-12 : 인스턴스 변수 생성과 사용
```
namespace week7wp
{
    internal class Program
    {
        class Product
        {
            public string name = "";
            public int price;
        }
        static void Main(string[] args)
        {
            Product product  = new Product();
        }
    }
}
```

#### 예제 5-13 : 인스턴스 변수 사용
```
namespace week7wp
{
    internal class Program
    {
        class Product
        {
            public string name = "";
            public int price;
        }
        static void Main(string[] args)
        {
            Product product  = new Product(); // 인스턴스 생성

            // 인스턴스 변수 변경
            product.name = "감자"; 
            product.price = 2000;

            // 인스턴스 변수 출력
            Console.WriteLine(product.name + " : " + product.price + "원");
        }
    }
}

- 결과
감자 : 2000원
```

#### 예제 5-14 : 인스턴스 변수를 생성할 때 초기화
```
class Product
{
    public string name = "default";
    public int price = 1000;
}
```

#### 예제 5-15 : 인스턴스 변수 생성과 동시에 초기화
```
namespace week7wp
{
    internal class Program
    {
        class Product
        {
            public string name = "";
            public int price;
        }
        static void Main(string[] args)
        {
            Product productA = new Product() { name = "감자", price = 2000 };
            Product productB = new Product() { name = "고구마", price = 3000 };
        }
    }
}
```

### 클래스 변수와 클래스 메서드
- 클래스 이름으로 곧바로 사용하는 변수의 메서드
- 클래스 변수 생성 방법
  - static 키워드 사용
```
[접근 제한자] static [자료형] [이름]
```
  - Math 클래스의 클래스 메서드

#### 예제 5-16 : 클래스 변수 생성과 사용
```
namespace week7wp
{
    internal class Program
    {
        class MyMath
        {
            public static double PI = 3.141592;
        }
        static void Main(string[] args)
        {
            Console.WriteLine(MyMath.PI);
        }
    }
}

- 결과
3.141592
```

##### ✍️작성자: 박지안
##### 🐧실습 환경: Visual Studio 2022
##### 🗓️ 작업일: 2026-04-18
