# C# 프로그래밍 - 13주차 정리

## 📚 학습 내용
- 제네릭
- 인덱서
- OUT 키워드
- 구조체

### 제네릭
- 제네릭은 클래스 내부에서 자료형에 별칭(Alias)을 지정하는 기능
  - List<int> list = new List<int>();의 <> 사용 예
  - 제네릭 활용 방법
    - 클래스 선언할 때 클래스명 뒤에 <> 기호 사용하고, <> 기호 내부에 식별자 지정
    ```
    class Wanted<T>
    {

    }
    ```
- 두 개 이상의 제네릭을 사용하는 클래스
  - 일반적으로 제네릭 하나 지정 시 식별자 T 사용하며, 두 개 이상 지정 가능
  ```
  class Test<T, U>
  {

  }
  ```

#### 예제 8-1 : 제네릭 기본
- 제네릭을 이용하여 변수 Value의 자료형을 원하는 자료형으로 지정하기
```
namespace GenericBasic
{
  // T 식별자 지정  
  class Wanted<T>
  {
    public T value;
    public Wanted(T value)
    {
      this.Value = value;
    }
  }

  class Program
  {
    static void Main(string[] args)
    {
      // T 식별자 활용
      Wanted<string> wantedString = new Wanted<string>("String");
      Wanted<int> wantedInt = new Wanted<int>(52273);
      Wanted<double> wantedDouble = new Wanted<double>(52.273);

      Console.WriteLine(wantedString.Value);
      Console.WriteLine(wantedInt.Value);
      Console.WriteLine(wantedDouble.Value);
    }
  }
}

[실행 결과]
String
52273
52.273
```

#### (참고) Where 키워드
- 제네릭의 제한
  - 제네릭에 모든 자료형을 허용하면 안되는 경우가 있는데, 이 경우 Where 키워드를 사용하여 제네릭을 제한
  ```
  class Test<T, U>
    where T : class // T는 클래스여야 함
    where U : struct // U는 구조체여야 함
  {

  }
  ```
  ```
  class Test<T, U>
    where T : ICompareable // T는 IComparable 또는 IComparable의 상속을 받은 것이어야 함
    where U : ICompareable, IDispoable // U는 IComparable과 IDisposable 또는 이러한 것들의 상속을 받은 것이어야 함
  {

  }
  ```

### 인덱서
- 인덱서 선언 예시
```
class Products
{                ↱ products[i]의 자료형은 int임      
  public int this[int i] // 인덱서를 선언
  {
    // Products products = new Product();
    // products[i] 할 때에 호출
    get { return i; }
    // products[i] = 10 할 때에 호출
    set { Console.WriteLine(i + "번째 상품 설정"); }
  }
}
```

#### 예제 8-2 : 인덱서로 배열처럼 사용하는 제곰 클래스
- SquareCalculator 클래스의 인덱서로 int자료형의 정수 넣으면 해당 숫자를 제곱해서 반환
```
namespace IndexerBasic
{
  class SquareCalculator
  {
    // 인덱서 선언
    public int this[int i]
    {
      get
      {
        return i * i;
      }
    }
  }

  class Program
  {
    static void Main(string[] args)
    {
      SqaureCalculator square = new SquareCalculator();
      Console.WriteLine(square[10]);
    }
  }
}

[실행 결과]
100
400
900
```

### OUT 키워드
- C#메서드에서 여러 개의 값을 반환하고자 할 때 사용하는 키워드
  - TryParse() 메서드
    - 값을 여러 개 반환하고자 할 때 사용하는 대표적인 메서드
    - int.TryParse(), float.TryParse()와 같이 기본적인 숫자 자료형에 소속된 클래스 메서드
  - int.TryParse() 메서드의 기본 형태
  ```
  public static bool TryParse (string s, out int result);
  ```
    - out 키워드가 붙은 매개변수 입력할 때
  ```
  int.TryParse("52273", out output);
  ```
- out 키워드는 매개변수로 넣은 변수로 값을 넣어 줌
  - 변수 아닌 일반 자료 넣으면 오류가 발생
  ```
  int.TryParse(Console.ReadLine(), 52273);
                                     ↳ 인수는 'out' 키워드와 함께 전달해야 함
  ```
- out 키워드를 사용하는 메서드 생성
  - Int.TryParse()메서드 선언처럼, 메서드 선언 시 out키워드를 입력하고 메서드 내부에서는 일반 매개변수처럼 사용

#### 예제 8-3 : int.TryParse() 메서드
- Int.TryParse()메서드를 사용하여 사용자에게 입력 받은 문자열을 숫자로 변환하기
```
namespace TryMethod
{
  class Program
  {
    static void Main(string[] args)
    {
      Console.WriteLine("숫자 입력: ");
      int output;
      bool result = int.TryParse(Console.ReadLine(), out output); // Out키워드는 매개변수로 넣은 변수로 값을 반환해 줌

      if (result)
      {
        Console.WriteLine("입력한 숫자: " + output);
      }
      else
      {
        Console.WriteLine("숫자를 입력해주세요!");
      }
    }
  }
}

[실행 결과]
숫자 입력: 52273
입력한 숫자: 52273

숫자입력: ㅇㅂㅇ
숫자를 입력해주세요!
```

#### 예제 8-4 : out 키워드를 사용하는 메서드 생성
- NextPosition()메서드에서의 out키워드 사용
```
namespace MethodWithOut
{
  class Program
  {
    static void NextPosition(int x, int y, int vx, int vy, out int rx, out int ry)
    {
      // 다음 위치 = 현재 위치 + 현재 속도
      rx = x + vx;
      ry = y = vy;
    }

    static void Main(string[] args)
    {
      int x = 0;
      int y = 0;
      int vx = 1;
      int vy = 1;

      Console.WriteLine("현재 좌표: (" + x + "," + y + ")");
      NextPosition(x, y, vx, vy, out x, out y);
      Console.WriteLine("다음 좌표: (" + x + "," + y + ")");
    }
  }
}

[실행 결과]
현재 좌표: (0,0)
다음 좌표: (1,1)
```

### 구조체
- 구조체는 간단한 객체 만들 때 사용하는 형식
  - 클래스와 거의 동일한 구문 사용, 복사 형식이 다르고 클래스보다 제한 많음
  - 구조체는 상속, 인터페이스 구현 불가능, 클래스보다 안정성 높음
  - C#의 기본 자료형은 모두 구조체로 정의
    - Int 자료형은 구조체

#### 구조체 선언
- 구조체를 만드는 기본 방법은 클래스와 동일
  - 멤버 변수로 x와 y를 갖는 구조체 만들기
  ```
  struct Point
  {
    public int x;
    public int y;
  }
  ```
    - 구조체는 new키워드 없이 인스턴스를 생성
    - 단, 이때 멤버변수를 초기화하지 않으면 해당 멤버변수 사용 시 오류 발생
- 구조체의 멤버를 초기화하지 않고 사용하는 경우, 오류 발생

#### 예제 8-5 : new 키워드를 사용하지 않고 구조체 인스턴스 생성
- 구조체 Point 선언하고 사용하기
```
namespace StructBasic
{
  class Program
  {
    // 구조체 Point 선언
    struct Point
    {
      public int x;
      public int y;
    }

    static void Main(string[] args)
    {
      // 구조체 Point 생성
      Point point;
      point.x = 10;
      point.y = 10;
      // 구조체 Point 사용
      Console.WriteLine(point.x);
      Console.WriteLine(point.y);
    }
  }
}

[실행 결과]
10
10
```

#### 구조체의 생성자
- 매개변수 없는 생성자 선언 불가
  - 예시 (오류 발생)
  ```
  struct Point
  {
    public int x;
    public int y;

    public Point()
    {

    }
  }
  ```
- 매개변수 넣어 생성자 만들기
```
struct Point
{
  public int x;
  public int y;

  public Point(int x, int y)
  {
    this.x = x;
    this.y = y;
  }
}
```
  - 매개변수 없는 생성자는 자동 정의되기 때문에 구조체는 매개변수 없는 생성자를 만들 수 없음
  - 위와 같이, 매개변수가 있는 생성자를 만들어도 매개변수 없는 생성자 사용 가능
- 매개변수 없는 생성자
```
Point point = new Point();
```
  - 내부 변수의 초기화
    - 내부 변수는 자동적으로 해당 자료형의 기본 값으로 초기화
    - (예시) 숫자 관련 자료형은 0으로, 문자열 또는 객체는 null로 초기화됨
- 구조체는 생성자에서 모든 멤버 변수를 초기화된 상태로 만들어야 함
- 그리고 선언과 동시에 멤버 변수를 초기화 할 수 없음
```
struct Point
{
  public int x;
  public int y;
  public string testA; // 초기화되지 않은 멤버 변수이므로 생성자를 만든다면, 생성자에서 반드시 초기화해줘야 함
  public string testB = "init"; // 선언과 동시에 초기화할 수 없음, 오류 발생

  public Point(int x, int y) // 멤버 변수 testA를 초기화하지 않았으므로, 오류 발생
  {
    this.x = x;
    this.y = y;
  }
}
```

#### 예제 8-6 : 구조체의 생성자
- 매개변수없는 생성자로 구조체 인스턴스를 생성하고 멤버변수 출력하기
```
namespace ConstructorOfstruct
{
  class Program
  {
    struct Point
    {
      public int x;
      public int y;

      public Point(int x, int y)
      {
        this.x = x;
        this.y = y;
      }
    }
    static void Main(string[] args)
    {
      Point point = new Point(); // 매개변수 없는 생성자로 구조체 인스턴스 생성값이 주어지지 않았으므로 0으로 초기화

      Console.WriteLine(point.x);
      Console.WriteLine(point.y);
    }
  }
}

[실행 결과]
0
0
```

#### (참고) 구조체에서 클래스 인스턴스를 멤버 변수로 선언할 때
- 구조체에서 클래스 인스턴스를 멤버 변수로 선언
  - 이때도 마찬가지로 무조건 초기화해야 함
```
struct Point
{
  public int x;
  public int y;
  public Program program;

  public Point(int x, int y)
  {
    this.x = x;
    this.y = y;
    this.program = null; // null로 초기화
  }
}
```

#### 예제 8-7 : 구조체의 값 복사
- 생성된 구조체의 값 복사 결과 예측하고, 확인하기
```
namespace StructCopy
{
  class Program
  {
    public int x;
    public int y;

    public PointClass(int x, int y)
    {
      this.x = x;
      this.y = y;
    }
  }

  struct PointStruct
  {
    public int x;
    public int y;

    public PointStruct(int x, int y)
    {
      this.x = x;
      this.y = y;
    }
  }

  static void Main(string[] args)
  {
    // 클래스
    PointClass pointClassA = new PointClass(10, 20);
    PointClass pointClassB = new pointClassA; // 침조 복사가 수행
    pointClassB.x = 100;
    pointClassB.y = 200;

    Console.WriteLine("pointClassA: " + pointClassA.x + "," + pointClassA.y);
    Console.WriteLine("pointClassB: " + pointClassB.x + "," + pointClassB.y);
    Console.WriteLine();

    // 구조체
    PointStruct pointStructA = new PointStruct(10, 20);
    PointStruct pointStructB = pointStructA; // 값 복사 수행
    pointStructB.x = 100;
    pointStructB.y = 200;

    Console.WriteLine("pointStructA: " + pointStructA.x + "," + pointStructA.y);
    Console.WriteLine("pointStructB: " + pointStructB.x + "," + pointStructB.y);
  }
}

[실행 결과]
pointClassA: 100,200
pointClassB: 100,200

pointStructA: 10,20
pointStructB: 100,200
```

##### ✍️작성자: 박지안
##### 🐧실습 환경: Visual Studio 2022
##### 🗓️ 작업일: 2026-06-18
