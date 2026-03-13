# C# 프로그래밍 첫걸음 - 2주차 정리

## 📚 학습 내용
- C# 언어 소개
- 플랫폼(Platform)
- .NET 플랫폼
- 라이브러리와 프레임워크
- Visual Studio 개발 환경
- C# 콘솔 프로그램 실행
- Console 출력 메서드

---

# 1. C#이란?

C#은 Microsoft에서 개발한 **객체 지향 프로그래밍 언어(Object-Oriented Programming Language)** 이다.

## 특징

### 1️⃣ 형식 안정적(Type Safe)
자료형을 엄격하게 검사하여 프로그램 오류를 줄여준다.

예시

```csharp
int number = 10;
string text = "Hello";

잘못된 자료형을 사용하면 컴파일 오류가 발생한다.

2️⃣ 객체 지향 언어(Object-Oriented)

프로그램을 객체(Object) 단위로 구성하여 개발한다.

예시

사람

자동차

게임 캐릭터

각각의 객체가 속성과 기능을 가진다.

2. 플랫폼 (Platform)

플랫폼은 프로그램이 실행되는 환경을 의미한다.

예시

Windows

Linux

MacOS

Android

iOS

프로그램은 반드시 플랫폼 위에서 실행된다.

3. .NET 플랫폼

.NET은 Microsoft에서 만든 소프트웨어 플랫폼이다.

C# 프로그램이 실행될 수 있도록 도와주는 환경이다.

구성 요소
CLR (Common Language Runtime)

프로그램을 실행하는 실행 엔진

역할

메모리 관리

코드 실행

오류 관리

.NET 라이브러리

자주 사용하는 기능들을 미리 만들어 둔 코드 집합

예시

Console.WriteLine("Hello World");
Math.Abs(-10);
4. 라이브러리와 프레임워크
라이브러리 (Library)

개발자가 필요할 때 가져다 사용하는 코드 모음

특징

개발자가 직접 호출해서 사용

프로그램 흐름을 개발자가 제어

예시

Console.WriteLine("Hello");
프레임워크 (Framework)

프로그램의 전체 구조를 제공하는 개발 환경

특징

프로그램 흐름을 프레임워크가 관리

개발자는 필요한 부분만 작성

예시

ASP.NET

Unity

WPF

5. C# 활용 분야

C#은 다양한 분야에서 사용된다.

1️⃣ GUI 프로그램 개발

Windows에서 실행되는 프로그램 개발

예시

계산기

메모장

관리 프로그램

사용 기술

Windows Forms

WPF

2️⃣ 웹 개발

웹 사이트 및 서버 개발

사용 기술

ASP.NET

예시

로그인 시스템

게시판

쇼핑몰 서버

3️⃣ 게임 개발

게임 개발 엔진 Unity에서 C#을 사용한다.

예시

모바일 게임

PC 게임

4️⃣ IoT 개발

센서와 장치를 인터넷과 연결하는 프로그램 개발

예시

스마트 홈

IoT 센서 장치

6. Visual Studio 2022 개발 환경

C# 프로그램 개발을 위해 Visual Studio 2022를 사용한다.

설치 과정

1️⃣ Visual Studio 2022 다운로드

2️⃣ 설치 관리자 실행

3️⃣ .NET 데스크톱 개발 체크

4️⃣ 설치 진행

7. C# 콘솔 프로그램 만들기
프로젝트 생성

Visual Studio 실행

새 프로젝트 만들기

콘솔 앱(C#) 선택

프로젝트 이름 입력

최상위 문 사용 안 함 체크

8. Program.cs

Program.cs는 프로그램의 시작 파일이다.

프로그램은 Main() 메서드부터 실행된다.

예시 코드

using System;

namespace FirstProgram
{
    internal class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Hello World");
        }
    }
}
9. 프로그램 실행

프로그램 실행 방법

상단 Start 버튼 클릭

F5 키

실행하면 콘솔 창이 열리면서 결과가 출력된다.

10. Console 출력 메서드
Write()

출력만 하고 줄바꿈을 하지 않는다

Console.Write("Hello");
Console.Write("World");

출력 결과

HelloWorld
WriteLine()

출력 후 줄바꿈을 한다

Console.WriteLine("Hello");
Console.WriteLine("World");

출력 결과

Hello
World
11. 자동 완성 기능

Visual Studio에서는 **자동 완성 기능(IntelliSense)**을 제공한다.

단축키

Ctrl + Space

장점

코드 작성 속도 향상

함수 설명 확인 가능

오타 감소

📌 정리

C#은 객체 지향 프로그래밍 언어이다.

.NET 플랫폼 위에서 실행된다.

CLR이 프로그램 실행을 담당한다.

라이브러리는 필요할 때 사용하는 코드 모음이다.

프레임워크는 프로그램 구조를 제공한다.

Visual Studio 2022에서 C# 프로그램을 개발한다.

Console.Write()와 Console.WriteLine()의 차이를 이해해야 한다.

✍️작성자: 박지안
🐧실습 환경: Visual Studio 2022
🗓️ 작업일: 2026-03-13
