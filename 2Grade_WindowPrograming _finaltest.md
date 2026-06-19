# 2학년 기말고사 정리

## 접근 제한자
- 
| 접근 제한자 | 접근 가능 범위 |
|------------|----------------|
| public | 어디서든 접근 가능 |
| private | 해당 클래스 내부에서만 접근 가능 |
| protected | 상속받은 자식 클래스에서 접근 가능 |
| internal | 같은 프로젝트 내에서 접근 가능 |
- 시험 포인트
```
class Test
{
  private int num = 10;
}

Test t = new Test();
Console.WriteLine(t.num);
❌ 오류
```
```
class Test()
{
  public int num = 10;
}

Test t = new Test();
Console.WriteLine(t.num);
⭕ 가능
```

## 오버로딩(Overloading)
- 정의 : 같은 이릉의 메서드를 여러 개 만드는 것
- 조건 : 매개변수가 달라야 함
  - 개수 다름
  - 타입 다름
  - 순서 다름
```
[예시]

class Test()
{
  public void Print()
  {
  }

  public void Print(string a)
  {
  }
}
```
- 특징
  - 같은 클래스
  - 메서드 이름 동일
  - 매개변수 달라야 함

## 오버라이딩(Overriding)
- 정의 : 부모 클래스 메서드를 자식 클래스가 재정의
```
[부모]

class Animal
{
  public virtual void Sound()
  {
    Console.WriteLine("동물");
  }
}
```
```
[자식]

class Dog : Animal
{
  public override void Sound()
  {
    Console.WriteLine("멍멍");
  }
}
```
- 특징
  - 부모 : virtual
  - 자식 : override
 
## 하이딩(Hiding)
- 정의 : 부모 메서드를 숨기고 새로 만듦
```
[부모]

class Animal
{
  public void Sound()
  {
    Console.WriteLine("동물");
  }
}
```
```
[자식]

class Dog : Animal
{
  public new void Sound()
  {
    Console.WriteLine("멍멍");
  }
}
```
- 특징
  - 하이딩 = new
  - 오버라이딩 = override
 
## 섀도잉(Shadowing)
- 정의 : 부모 변수와 같은 이름의 변수를 자식이 선언
```
class Parent
{
  public int x = 10;
}

class Child : Parent
{
  public new int x = 20;
}

Child c = new Child();
Console.WriteLine(c.x);

[출력]
20
```

## 상속
```
[문법]

class Parent
{
}

class Child : Parent
{
}
```
- 특징
  - 부모 멤버 사용 가능
  - 코드 재사용
 
## 오버라이딩 제한
```
[불가능]

class Parent
{
  public void Test()
  {
  }
}
```
```
class Child : Parent
{
  public override void Test()
  {
  }
}

❌ 오류
```
- 반드시 virtual 필요
```
class Parent
{
  public virtual void Test()
  {
  }
}
```
```
class Child : Parent
{
  public override void Test()
  {
  }
}

⭕ 가능
```

## 값 복사(Value Copy)
- 대표
```
int
double
char
bool
struct
```
```
int a = 10;
int b = a;
b = 20;

[결과]
a = 10
b = 20
```

## 참조 복사(Reference Copy)
- 대표
```
class
array
string
```
```
Person p1 = new Person();
Person p2 = p1;

p2.age = 20;

[결과]
p1.age = 20
p2.age = 20

같은 객체를 가리킴
```

## 구조체(Struct)
- 특징
  - 값 형식
  - 값 복사
```
struct Point
{
  public int x;
  public int y;
```
```
Point p1;
p1.x = 10;

Point p2 = p1;

p2.x = 20;

[결과]
p1.x = 10
p2.x = 20
```

## 값 전달
```
void Test(int x)
{
  x = 100;
}
```
```
int a = 10;
Test(a)
Console.WriteLine(a);

[출력]
10
```

## 참조 전달
```
void Test(ref int x)
{
  x = 100;
}
```
```
int a = 10;
Test(ref a);
Console.WriteLine(a);

[출력]
100
```
- ref : 참조 전달

## 속성
```
[형태]

private int age;

public int Age
{
  get { return age; }
  set { age = value; }
}
```
```
[자동 구현 속성]

public int Age
{
  get;
  set;
}
```

### 기출 문제
- 1번
```
int a = 10;
int b = a;

b = 20;

Console.WriteLine(a);

[답]
10
```
- 2번
```
class Test
{
  public int x = 10;
}

Test a = new Test();
Test b = a;

b.x = 20;

Console.WriteLine(a.x);

[답]
20
```
- 3번
```
class Parent
{
  public virtual void Show()
  {
    Console.WriteLine("Parent");
  }
}

class Child : Parent
{
  public override void Show()
  {
    Console.WriteLine("Child");
  }
}

[핵심]
virtual + override
```
- 4번
```
class Parent
{
  public void Show()
  {
  }
}

class Child : Parent
{
  public new void Show()
  {
  }
}

[핵심]
하이딩(Hiding) : new
```
