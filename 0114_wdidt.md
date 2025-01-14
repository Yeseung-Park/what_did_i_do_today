# 0114 What did I do today
- [X] JAVA 객체지향 프로그래밍 playlist
- [X] JAVA 상속 playlist
- [X] JAVA 인터페이스 playlist
- [X] JAVA 예외 처리 playlist

## JAVA 객체지향 프로그래밍
### 클래스
#### 클래스를 사용하는 이유
- 클래스를 사용하기 전
  ```java
  public class MyOOP {
      public static void main(String[] args) {
          delimiter = "----";
          printA();
          printA();
          printB();
          printB();

          delimiter = "****";
          printA();
          printA();
          printB();
          printB();
      }
      public static String delimiter = "";
      public static void printA() {
          System.out.println(delimiter);
          System.out.println("A");
          System.out.println("A");
      }
      public static void printB() {
          System.out.println(delimiter);
          System.out.println("B");
          System.out.println("B");
      }
  }
  ```
- 클래스를 사용한 후
  ```java
  class Print {
      public static String delimiter = "";
      public static void A() {
          System.out.println(delimiter);
          System.out.println("A");
          System.out.println("A");
      }
      public static void B() {
          System.out.println(delimiter);
          System.out.println("B");
          System.out.println("B");
      }
  }
  public class MyOOP {
      public static void main(String[] args) {
          Print.delimiter = "----";
          Print.A();
          Print.B();

          Print.delimiter = "****";
          Print.A();
          Print.B();
      }
  }
  ```
- 클래스를 사용했더니 훨씬 깔끔하고 가독성이 좋은 코드가 되었다.
- 클래스를 사용하면 어떤 코드가 기능적으로 연관이 되어있는지 한 눈에 알아볼 수 있는 장점도 있다.

#### 구조
- 클래스라는 키워드를 사용하여 클래스를 만든다.
- 내부에 클래스 소속의 변수와 메서드를 담는다.
  - 변수와 메서드를 통틀어서 멤버라고 한다.
- 사실 자바는 모두 클래스다.
  - 자바는 파일을 만들 경우 파일명과 똑같은 클래스를 만들고 자바는 해당 클래스의 main 메서드를 실행하도록 설계되어있다.

### 인스턴스
```java
class Print {
    public String delimiter = "";
    public void A() {
        System.out.println(delimiter);
        System.out.println("A");
        System.out.println("A");
    }
    public void B() {
        System.out.println(delimiter);
        System.out.println("B");
        System.out.println("B");
    }
    // 메서드와 변수가 인스턴스 소속일 수 있게 static을 없애주었다.
    // 이에 대해서는 뒤에서 좀 더 자세히 공부해야할 듯.
}

public class MyOOP {
    public static void main(String[] args) {
        Print p1 = new Print();
        // p1이라는 Print의 인스턴스 생성
        p1.delimiter = "----";
        p1.A();
        p1.B();

        Print p2 = new Print();
        // p2라는 Print의 인스턴스 생성
        p2.delimiter = "****";
        p2.A();
        p2.B();

        p1.A();
        p2.A();
    }
}
```
- 코드가 훨씬 더 깔끔해졌다!

#### 인스턴스와 클래스의 차이
- 일단 내가 이해한 걸로는 클래스는 유사한 기능을 하는 메서드와 변수를 모아둔 것
- 인스턴스는 클래스를 통해 만든 뭔가... 커다란 클래스의 기능을 대신하는 작은 무언가...
- 그니까 뭔가 클래스는 본점 인스턴스는 체인점...?
- 사실 이 부분은 파이썬에서도 공통적으로 적용되는 사항이라 이해가 어느정도 잘 되는 것 같다.
- GPT 가라사대 클래스는 객체를 생성하기 위한 청사진 또는 틀, 인스턴스는 클래스에서 실제로 생성된 객체... 정도로 생각하면 된다네.
  - 클래스 자체를 사용할수는 있지만 인스턴스를 생성해서 사용하는 것이 대부분인 것 같다.

### static

- 인스턴스 변수는 인스턴스를 통해서 사용되도록 고안된 변수이다.
- 클래스 메서드 내부에서는 인스턴스 변수에 접근할 수 없다.
- 그러나 인스턴스 메서드 내부에서는 클래스 변수와 인스턴스 변수 모두에 접근할 수 있다.
- 클래스를 통해서 직접 인스턴스 변수와 메서드에 접근하는 것은 금지되어 있다.
- 인스턴스를 생성했을 때 인스턴스는 클래스의 모든 내용을 일단 복제를 한다고 생각하면 된다.
  - 그러나 이 때 클래스 변수와 클래스 메서드는 클래스 소속이기 때문에 완전 복제를 해서 개별적으로 사용할 수 있다기보다는 참조만 한다.
  - 인스턴스 변수와 인스턴스 메서드는 완전 복제를 했기 때문에 원래 클래스의 내용과 개별적인 존재로 인스턴스에서 인스턴스 변수와 메서드를 수정한다고 해서 클래스 내부의 인스턴스 변수와 메서드가 수정되지는 않는다.
  - 그러나 클래스 변수와 메서드는 완전 복제를 한 것이 아니라 그냥 참조만 하고 있는, 엄연히 연결되어 있는 관계이기 때문에 인스턴스에서 클래스 변수와 메서드를 수정할 경우 원래 클래스 내부의 클래스 변수와 메서드도 동일하게 수정된다.
  - 이 개념이 상당히 헷갈리는군...
  - 다음 코드로 한 번 쭉 보자.
    ```java
    class Foo {
        public static String classVar = "I class var";
        public String instanceVar = "I instance var";
        public static void classMethod() {
            System.out.println(classVar);
        }
        public void instanceMethod() {
            System.out.println(classVar);
            System.out.println(instanceVar);
        }
    }
    public class StaticApp {
        public static void main(String[] args) {
            Foo f1 = new Foo();
            Foo f2 = new Foo();

            System.out.println(f1.classVar);    // I class var
            System.out.println(f1.instanceVar);    // I instance var
            
            f1.classVar = "changed by f1";
            System.out.println(Foo.classVar);    // changed by f1
            System.out.println(f2.classVar);    // changed by f1
            // 클래스 변수이기 때문에 f1 인스턴스의 수정사항이 클래스와 해당 클래스의 모든 인스턴스에 적용된다.
            
            f1.instanceVar = "changed by f1";
            System.out.println(f1.instanceVar);    // changed by f1
            System.out.println(f2.instanceVar);    // I instance var
            // 인스턴스 변수이기 때문에 f1에서의 변화가 영향을 미치지 않는다.
            // 참고로 클래스에서는 인스턴스 변수에 접근할 수 없기 때문에 Foo.instanceVar 같은건 존재하지 않는다.
        }
    }
    ```

- 여러 상태가 공통된 클래스를 써야할 경우 인스턴스를 사용하는 것이 좋다.
  ```java
  class Accounting {
      public double valueOfSupply;
      public static double vatRate = 0.1;
      
      public Accounting(double valueOfSupply) {
          this.valueOfSupply = valueOfSupply;
      }
      // 생성자! 인스턴스를 생성할 때 인자로 전달한 값을 해당 인스턴스의 valueOfSupply 값으로 설정할 수 있다.
      
      public double getVAT() {
          return valueOfSupply * vatRate;
      }
      public double getTotal() {
          return valueOfSupply + getVAT();
      }
  }
  public class AccountingApp {
      public static void main(String[] args) {
          Accounting a1 = new Accounting(10000.0);
          Accounting a2 = new Accounting(20000.0);
          // Value of Supply의 값을 매번 수정해주기 보다는 인스턴스를 생성해서 코드를 예쁘게 작성할 수 있다.

          System.out.println("Value of supply: " + a1.valueOfSupply);
          System.out.println("Value of supply: " + a2.valueOfSupply);

          System.out.println("VAT : " + a1.getVAT());
          System.out.println("VAT : " + a2.getVAT());

          System.out.println("Total : " + a1.getTotal());
          System.out.println("Total : " + a2.getTotal());
      }
  }
  ```


### 생성자
- 인스턴스가 생성될 때 최초로 수행되어야 하는 작업 등을 지정할 때 생성자를 사용할 수 있다.
- 클래스와 똑같은 이름의 메서드를 정의하면 그게 생성자다.
- 인스턴스를 생성할 때 자바는 이 클래스와 동일한 이름의 메서드가 있다면 그걸 호출하도록 약속이 되어있기 때문에 이를 이용해서 인스턴스를 생성하는 순간 수행되어야 하는 행위를 지정할 수 있다.

#### this
- 해당 클래스가 인스턴스화 되었을 때 인스턴스를 가리키는 특수한 키워드

<br>


```
전반적으로 정보처리기사 공부할 때 배운 내용이라 읽을 수는 있었는데 구체적으로 어떻게 작성하는 것인지 새롭게 알게된 것 같다.
```

## JAVA 상속
```java
class Cal {
    public int sum(int v1, int v2) {
        return v1+v2;
    }
}
class Cal3 extends Cal{

}
public class InheritanceApp {
    public static void main(String[] args) {
        Cal c = new Cal();
        System.out.println(c.sum(2, 1));

        Cal3 c3 = new Cal3();
        System.out.println(c3.sum(2, 1));
        // Cal3 내부에는 sum이 정의되어 있지 않지만 Cal3는 Cal을 상속받고 있기 때문에 Cal에서 정의된 sum을 사용할 수 있다.
    }
}
```

### 오버라이딩
- 부모 클래스에서 정의된 메서드를 자식 클래스에서 재정의하는 것
- 부모 클래스의 메서드에 "올라 타서" 재정의를 했다는 느낌으로 외우면 좋을 듯.
- 메서드의 **오버로딩**과 헷갈리지 말기!!!!!!!!
  - 오버로딩: 이름은 같지만 매개변수가 다른 메서드를 여러 개 정의하는 것.
  - 매개변수의 타입과 순서가 다르면 오버로딩이 가능하다.
```java
class Cal {
    public int sum(int v1, int v2) {
        return v1+v2;
    }
}
class Cal3 extends Cal{
    public int minus(int v1, int v2) {
        return v1-v2;
    }
    // 오버라이딩
    public int sum(int v1, int v2) {
        System.out.println("Cal3!!");
        return v1+v2;
    }
    // 부모 클래스에서 정의된 sum 메서드를 자식 클래스에서 재정의하였다.
}
public class InheritanceApp {
    public static void main(String[] args) {
        Cal c = new Cal();
        System.out.println(c.sum(2, 1));    // 3

        Cal3 c3 = new Cal3();
        System.out.println(c3.minus(2, 1));    // Cal3!! / 3
        System.out.println(c3.sum(2, 1));    // 1
    }
}
```

### super / this
- **super**: 부모 클래스를 가리키는 키워드
- **this**: 자식 클래스를 가리키는 키워드

### 생성자가 있는 클래스를 상속받을 경우
- 생성자가 있는 클래스를 상속받았을 경우 자식 클래스에도 반드시 부모 클래스를 호출하는 생성자를 만들어야 한다.
```java
class Cal {
    int v1, v2;
    Cal(int v1, int v2) {
        System.out.println("Cal init!!");
        this.v1 = v1;
        this.v2 = v2;
    }
    public int sum() {
        return this.v1+v2;
    }
}
class Cal3 extends Cal{
    Cal3(int v1, int v2) {
        super(v1, v2);    // 부모 클래스의 생성자를 의미
        System.out.println("Cal3 init!!");
    }
    public int minus() {
        return this.v1-v2;
    }
}
public class InheritanceApp {
    public static void main(String[] args) {
        Cal c = new Cal(2, 1);
        Cal3 c3 = new Cal3(2, 1);
        System.out.println(c3.sum());
        System.out.println(c3.minus());
    }
}
```

## JAVA 인터페이스
- 쉽지 않다. 이게 제일 헷갈리는 듯.
- 인터페이스는 클래스의 내부 구성 요소가 준수해야 할 규칙 같은 것이라고 생각하면 된다.
- implements된 인터페이스를 따르지 않는 메서드는 컴파일조차 안 된다.
- 하나의 클래스는 여러 개의 인터페이스를 가질 수 있다.
- 변수의 경우 인터페이스에서 값을 정의하며 메서드의 경우 메서드 이름, 매개 변수와 타입, 반환 값의 타입 정도만 인터페이스에서 정의하며 실제 내용은 클래스에서 정의한다.
```java
interface Calculable {
    double PI = 3.14;
    // 변수의 경우 값을 인터페이스에서 정의한다.
    int sum(int v1, int v2);
    // 메서드의 경우 내용은 클래스에서 정의한다.
}
// int 2개를 인자로 받고 반환 값도 int인 sum이라는 이름의 메서드
// 라는 나름의 규칙
interface Printable {
  void print();
}
class RealCal implements Calculable, Printable {
    public int sum(int v1, int v2) {
        return v1+v2;
    }
    public void print() {
      System.out.println("This is RealCal!!");
    }
}
// RealCal은 Calculable이라는 인터페이스를 따른다.
// Calculable에 정의된 내용을 따르지 않는 애들은 애초에 컴파일 자체가 안 된다.
// 클래스는 단 하나의 클래스만을 상속받을 수 있지만 인터페이스는 여러 개를 가질 수 있다.

public class InterfaceApp {
    public static void main(String[] args) {
        RealCal c = new RealCal();
        System.out.println(c.sum(2, 1));    // 3
        c.print();    // This is RealCal!!
        System.out.println(c.PI);    // 3.14
    }
}
```

```
스프링에서 인터페이스를 사용하는 이유는 다양한 디피가 이이
```

### 다형성 Polymorphism
- 하나의 클래스가 다양한 기능을 하는... 무언가...
- 그니까 저 위의 코드에서 `RealCal`은 `Calculable`이랑 `Printable`이라는 인터페이스를 갖고 있다.
- 근데 저 인스턴스를 정의할 때 `RealCal c = new RealCal();`이 아니라 `Calculable c = new RealCal();` 이런 식으로 인터페이스를 데이터 타입으로 정의할 수 있따는 거지.
  - 그러나 이렇게 정의하게 될 경우 해당 인스턴스는 `interface Calculable`에 정의된 메서드와 변수만 사용 가능하다.
- 이렇게 하나의 클래스가 다양한 기능을... 하는...? 다양한 모습으로 변하는...? 그런걸...? 다형성...? 이라고 한다...?
- 이건 더 공부를 해야할 것 같다. 애초에 인터페이스가 너무 어려움 일단.

## JAVA 예외처리
### try catch
```java
public class ExceptionApp {
    public static void main(String[] args) {
        System.out.println(1);
        int[] scores = {10, 20, 30};
        try {
            System.out.println(scores[3]);
        } catch(ArrayIndexOutOfBoundsException e) {
            System.out.println("없는 값을 찾고 계시네요 ^^");
        }
        try {
            System.out.println(2 / 0);
        } catch(ArithmeticException e) {
            System.out.println("잘못된 계산이네요.");
        }
        System.out.println(3);
    }
}
```

- try 내부 안에 있는 구문은 한 번 catch로 빠져나올 경우 try 내부 안의 뒤 구문은 실행이 되지 않고 바로 빠져나간다.
  ```java
  public class ExceptionApp {
      public static void main(String[] args) {
          System.out.println(1);
          int[] scores = {10, 20, 30};
          try {
              System.out.println(2);
              System.out.println(scores[3]);
              System.out.println(3);
              System.out.println(2 / 0);
              System.out.println(4);
          } catch(ArithmeticException e) {
              System.out.println("잘못된 계산이네요.");
          } catch(ArrayIndexOutOfBoundsException e) {
              System.out.println("없는 값을 찾고 계시네요 ^^");
          }
          System.out.println(5);
      }
  }

  // 1
  // 2
  // 잘못된 계산이네요.
  // 5

  // 현재 System.out.println(scores[3])에서 catch로 빠져나간 후 뒤의 내용이 실행이 되지 않았다.
  ```

### Checked Exception vs UnChecked Exception
#### Checked Exception
- 컴파일도 안 되는 exception
- RuntimeException을 제외한 exception
  - IOException
- 예외처리 안 하면 빨간 줄 쳐진다.
  - 자바는 너무나 친절해서 예외처리가 반드시 필요한 IOException에 대해서는 어디가 필요한 지 알려준다.
  - 이게 제일 많이 나오는 곳이 resource를 다룰 때이다.
    - 이는 try-with-resource를 이용하면 예외처리를 간단하게 할 수 있다.
      ```java
      import java.io.FileWriter;
      import java.io.IOException;

      public class TryWithResource {
          public static void main(String[] args) {
              try (FileWriter f = new FileWriter("data.txt")) {
                  f.write("Hello");
              } catch (IOException e) {
                  e.printStackTrace();
              }
          }
      }

      // try가 필요한 리소스를 선언하는 구문을 인자로 넣으면 자바는 자동으로 close를 해준다.
      ```
#### Unchecked Exception
- 사용자의 재량에 따른 exception
- RuntimeException을 포함한 하위 exception

```
예외 처리를 직접 하지 않고 throw를 통해 전달할 수도 있는데 이건 나중에 추가적으로 알아보자.
```

## 김영한의 스프링 입문 - 코드로 배우는 스프링 부트, 웹 MVC, DB 접근 기술
### 트러블 슈팅
#### 1. 프로젝트 생성 후 빌드 과정 트러블
- 뭔가 하지도 않았는데 트러블이 발생해서 굉장히 화가 난다.
- **문제 상황** : 강의에서 추천해 준 [스프링 부트 스타터 사이트](https://start.spring.io/)를 이용해서 프로젝트 파일을 만들고 build.gradle을 프로젝트로 열었는데 뭔 괴상한 오류가 떴다.
  - 근...데 괴상한 오류를 다시 보려고 똑같은 사이트에서 다시 만들어서 실행했더니 이제는 됐다.
  - 허무한 내 시간이 날라갔다.
- **해결 방법** : 아무래도 스프링 부트 스타터 사이트에서 java 버전을 17로 해서 그랬던 것 같다. 실제로 내가 사용하고 있는 JDK는 23 버전인데 말이다. 나는 그냥 17 이상이면 된다고 하길래 17로 해도 괜찮을 줄 알았다. 그걸 바꾸니까 제대로 실행이 됐다.

## 더 공부 해 볼 것
1. 다형성 (Polymorphism)
2. 접근 제어 (Access Modifiers)
3. Final
4. 추상화 (Abstract)