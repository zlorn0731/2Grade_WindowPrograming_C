# C# 프로그래밍 - 9주차 정리

## 📚 학습 내용
- 메서드 기본 형태
- 매개변수의 반환
- 클래스 메서드
- 오버로딩
- 접근 제한자

### 메서드 기본 형태
```
[메서드 기본 형식]

[접근 제한자] [반환형] [메서드 이름] ([매개변수])
{
    [메서드 코드]
}
```
- 두 개의 매개변수를 갖는 메서드
  - 메서드는 매개변수를 여러 개 가질 수 있음
```
public int Multi(int x, int y)
{
    return x * y;
}
```
- 아무것도 반환하지 않는 메서드
  - 메서드는 아무것도 반환하지 않을 수 있음
```
public void Print()
{
    Console.WriteLine("Print() 메서드가 호출 되었습니다.");
}
``` 

#### 예제 6-1 : 인스턴스 메서드 생성과 사용
- Test 클래스에 매개변수로 넣은 숫자를 제곱하는 Power 메서드 생성하기
```
namespace week09wp
{
    internal class Program
    {
        class Test
        {
            public int Power(int x)
            {
                return x * x;
            }
        }
        static void Main(string[] args)
        {
            Test test = new Test();

            Console.WriteLine(test.Power(10));
            Console.WriteLine(test.Power(20));
        }
    }
}

- 결과
100
400
```

### 매개변수와 반환
- 반환 메서드 형태
  - 반환값을 갖는 메서드의 일반적 형태
```
public 자료형 메서드(자료형 매개변수, 자료형 매개변수)
{
    자료형 output = 초기값;

    // output에 값을 계산

    return output;
}
```

#### 예제 6-2 : 매개 변수와 반환(1)
- 매개변수 min부터 max까지 더하는 메서드
```
namespace week09wp
{
    internal class Program
    {
        class Test
        {
            public int Sum(int min, int max)
            {
                int output = 0;
                for (int i = min; i <= max; i++) 
                {
                    output += i;
                }
                return output;
            }
        }
        static void Main(string[] args)
        {
            Test test = new Test();
            Console.WriteLine(test.Sum(1, 100));
        }
    }
}

- 결과
5050
```

#### 예제 6-3 : 매개 변수와 반환(2)
- 매개변수 min부터 max까지 곱하는 메서드
```
namespace week09wp
{
    internal class Program
    {
        class Test
        {
            public int Multiply(int min, int max)
            {
                int output = 1;
                for (int i = min; i <= max; i++)
                {
                    output *= i;
                }
                return output;
            }
        }
        static void Main(string[] args)
        {
            Test test = new Test();
            Console.WriteLine(test.Multiply(1, 10));
        }
    }
}

- 결과
3628800
```

### 클래스 메서드
- Main() 메서드 - 클래스 메서드
  - 기본 콘솔 프로젝트로 생성되는 Program 클래스의 Main() 메서드는 클래스 메서드
```
class Program
{
    static void Main(String[] args)
    {

    }
}
```
- 클래스 메서드 생성 방법
```
[클래스 메서드 기본 형식]

[접근 제한자] static [반환형] [메서드 이름] ([매개변수])
{
     [메서드 코드]
}
```
- (비교)클래스 변수 생성 시, [접근 제한자] static [자료형] [변수명]

- 반환 메서드 형태
  - 클래스 메서드 사용 방법
    - Program 클래스 내부의 Main() 메서드를 직접 사용할 경우, "클래스명." 바로 사용
```
Program.
```

#### 예제 6-4 : 클래스 메서드 생성과 사용
- 클래스 메서드 MyMath.Abs() 생성하고 호출하기
```
namespace week09wp
{
    internal class Program
    {
        class MyMath
        {
            public static int Abs(int input)
            {
                if (input < 0)
                {
                    return -input;
                }
                else
                {
                    return input;
                }
            }
        }
        static void Main(string[] args)
        {
            Console.WriteLine(MyMath.Abs(52));
            Console.WriteLine(MyMath.Abs(-273));
        }
    }
}

- 결과
52
273
```

### 오버로딩
- 오버로딩(Overloading)
  - 이름은 같고, 매개변수는 다른 메서드를 만드는 것

#### 예제 6-5 : 메서드 오버로딩
- Abs() 메서드를 다양한 자료형에서 동작할 수 있도록 오버로딩하기
```
namespace week09wp
{
    internal class Program
    {
        class MyMath
        {
            public static int Abs(int input)
            {
                if (input < 0) { return -input; }
                else { return input; }
            }
            public static double Abs(double input)
            {
                if (input < 0) { return -input; }
                else { return input; }
            }
            public static long Abs(long input)
            {
                if (input < 0) { return -input; }
                else { return input; }
            }
        }
        static void Main(string[] args)
        {
            // int
            Console.WriteLine(MyMath.Abs(52));
            Console.WriteLine(MyMath.Abs(-273));

            // double
            Console.WriteLine(MyMath.Abs(52.273));
            Console.WriteLine(MyMath.Abs(-32.103));

            // long
            Console.WriteLine(MyMath.Abs(21474836470));
            Console.WriteLine(MyMath.Abs(-21474836470));
        }
    }
}

- 결과
52
273
52.273
32.103
21474836470
21474836470
```

### 접근 제한자
- 가장 기본적인 접근 제한자 설정
```
[변수 & 메서드 기본형식]

[접근 제한자] [자료형] [변수 이름]
[접근 제한자] [반환형] [메서드 이름] ([매개변수])
{
    [메서드 코드]
}
```
- 대표적 접근 제한자 : Public, Private

#### private 접근 제한자
- 접근 제한자 생략 시, 자동으로 private 접근 제한자 설정
  - Main() 메서드는 기본적으로 private 메서드
  ```
  static void Main(String[] args)
  {

  }
  ```
- 다른 클래스에서 Program 클래스의 Main() 메서드 호출
  - 외부 클래스에서의 접근
```
class Test
{
    public void TestMethod()
    {
         Program.Main(new string[] {""}); // 오류 발생
    }
}

class Program
{
    static void Main(string[] args)
    {

    }
}
```
  - 접근 제한자로 인한 접근불가 상태이므로 오류 발생
```
publiv void TestMethod()
{
    Program.Main(new string[] {""});
}
```

#### public 접근 제한자
- 다른 클래스에서 Main() 메서드를 호출
  - Public 접근 제한자를 붙인 Main() 메서드
```
class Test
{
    public void TestMethod()
    {
         Program.Main(new string[] {""}); 
    }
}

class Program
{
    public static void Main(string[] args)
    { ↳ 접근 제한자를 추가함

    }
}
```
- public 접근 제한자가 걸린 변수 또는 메서드는 모든 곳에서 접근 가능

#### 궁금했던 질문
- 인스턴스 메서드로 코드를 짠다면 문장이 하나 더 추가가 되는데 애초에 static을 써서 클래스 메서드로 만들면 안되는지
```
[답변]

실제 프로그램에서는 객체마다 다른 데이터를 가지는 경우가 많기 때문이다.
예를 들어 게임 캐릭터는 플레이어마다 hp가 다름. 이렇게 객체별 상태가 필요함.
정리하면 인스턴스 메서드는 객체 필요, 클래스 메서드는 객체 필요 없음.
```
- 클래스를 하나 더 만들어서 그 안에 코드를 짜는 이유가 main함수의 가독성 떄문인지
```
[답변]

지금 배우는 단계에서 : Main 함수가 너무 길어지는 걸 막고, 기능별로 나눠서 보기 쉽게 만들기 위해 클래스를 따로 만드는 경우가 있음
진짜 중요한 이유 : 단순한 길이 떄문이 아닌, 관련된 데이터와 기능을 하나로 묶기 위해서
정리하면 클래스 만드는 이유는:
1. Main함수가 너무 길어지는 걸 방지
2. 코드 가독성 향상
3. 기능별로 분리
4. 관련 데이터와 기능을 묶기 위해
5. 유지보수 쉽게 하기 위해
```

##### ✍️작성자: 박지안
##### 🐧실습 환경: Visual Studio 2022
##### 🗓️ 작업일: 2026-05-08
