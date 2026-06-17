# C# 프로그래밍 - 11주차 정리

## 📚 학습 내용
- 상속과 다형성 소개
- 상속
- 다형성
- is 키워드
- 클래스 자료형 변환

### 상속과 다형성 소개
- 상속과 다형성은 C#에서 반복을 줄이기 위해 사용하는 방법
  - 강아지와 고양이를 나타내는 클래스 만들기
    - Dog 클래스
    ```
            class Dog
        {
            // 속성 Age, Color
            public int Age { get; set; }
            public string Color { get; set; }

            // 생성자
            public Dog() { this.Age = 0; }

            // 메서드 Eat(), Sleep(), Bark()
            public void Eat() { Console.WriteLine("냠냠 먹습니다."); }
            public void Sleep() { Console.WriteLine("쿨쿨 잠을 잡니다."); }
            public void Bark() { Console.WriteLine("왈왈 짓습니다."); }
        }
    ```
    - Cat 클래스
    ```
            class Cat
        {
            // 속성 Age
            public int Age { get; set; }

            // 생성자
            public Cat() { this.Age = 0; }

            // 메서드 Eat(), Sleep(), Meow()
            public void Eat() { Console.WriteLine("냠냠 먹습니다."); }
            public void Sleep() { Console.WriteLine("쿨쿨 잠을 잡니다."); }
            public void Meow() { Console.WriteLine("냥냥 웁니다."); }
        }
    ```
    - Dog과 Cat 클래스의 인스턴스를 만들고 메서드 호출하기
    ```
        static void Main(string[] args)
        {
            // Dog, Cat 인스턴스 생성
            List<Dog> Dogs = new List<Dog>() { new Dog(), new Dog(), new Dog() };
            List<Cat> Cats = new List<Cat>() { new Cat(), new Cat(), new Cat() };

            // Dog들의 메서드 실행
            foreach (var item in Dogs)
            {
                item.Eat();
                item.Sleep();
                item.Bark();
            }

            // Cat들의 메서드 실행
            foreach (var item in Cats)
            {
                item.Eat();
                item.Sleep();
                item.Meow();
            }
        }
    ```

### 상속
- 상속은 클래스 사이에 부모 자식 관계를 정의하는 작업
  - 부모 클래스 하나의 자식을 여러 개 가질 수 있음
  - 부모 자신이 가진 것을 자식에게 물려주게 됨
  - 현재 Dog 클래스와 Cat 클래스 구성(분할되어 있는 클래스)
  - 부모 클래스(Animal)를 만드는 코드 구성(상속을 사용한 구성)

- (1) 우선, 부모클래스는 일반클래스처럼 정의
  - 부모클래스 Animal 코드 작성
  ```
  class Animal
  {
      public int Age { get; set; } // 속성 Age

      public Animal() { this.Age = 0; } // 생성자 Animal()

      public void Eat() { Console.WriteLine("냠냠 먹습니다."); } // 메서드 Eat()
      public void Sleep() { Console.WriteLine("쿨쿨 잠을 잡니다."); } // 메서드 Sleep()
  }
  ```
- (2) 부모로부터 상속받는 자식클래스 정의
  - Animal클래스의 상속을 받는 Dog과 Cat 클래스
  ```
  class Dog : Animal // Animal 클래스의 상속을 받습니다.
  {
    publi string Color { get; set; }

    public void Bark() { Console.WriteLine("왈왈 짓습니다."); }
  }

  class Cat : Animal // Animal 클래스의 상속을 받습니다.
  {
    public void Meow() { Console.WriteLine("냥냥 웁니다."); }
  }
  ```
- 클래스의 부모 자식 관계가 형성되면 자식 클래스는 부모 클래스의 public 또는 protected 멤버에 접근 가능
  - 부모의 모든 멤버 public이므로 Dog 클래스의 인스턴스를 만들면 해당 인스턴스에서 자신의 멤버는 물론 부모의 멤버에 모두 접근 가능
  - Dog 클래스에서 접근할 수 있는 멤버 목록
  ```
  Dog dog = new Doy();
  dog.~
  ```

#### (참고) 다른 접근 제한자
- C#의 접근 제한자
  - 기본적인 접근 제한자는 private, public protected (교재에서 다루는 범위)
  - 그 외에 internal, protected internal
- 
| 접근 제한자 | 내부 클래스 | 외부 클래스 | 파생 클래스 | 프로젝트 |
|------------|-------------|-----------|------------|----------|
| public | O | O | O | O |
| internal | O | O | O | |
| protected | O | | O | |
| private | O | | | |
| protected internal | O | 사용하는 클래스가 같은 어셈블리 안에 있을 때 접근 가능 | O | |

#### (참고) base 키워드
- 자식 클래스에서 부모 클래스에 정의한 멤버의 사용
  - 부모로부터 상속받은 메서드 호출
  ```
  class Animal
  {
    public void Eat() { Console.WriteLine("냠냠 먹습니다."); }
    public void Sleep() { Console.WriteLine("쿨쿨 잠을 잡니다."); }
  }

  class Dog : Animal
  {
    public void Test()
    {
      // 부모에게서 상속받은 Eat()메서드와 Sleep()메서드를 호출
      Eat();
      Sleep();
    }
  }
  ```
- (이름이 겹치는 등) 특수한 이유로 부모의 메서드에 접근 불가할 경우 this 키워드와 같은 형태로 base 키워드 사용
  - 부모를 나타내는 base 키워드 사용 cf.this는 자신을 나타내는 키워드였음
```
class Dog : Animal
{
  public string Color { get; set; }

  public void Bark()
  {
    base.~
  }
}
```

#### (참고) protected 접근 제한자
- private과 비슷하지만 상속한 클래스(파생 클래스)에서는 접근 가능
  - 세 가지 접근 제한자(계속)
```
class Program
{
  class Animal
  {
    private void Private() { }
    protected void Protected() { }
    public void Public() { }

    public void TestA() // Animal 클래스 내부
    {
      // 자신의 클래스 내부에서는 모든 멤버를 사용할 수 있음
      Private();
      Protected();
      Public();
    }
}
```
```
  class Dog : Animal
  {
    public void TestB() // Animal 클래스의 파생클래스(자식 클래스)
    {
      // 상속받은 클래스에서는 private 접근 제한자가 붙은 멤버를 사용할 수 있음
      Protected();
      Public();
    }
  }

  static void Main(String[] args)
  { // Animal 클래스의 외부클래스(Program)
    Dog dog = new Dog();
    dog.Public(); // 이외의 모든 장소에서는 public 접근 제한자가 붙은 멤버만 사용할 수 있음
  }
}
```

### 다형성
- Main()메서드의 코드 중복 문제
```
static void Main(string[] args)
{
  List<Dog> Dogs = new List<Dog>() { new Dog(), new Dog(), new Dog() };
  List<Cat> Cats = new List<Cat>() { new Cat(), new Cat(), new Cat() };
  // 비슷한 코드 중복

  foreach (vat item in Dogs)
  {
    item.Eat();
    item.Sleep();
    item.Bark();
  }
  // 비슷한 코드 중복
  foreach (var item in Cats)
  {
    item.Eat();
    item.Sleep();
    item.Meow();
  }
}
```

- 다형성은 하나의 클래스가 여러 형태로 변환될 수 있는 성질
  - 자식 클래스가 부모 클래스로 위장하는 것으로 생각할 것
    - (예시) 자료형 Animal로 dog생성
      - 변수 dog는 외관상으로 자료형 Animal이지만 실제 내부에는 Dog이 들어있음
      - 외관상으로는 Animal 객체이므로 사용할 수 있는 멤버는 Animal 클래스 멤버 뿐임
      - 부모로 위장한 자식은 부모의 멤버만 사용 가능
      ```
      Animal dog = new Dog();
      Animal cat = new Cat();
      ```

- 다형성을 사용한 코드 중복 해결
```
static void Main(string[] args)
{
  List<Animal> Animals = new List<Animal>(); // 하나의 리스트를 사용 
  {
    new Dog(), new Cat(), new Dog(),
    new Dog(), new Cat(), new Dog()
  };

  //  하나의 반복문을 사용
  foreach (var item in Animals)
  {
    item.Eat();
    item.Sleep();
  }
}
```

- 부모로 위장한 자식은 부모 멤버만 사용할 수 있음
- 따라서, 자식 클래스에 있는 메서드를 사용 위해, 자식 클래스로 자료형 변환이 필요
  - 위장을 해제하고 자신의 멤버를 사용

- 무작정 Cat 클래스로 변환해서 사용
  - 무작정 변환해서 메서드 호출
  ```
  foreach (var item in Animals)
  {
    item.Eat();
    item.Sleep();
    ((Cat)item).Meow);
  }
  ```
  - 내부에 조건문을 넣고 Dog클래스는 Dog클래스로 변환하여 Bark() 메서드 호출하고, Cat클래스는 Cat클래스로 변환하여 Meow() 메서드를 호출해야 함
 
### 상속
- (참고) 최상위 객체
  - C#에서 만드는 모든 객체는 Object라는 객체의 상속을 받게 됨
    - Object 객체의 선언
      - 아래 메서드 중 public 접근 제한자가 붙은 메서드들은 C#에서 만드는 모든 객체에 상속됨
      ```
      class Object
      {
        public Object();

        public virtual bool Equals(object obj);
        pulic static bool Equals(object objA, object objB);
        public virtual int GetHasCode();
        public Type GetType();
        protected object MemberwiseClone();
        public static bool ReferenceEquals(object objA, object objB);
        public virtual string ToString();
      }
      ```
      
- 상속 관계
  - 최상위 Object 클래스
```
         [Object]
          class
            ↑
         [Animal]
          class
         - Properties
           Age
         - Methods
           Animal
           Eat
           Sleep 
            ↑
   ↑--------→←---------↑
 [Dog]               [Cat]
 class               class
 → Animal            → Animal
- Properties        - Methods 
  Color               Meow 
- Methods
  Bark
```

- 상속 관계
  - Object 객체의 다형성 예제(1)
  ```
  List<Object> listOfObject = new List<Object>();
  listOfObject.Add(new Dog());
  listOfObject.Add(new Cat());
  ```
  - Object 객체의 다형성 예제(2)
  ```
  List<Object> listOfObject = new List<Object>();
  listOfObject.Add(new Dog());
  listOfObject.Add(new Cat());
  listOfObject.Add(52);
  listOfObject.Add(52l);
  listOfObject.Add(52.273f);
  listOfObject.Add(52.273);
  ```

### is 키워드
- is키워드는 특정 객체가 어떤 클래스인지 확인하는데 사용
  - is키워드 형태
    - 이 객체가 특정 클래스의 객체라면 true 반환
    ```
    [객체 is 클래스]

    static void Main(string[] args)
    {
      List<Animal>Animals = new List<Animal>() { /* 생략 */ }

      foreach (var item in Animals)
      {
        item.Eat();
        item.Sleep();

        if (item is Dog) { } // 만약 변수 item이 Dog 객체라면
        if (item is Cat) { } // 만약 변수 item이 Cat 객체라면
      }
    }
    ```

- Dog 클래스의 상속 관계
```
item is Dog
item is Animal
item is Object
```
```
    [Object]
     class
      ↑
   [Animal]
    class
   - Properties
     Age
   - Methods
     Animal
     Eat
     Sleep 
      ↑
    [Dog]               
    class               
    → Animal            
   - Properties        
     Color              
   - Methods
     Bark
```

### 클래스와 자료형 변환
- 일반적인 자료형 변환
  - (1) 일반적인 자료형 변환의 형태
  ```
  (클래스) 변수
  ```
    - (예시)
      - is 키워드를 사용한 부분에 다음과 같은 자료형 변환과 메서드 호출부분 추가
      - 자료형을 확인하고 변환하므로 예외가 발생하지 않음
      ```
      foreach (var item in Animals)
      {
        item.Eat();
        item.Sleep();

        if (item is Dog) { ((Dog)item).Bark(); }
        if (item is Cat) { ((Cat)item).Meow(); }
      ```

- as 키워드로 자료형 변환
  - (2) as 키워드로 자료형 변환의 형태
  ```
  변수 as 클래스
  ```
    - (예시)
      - as 키워드를 사용하면 자료형 변환에 실패해도 예외가 발생하지 않음
      - 단지 null(아무것도 아닌 값)을 넣게 됨
      - 오른쪽 as 키워드를 사용하는 일반적인 형태의 코드임
      ```
      foreach (var item in Animals)
      {
        item.Eat();
        item.Sleep();

        var dog = item as Dog;
        if (dog != null) { dog.Bark(); }

        var cat = item as Cat;
        if (cat != null) { cat.Meow(); }
      }
      ```

### 실습 7-1
- 부모에게서 상속 받은 메서드 호출
```
namespace BInheritance
{
  class Animal
  {
    public int Age { get; set; }

    public Animal() { this.Age = 0; }

    public void Eat() { Console.WriteLine("냠냠 먹습니다."); }
    public void Sleep() { Console.WriteLine("쿨쿨 잠을 잡니다."); }
  }

  class Dog : Animal
  {
    public string Color { get; set; }
    public void Bark() { Console.WriteLine("왈왈 짓습니다."); }

    public void Test()
    {
      Eat();
      Sleep();
    }
  }

  class Cat : Animal
  {
    public void Meow() { Console.WriteLine("냥냥 웁니다."); }
  }

  class Program
  {
    static void Main(string[] args)
    {
    }
  }
}
```

### 실습 7-2
- 다형성을 사용한 코드 중복 해결
```
namespace CInheritance
{
  class Animal
  {
    public int Age { get; set; }

    public Animal() { this.Age = 0; }

    public void Eat() { Console.WriteLine("냠냠 먹습니다."); }
    public void Sleep() { Console.WriteLine("쿨쿨 잠을 잡니다."); }
  }

  class Dog : Animal
  {
    public string Color { get; set; }
    public void Bark() { Console.WriteLine("왈알 짓습니다."); }
  }

  class Cat : Animal
  {
    public void Meow() { Console.WriteLine("냥냥 웁니다."); }
  }

  class Program
  {
    static void Main(string[] args)
    {
      List<Animal> Animals = new List<Animal>()
      {
        new Dog(), new Cat(), new Cat(), new Dog(), new Dog(), new Cat(), new Dog(), new Dog()
      };
      foreach (var item in Animals)
      {
        item.Eat();
        item.Sleep();
      }

      List<Object> listOfobjectA = new List<object>();
      listOfobjectA.Add(new Dog());
      listOfobjectA.add(new Cat());
    }
  }
}
```

### 실습 7-3
- is 키워드 & as 키워드 사용
```
namespace DInheritance
{
  class Animal
  {
    public int Age { get; set; }

    public Animal() { this.Age = 0; }

    public void Eat() { Console.WriteLine("냠냠 먹습니다."); }
    public void Sleep() { Console.WriteLine("쿨쿨 잠을 잡니다."); }
  }

  class Dog : Animal
  {
    public string Color { get; set; }
    public void Bark() { Console.WriteLine("왈왈 짓습니다."); }
  }

  class Cat : Animal
  {
    public void Meow() { Console.WriteLine("냥냥 웁니다."); }
  }

  class Program
  {
    static void Main(string[] args)
    {
      List<Animal> Animals = new List<Animal>()
      {
        new Dog(), new Cat(), new Cat(), new Dog(), new Dog(), new Cat(), new Dog(), new Dog()
      };

      foreach (var item in Animals)
      {
        if (item is Dog) { ((Dog)item).Bark(); }
        if (item is Cat) { ((Cat)item).Meow(); }

        var dog = item as Dog;
        if (dog != null) { dog.Bark(); }

        var cat = item as Cat;
        if (cat != null) { cat.Meow(); }
      }
  }
}
```

##### ✍️작성자: 박지안
##### 🐧실습 환경: Visual Studio 2022
##### 🗓️ 작업일: 2026-06-17
