# C# 프로그래밍 - 10주차 정리

## 📚 학습 내용
- 윈도 폼 : 윈도 폼 기본 익히기
- 윈도 폼 : 윈도 폼에서 메서드 활용하기

### 윈도 폼 : 윈도 폼 기본 익히기

#### 프로젝트 생성
- Windows Forms 응용 프로그램 (GUI 응용 프로그램) 만들기
  - [파일]-[새 프로젝트] 클릭 → Windows Form (프로젝트명 : FirstFromApplication)
  - 생성된 프로젝트 & 실행된 프로젝트

#### 윈도 폼의 구조
- 윈도 폼 응용 프로그램 프로젝트의 기본 구조
  - 기본 구조
    - Program.cs 파일
      - 응용프로그램 관련 설정 수행
      - From1 클래스의 인스턴스 생성 및 실행
      ```
      Application.Run(new Form1()) - Form1 클래스의 인스턴스를 생성하고 실행
      ```
- Form1 클래스
- Form1.cs 파일에서 마우스 오른쪽 버튼 클릭, [코드 보기] 클릭
```
namespace FirstFromApplication
{
    public partial class Form1 : Form
    {
        public Form1()
        {
            InitializeComponent();
        }
    }
}
```

#### 디자인 화면에서 요소 생성
- 도구 상자 열기
  - 화면 왼쪽의 도구 상자 클릭 또는 메뉴의 [보기]-[도구 상자]
- 도구 상자에서 원하는 요소를 폼 위로 드래그
  - 도구 상자의 사용
- 속성 보기(메뉴[보기]-[속성])
- 속성 지정
  - (예시) Text라는 이름의 속성을 찾아 원하는 글자로 수정하기

#### 다자인 코드
- 속성 지정
  - (예시) 버튼 이름을 Button1에서 myButton으로 변경하기
- Form1.Designer.cs 파일 확인
  - 버튼과 관련된 코드를 추가된 것 확인
- Name 속성에서 지정한 myButton글자로 변수 만들어짐
- 코드로 인스턴스 생성, 속성 지정을 살펴볼 수 있음
```
Controls.Add(myButton) - myButton을 화면에 추가
private Button myButton - 변수 myButton이 만들어짐
```

#### 코드에서 요소의 속성 지정
- 요소의 속성을 원하는 대로 변경하는 방법
  - Form1.cs 파일 열기 - myButton 객체 활용
  - Form1.cs 파일 열기 - myButton 객체의 Text 속성 변경하기
  - Form1.cs 파일 열기 - myButton 객체 Text 속성을 "코드에서 변경!"으로 변경하기

#### 코드에서 요소 생성
- 직접 Button 클래스의 인스턴스 생성하기
```
Button button = new Button();
```
- 생성한 버튼 화면에 붙이기
  - Form1 클래스가 가지고 있는 Controls 속성 사용
- Controls 속성은 부모로부터 상속받는데, Controls.Add() 메서드를 사용
- 새로 만든 button 객체에 속성을 지정
  - Location 속성 : 위치를 지정(Location속성은 Point클래스의 인스턴스임)
  - 반복문으로 여러 개의 버튼 생성하기

### 윈도 폼 : 윈도 폼에서 메서드 활묭하기

#### 이벤트 정적 연결(디자인에서 연결)
- 화면 디자인
  - 도구 상자에서 버튼(Button 클래스), 텍스트 박스(TextBox 클래스), 레이블(Label 클래스)을 드래그하여 화면 구성
  - Form1.Designer.cs 파일에서 자동 생성된 요소
  ```
  private Button button1;
  private TextBox textBox1;
  private Label label1;
  ```
- 버튼에 적용할 수 있는 이벤트
  - 디자인 화면에서 생성된 버튼 클릭, 속성 화면의 번개 모양 아이콘(이벤트) 클릭
  - Click 글자 자체 또는 옆 빈 공간을 잡고 더블 클릭하여 코드 확인
- 디자인 화면의 속성 화면
  - Click 부분에 자동 생성된 button1_Click() 메서드가 연결되었는지 확인
  - 연결된 이벤트
  ```
  Click → button1_Click
  ```
- 버튼 클릭 메서드의 코드 작성
  - Button1_click() 메서드
  ```
  private void button1_Click(object sender, EvenArgs e)
  {
      textBox1.Text = "+";
      label1.Text = "+";
  }
  ```
  - 버튼을 여러 번 클릭했을 때의 화면
  ```
  [button1]
  |++++++++|
  label1++++++++
  ```

#### 이벤트 동적 연결(코드에서 연결)
- 이벤트 동적 연결(코드에서 연결)
  - Form1.Designer.cs 파일에 자동 생성된 코드
  ```
  button1.Location = new Point(12, 12);
  button1.Name = "button1";
  button1.Size = new Size(75, 23);
  button1.TabIndex = 0;
  button1.Text = "button1";
  button1.UseVisualStyleBackColor = true;
  button1.Click += button1_click; // 여기가 바로 이벤트 연결하는 부분
  ```
  - Form1.cs 파일에서 button1에 Click 이벤트 연결(번개 모양의 이벤트)
  - 이벤트 메서드 자동 작성, 이벤트 뒤에 += 기호 입력
    - 자동 완성 기능으로 코드를 자동 삽입(Tab키를 두 번 누름)
    ```
    public Form1()
    {
       InitializeComponent();
       button1.Click += ~ [Button1_Click; (삽입하려면 <Tab>키 누름)]
    }
    ```
    - 자동 생성된 이벤트 메서드
    ```
    [구현하지 않았으니 구현해달라고 강제로 오류를 띄우는 코드]
    private void Button1_Click(object sender, EventArgs e)
    {
        throw new NotImplementedException();
    }
    ```
    - 이벤트 메서드의 형태(2개의 매개변수 사용)
    ```
    private void Button1_Click(object? sender, EventArgs e)
    {

    }
    ```
    - sender 객체
      - 이벤트를 발생시킨 자기 자신을 나타냄
      - sender 객체 활용
        - (예시) 버튼을 클릭한 자기자신의 Text 속성 변경하기
        ```
        private void Button1_Click(object? sender, EventArgs e)
        {
            Button self = (Button)sender;
            self.Text = "저를 클릭했습니다!";
        }
        ```

#### 이벤트 메서드의 매개변수
- 이벤트 정보 객체
  - 이벤트와 관련된 추가 정보를 알려주는 객체
  - e 객체 멤버에 대한 정보(속성, 메서드) 확인
  ```
  private void button1_Click(object sender, EventArgs e)
  {
      e.~
  }
  ```

#### 백그라운드 요소의 이벤트
- 폼의 백그라운드에서 작동하는 요소들
  - 도구상자의 구성 요소 확인
  - 타이머(Timer 클래스)
    - 특정 시간 간격마다 특정한 코드를 호출해주는 기능
- 타이머를 이용한 프로그램
  - 버튼을 누르면 버튼의 Enabled 속성을 true로 바꿔서 타이머를 작동시키고, 프로그램을 실행한 지 몇 초나 지났는지 확인하는 프로그램
  - (1) 타이머 객체의 속성 지정
  - (2) Tick 이벤트의 이벤트 메서드 자동생성
  - (3) Tick 이벤트 메서드의 내부코드 작성
    - 시간경과 확인 코드
    - 프로그램이 시작된 지 몇 초가 지났는지 출력
   
##### ✍️작성자: 박지안
##### 🐧실습 환경: Visual Studio 2022
##### 🗓️ 작업일: 2026-05-29
