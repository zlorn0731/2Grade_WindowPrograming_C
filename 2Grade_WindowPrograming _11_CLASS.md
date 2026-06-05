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
pg18부터 다형성 부분부터 작성
