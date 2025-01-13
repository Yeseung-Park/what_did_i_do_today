# 0113 What did I do today
### 1. 김영한의 자바 입문 - 코드로 시작하는 자바 첫걸음

#### 오늘 공부한 내용
- 자바는 스코프를 벗어난 변수에 대한 메모리를 삭제한다.
  - 스코프가 있으면 효율적인 메모리 사용 및 유지보수가 가능하다.
  - 변수의 스코프는 꼭 필요한 곳으로 한정해서 사용하자.

- double을 int로 형변환 할 경우 double에 있는 정수 부분만 가져온다. 즉 버림을 진행한다.

- 자바에서의 계산
  - 같은 타입끼리의 계산은 같은 타입의 결과
  - 서로 다른 타입끼리의 계산은 큰 범위로 자동 형변환

- Scanner 문제 중 몰랐던 점 1
  ```java
  package scanner;

  import java.util.Scanner;

  public class ScannerWhileEx1 {
      public static void main(String[] args) {
          Scanner scanner = new Scanner(System.in);

          while (true) {
              System.out.print("이름을 입력하세요 (종료를 입력하면 종료): ");
              String name = scanner.nextLine();
              if (name.equals("종료")) {
                  System.out.println("프로그램을 종료합니다.");
                  break;
              }

              System.out.print("나이를 입력하세요: ");
              int age = scanner.nextInt();
              scanner.nextLine();    // 숫자 입력 후의 줄바꿈 처리 필요
              System.out.println("입력한 이름: " + name + ", 나이: " + age);
          }
      }
  }
  ```
    - 이 코드에서 `scanner.nextLine();`을 넣지 않으면 두 번째 while문을 돌릴 때 이름 입력이 스킵되는 현상이 발생한다.
    - 이는 Scanner 클래스의 입력 처리 방식에서 발생하는 현상으로 `nextInt();` 메서드는 숫자만 읽고 입력한 뒤의 엔터키는 처리하지 않는다.
      - 즉 엔터키는 입력 버퍼에 남아있는 것
      - 이를 이름 입력시의 `nextLine()`이 읽어버리면서 아무것도 입력이 되지 않고 넘어가게 된다.
    - 이런 현상을 막아주기 위해 `scanner.nextLine();`을 추가해주는 것이다.
      - 이렇게 되면 입력 버퍼에 남아있는 엔터키를 얘가 가져가면서 다음 이름 입력시에는 정상적으로 이름을 입력할 수 있게 된다.

- Scanner 문제 중 몰랐던 점 2
  - `double average = (double) sum / count;`
    - 여기서 sum과 count는 둘 다 int기 때문에 단순히 average의 타입을 double로 설정해준다고 해서 소수점까지 나오지 않는다.
    - 소수점까지 제대로 나오게 하기 위해서는 sum / count를 double로 바꿔준 다음 average에 담아야 한다.

- 자바의 배열
  ```java
  int[] students;
  students = new int[5];
  ```
    - `int[] students;`는 int를 담을 수 있는 배열의 이름을 우선 선언하는 것이다.
    - `students = new int[5];`를 함으로써 크기가 5인 배열이 만들어지는 것이며 `int[] students`에는 크기가 5인 배열이 만들어진 메모리 공간의 참조값이 보관된다.
      - 이 참조값은 배열의 첫 번째 원소를 가리킨다.
    - 이게 생각보다 상당히 복잡해서... 잘 알아둬야 할 듯.

- 자바의 변수 데이터 타입
  1. 기본형
      - `int`, `long`, `double`, `boolean` 등 변수에 사용할 값을 직접 넣을 수 있는 데이터 타입
      - 선언과 동시에 크기가 정해지기 때문에 크기를 동적으로 바꿀 수 없다.
      - 사용할 값을 직접 저장한다.
  2. 참조형
      - 데이터에 접근하기 위한 참조(주소)를 저장하는 데이터
      - 크기를 동적으로 할당할 수 있어 유연성을 제공할 수 있다.
      - 메모리에 저장된 배열이나 객체의 참조를 저장한다.

- 자바의 편리한 배열 선언
  - `int[] students = {90, 80, 70, 60, 50};`
  - 이 경우는 배열 변수의 선언을 한 줄에 함께 사용할 때만 가능하다.
  - 2차원 배열도 동일하게 선언 가능하다.
    ```java
    int[][] arr = {
            {1, 2, 3},
            {4, 5, 6}
    }
    ```

- for-each문
  ```java
  int[] numbers = {1, 2, 3, 4, 5};

  for (int number : numbers) {
      System.out.println(number);
  }
  ```
  - 약간 파이썬의 `for num in numbers:`와 같은 형태라고 생각하면 된다.

- 배열 강의의 2차원 배열1 문제에서 유의할 점
  - 과목에 대한 배열도 따로 지정해줘야한다!
  - 파이썬의 딕셔너리가 굉장했던 것...
  - 파이썬 최고...

- 자바의 메서드는 항상 반환값을 받을지, 어떤 타입의 반환값을 받을지 정해줘야 한다.
  - 파이썬 최고22222.....

- **자바는 항상 변수의 값을 복사해서 대입한다.**

- 메서드 오버로딩
  - 이름이 같고 매개변수가 다른 메서드를 여러 개 정의하는 것
  - 메서드의 이름이 같아도 매개변수의 타입 및 순서가 다르면 오버로딩을 할 수 있다.
    - 그러나 메서드 이름과 매개변수 타입이 같으면 오버로딩을 할 수 없다.
    ```java
    // 오버로딩 실패
    int add(int a, int b);
    double add(int a, int b);
    ```

- 메서드 시그니처
  - 메서드 이름 + 매개변수 타입
  - 자바에서 메서드를 구분할 수 있는 고유한 식별자나 서명
  - 메서드 이름이 같아도 메서드 시그니처가 다르면 다른 메서드로 간주한다.
  - 반환 타입은 시그니처에 포함되지 않는다는 것을 주의.

#### 더 공부해볼만한 내용
1. 메서드의 제어자