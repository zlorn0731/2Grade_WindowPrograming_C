# C# 프로그래밍 - 12주차 정리

## 📚 학습 내용
- 상속의 생성자
- 섀도잉과 하이딩
- 하이딩과 오버라이딩
- 상속과 오버라이딩 제한

### 상속의 생성자
- 생성자
  - 인스턴스 초기화할 때 사용
  - 자식 인스턴스를 생성하면, 부모의 멤버 초기화 위해 부모 생성자도 자동으로 호출
- 상속 시 기본적인 생성자 호출 순서
  - 부모생성자 먼저 호출 후
  - 그 다음 자식 생성자 호출
```
class Program
{
  class Parent
  {
    public Parent() // 부모 생성자
    {
      Console.WriteLine("부모 생성자");
    }
  }

  class Child : Parent
  {
    public Child() // 자식 생성자
    {
      Console.WriteLine("자식 생성자");
    }
  }

  static void Main(string[] args)
  {
    Child child = new Child(); // 자식 인스턴스를 생성
  }
}

[실행 결과]
부모 생성자
자식 생성자
```
- 부모 생성자 호출을 명시적으로 지정할 때
  - base 키워드를 사용한 생성자 지정
    - 생성자 메소드 뒤에 클론 입력하고 base() 입력
```
class Program
{
  class Parent
  {
    public Parent() { Console.WriteLine("부모 생성자"); }
  }

  class Child : Parent
  {
    public Child() : base() // base 키워드 사용
    {
      Console.WriteLine("자식 생성자");
    }
  }

  static void Main(string[] args)
  {
    Child child = new Chihld();
  }
}
```
- 매개변수가 있는 메서드를 호출하고 싶을 때
  - base 키워드를 사용한 생성자 지정
```
class Program
{
  class Parent
  {
    public Parent() { Console.WriteLine("Parent()"); }
    public Parent(int param) { Console.WriteLine("Parent(int param)"); }
    public Parent(string param) { Console.WriteLine("Parent(string param)"); }
  }

  class Child : Parent
  {
    public Child() : base(10) // Parent(int param) 부모 생성자를 호출
    {
      Console.WriteLine("Child() : base(10)");
    }

    public Child(string input) : base(input) // Parent(string param) 부모 생성자 호출
    {
      Console.WriteLine("Child(string input) : base(input)");
    }
  }

  static void Main(string[] args)
  {
    Child childA = new Child();
    Child childB = new Child("string");
  }
}
```

### (참고) 클래스 변수 상속
- 클래스 변수는 상속되어도 공유
  - 클래스 변수 상속
```
class Program
{
  class Parent
  {
    public static int counter = 0; // 클래스 변수 counter를 선언

    public void CountParent()
    {
      Parent.counter++; // Parent 클래스의 counter 변수를 증가시킴
    }
  }

  class Child : Parent
  {
    public void CountChild()
    {
      Child.counter++; // Child 클래스의 counter 변수를 증가시킴
    }
  }

  static void Main(string[] args)
  {
    Parent parent = new Parent();
    Child child = new Child();

    Parent.CountParent();
    child.CountChild();

    Console.WriteLine(Parent.counter);
    Console.WriteLine(Child.counter);
  }
}

[실행 결과]
2
2
```

### 섀도잉과 하이딩 중 섀도잉(Shadowing)
- 섀도잉은 특정한 영역에서 이름이 겹쳐 다른 변수를 가리는 것
```
class Program
{
  public static int number = 10;

  static void Main(string[] args)
  {
    int number = 20;
    Console.WriteLine(number);
  }
}

[실행 결과]
20
```

### 섀도잉과 하이딩 중 하이딩(Hiding)
- 하이딩은 부모 클래스와 자식 클래스에 동일 이름으로 멤버 만들 때 발생
```
class Program
{
  class Parent
  {
    public int variable = 273;
  }

  class Child : Parent
  {
    public string variable = "shadowing";
  }

  static void Main(string[] args)
  {
    Child child = new Child();
    Console.WriteLine(Child.variable);
  }
}

[실행 결과]
shadowing
```
- 부모에 있는 int 자료형의 변수 사용할 때
  - 부모로 자료형을 변환하고 사용
```
static void Main(string[] args)
{
  Child child = new Child();
  Console.WriteLine((Parent)child).variable);
}
```
- 메서드 하이딩
```
class Program
{
  class Parent
  {
    public void Method()
    {
      Console.WriteLine("부모의 메서드:);
    }
  }

  class Child : Parent
  {
    public void Method()
    {
      Console.WriteLine("자식의 메서드");
    }
  }

  static void Main(string[] args)
  {
    Child child = new Child();
    child.Method();
    ((Parent)child).Method();
  }
}
```
- 실행은 정상적이나 개발 환경에 경고 메시지 뜸
- 메서드는 변수와 다르게 충돌이 발생할 때 하이딩할지 오버라이딩할지 결정 가능
```
public new void Method()
{
  Console.WriteLine("자식의 메서드");
}

// new : 하이딩
```
```
public override void Method()
{
  Console.WriteLine("자식의 메서드");
}

// override : 오버라이딩
```

### 하이딩과 오버라이딩
- 오버라이딩(Overriding)
  - 오버라이딩은 부모 클래스의 메서드를 자식 클래스에서 재구현
    - 하이딩의 형태로 메서드 작성 후 앞에 virtual이라는 키워드 붙임
    - 하이딩은 멤버 전체(변수, 메서드 등)에서 발생
    - 오버라이딩은 메서드 관련만 발생

#### new 메서드
- 하이딩한다는 표시를 위해 메서드 이름 앞에 new 키워드 붙임
```
class Program
{
  class Parent
  {
    public int variable = 273;
    public void Method()
    {
      Console.WriteLine("부모의 메서드");
    }
  }

  class Child : Parent
  {
    public new string variable = "hiding"; // new 키워드를 사용해 변수를 하이딩하겠다고 선언
    public new void Method() // new 키워드를 사용해 하이딩하겠다고 선언
    {
      Console.WriteLine("자식의 메서드");
    }
  }

  static void Main(string[] args)
  {
    Child child = new Child();
    child.Method();
    ((Parent)child).Method();
  }
}
```

#### virtual과 override 메서드
- virtual과 override 메서드를 사용한 오버라이딩
```
class Program
{
  class Parent
  {
    public virtual void Method() // 부모의 메서드에 virtual 키워드를 적용
    {
      Console.WriteLine("부모의 메서드");
    }
  }

  class Child : Parent
  {
    public override void Method() // 자식의 메서드에 override 키워드를 적용
    {
      Console.WriteLine("자식의 메서드");
    }
  }

  static void Main(string[] args)
  {
    Child child = new Child();
    child.Method();
    ((Parent)child).Method);
  }
}

[실행 결과]
자식의 메서드
자식의 메서드
````

### 하이딩 활용
```
class Program
{
  class Animal
  {
    public void Eat()---------------------------------------→ 같은 이름을 재사용
    {                                                       |
      Console.WriteLine("냠냠 먹습니다.");                   |
    }                                                       |
  }                                                         |
                                                            |
  class Dog : Animal                                        |
  {                                                         |
    public void Eat()---------------------------------------|
    {                                                       |
      Console.WriteLine("강아지 사료를 먹습니다.");           |
    }                                                       |
  }                                                         |
                                                            |
  class Cat : Animal                                        |
  {                                                         |
    public void Eat()---------------------------------------|
    {
      Console.WriteLine("고양이 사료를 먹습니다.");
    }
  }

  static void Main(string[] args)
  {
    List<Animal> Animals = new List<Animal>()
    {
      new Dog(), new Cat(), new Cat(), new Dog(), new Dog(), new Cat(), new Dog(), new Dog()
    };

    foreach (var item in Animals)
    {
      item.Eat(); // Eat 메소드를 호출
    }
  }
}

[실행 결과]
냠냠 먹습니다.
냠냠 먹습니다.
냠냠 먹습니다.
냠냠 먹습니다.
냠냠 먹습니다.
냠냠 먹습니다.
냠냠 먹습니다.
냠냠 먹습니다.
```

### 오버라이딩 활용
```
class Animal
{
  public virtual void Eat()
  {
    Console.WriteLine("냠냠 먹습니다.");
  }
}

class Dog : Animal
{
  public override void Eat()
  {
    Console.WriteLine("강아지 사료를 먹습니다.");
  }
}

class Cat : Animal
{
  public override void Eat()
  {
    Console.WriteLine("고양이 사료를 먹습니다.");
  }
}

[실행 결과]
강아지 사료를 먹습니다.
고양이 사료를 먹습니다.
강아지 사료를 먹습니다.
고양이 사료를 먹습니다.
강아지 사료를 먹습니다.
고양이 사료를 먹습니다.
강아지 사료를 먹습니다.
고양이 사료를 먹습니다.
```

### new 키워드를 사용하는 하이딩 활용
```
class Animal
{
  public virtual void Eat()
  {
    Console.WriteLine("냠냠 먹습니다.");
  }
}

class Dog: Animal
{
  public new void Eat()
  {
    Console.WriteLine("강아지 사료를 먹습니다.");
  }
}

class Cat : Animal
{
  public override void Eat()
  {
    Console.WriteLine("고양이 사료를 먹습니다.");
  }
}

[실행 결과]
냠냠 먹습니다.
고양이 사료를 먹습니다.
고양이 사료를 먹습니다.
냠냠 먹습니다.
냠냠 먹습니다.
고양이 사료를 먹습니다.
냠냠 먹습니다.
냠냠 먹습니다.
```

### 상속과 오버라이딩 제한
- sealed 메소드
  - 클래스 적용(상속 제한), 메소드 적용(오버라이딩 제한)에 사용
    - 상속 제한 오류의 예시(sealed 클래스 오류)
```
class Program
{
  sealed class Parent // sealed 클래스 선언
  {
    public void Test() { }
  }

  class Child : Parent // 여기서 오류 발생
  {
    public void Test() { }
  }

  static void Main(string[] args)
  {
    Parent parent = new Parent();
    Child child = new Child();

    parent.Test();
    child.Test();
  }
}
```
```
class Parent
{
  public virtual void Test() { }
}

class Child : Parent
{
  sealed public override void Test() { } // sealed 메소드로 변경
}

class GrandChild : Child
{
  public override void Test() { } // 여기서 오류 발생
}
```
- abstract 키워드
  - 무조건 상속, 또는 메소드 반드시 오버라이딩 할 때 사용
    - 상속 제한 오류의 예시(abstract 클래스 오류)
```
class Program
{
  abstract class Parent // abstract 클래스로 선언
  {
    public void Test() { }
  }

  class Child : Parent
  {
    public void Test() { }
  }

  static void Main(string[] args)
  {
    Parent parent = new Parent(); // 여기서 오류 발생
    Child child = new Child();

    parent.Test();
    child.Test();
  }
}
```
```
abstract class Parent //abstract 메소드를 선언하려면 반드시 abstract 클래스가 되어야 함
{
  public abstract void Test(); // abstract 메소드로 선언
}

class Child : Parent // 여기에서 오류 발생
{

}
```
- abstract 메소드와 관련된 오류 해결
```
abstract class Parent
{
  public abstract void Test();
}

class Child : Parent
{
  public override void Test() { } // override 키워드를 사용해 오버라이딩해야 함
}
```

### 실습 7-4 
- 상속 시 생성자 호출 순서 & base 키워드를 사용한 생성자
```
namespace ConstructorSequences
{
  namespace A
  {
    class Parent
    {
      public Parent()
      {
        Console.WriteLine("부모 생성자");
      }
    }

    class Child : Parent
    {
      public Child()
      {
        Console.WriteLine("자식 생성자");
      }
    }
  }

  namespace B
  {
    class Parent
    {
      public Parent() { Console.WriteLine("부모 생성자"); }
    }

    class Child : Parent
    {
      public Child() : base()
      {
        Console.WriteLine("자식 생성자");
      }
    }
  }

  namespace C
  {
    class Parent
    {
      public Parent() { Console.WriteLine("Parent()"); }
      public Parent(int param) { Console.WriteLine("Parent(int param)"); }
      public Parent(string param) { Console.WriteLine("Parent(string param)"); }
    }

    class Child : Parent
    {
      public Child() : base(10)
      {
        Console.WriteLine("Child() : base(10)");
      }
      public Child(string input) : base(input)
      {
        Console.WriteLine("Child(string input) : base(input)");
      }
    }
  }

  class Program
  {
    static void Main(string[] args)
    {
      A.Child childA = new A.Child();
      Console.WriteLine();

      B.Child childB = new B.Child();
      Console.WriteLine();

      C.Child childc = new C.Child();
      C.Child childd = new C.Child("string");
    }
  }
}
```

### 실습 7-5
- 섀도잉, 변수 & 메소드 하이딩
```
namespace ShadowAndHide
{
  class Program
  {
    public static int number = 10;

    class Parent
    {
      public int variable = 273;
      public void Method()
      {
        Console.WriteLine("부모의 메서드");
      }
    }
    class Child : Parent
    {
      public string variable = "shadowing";

      public void Method()
      {
        Console.WriteLine("자식의 메서드");
      }
  }

  static void Maint(string[] args)
  {
    int number = 20;
    Console.WriteLine(number);
    Console.WriteLine();

    Child childA = new Child();
    Console.WriteLine(childA.variable);

    Child childB = new Child();
    Console.WriteLine(((Parent)childB).variable);

    Child childC = new Child();
    childC.Method();
    ((Parent)childC).Method();
  }
 }
}
```

### 실습 7-6
- 하이딩
```
namespace UsageOfHidding
{
  class Program
  {
    class Animal
    {
      public void Eat()
      {
        Console.WriteLine("냠냠 먹습니다.");
      }
    }
    class Dog : Animal
    {
      public void Eat()
      {
        Console.WriteLine("강아지 사료를 먹습니다.");
      }
    }
    class Cat : Animal
    {
      public void Eat()
      {
        Console.WriteLine("고양이 사료를 먹습니다.");
      }
    }

    static void Main(string[] args)
    {
      List<Animal> Animals = new List<Animal>()
      {
        new Dog(), new Cat(), new Cat(), new Dog(), new Dog(), new Cat(), new Dog(), new Dog()
      };

      foreach (var item in Animals)
      {
        item.Eat();
      }
    }
  }
}
```

### 실습 7-7
- 오버라이딩
```
namespace UsageOfOverriding
{
  class Program
  {
    class Animal
    {
      public virtual void Eat()
      {
        Console.WriteLine("냠냠 먹습니다.");
      }
    }
    class Dog : Animal
    {
      public override void Eat()
      {
        Console.WriteLine("강아지 사료를 먹습니다.");
      }
    }
    class Cat : Animal
    {
      public override void Eat()
      {
        Console.WriteLine("고양이 사료를 먹습니다.");
      }
    }

    static void Main(string[] args)
    {
      List<Animal> Animals = new List<Animal>()
      {
        new Dog(), new Cat(), new Cat(), new Dog(), new Dog(), new Cat(), new Dog(), new Dog()
      };

      foreach (var item in Animals)
      {
        item.Eat();
      }
    }
  }
}
```

### 실습 7-8
- abstract 클래스 오류 및 abstract 메서드
```
namespace Abstract
{
  namespace A
  {
    abstract class Parent
    {
      public void Test() { }
    }

    class Child : Parent
    {
      public void Test() { }
    }
  }

  namespace B
  {
    abstract class Parent
    {
      public abstract void Test();
    }

    class Child : Parent
    {
      // abstract 메서드와 관련된 오류 해결
      // public override void Test() { }
    }
  }

  class Program
  {
    static void Main(string[] args)
    {
      A.Parent parent = new A.Parent();
      A.Child child = new A.Child();

      parent.Test();
      child.Test();
    }
  }
}
```

##### ✍️작성자: 박지안
##### 🐧실습 환경: Visual Studio 2022
##### 🗓️ 작업일: 2026-06-17
