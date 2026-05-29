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

  pg11 부터 작성요함
