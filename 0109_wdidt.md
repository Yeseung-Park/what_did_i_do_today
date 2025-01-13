# 0109 What did I do today

#### 1. 김영현의 자바 입문 - 코드로 시작하는 자바 첫걸음
- 반복문 문제 못 풀었다.
  - 문제: 이대로 출력하라.
    ```
    //rows = 2
    *
    **
    //rows = 5
    *
    **
    ***
    ****
    *****
    ```
  - 풀이:
    ```java
    package loop;

    public class NestedEx2 {
        public static void main(String[] args) {
            int rows = 5;
            for (int i = 1;i <= rows;i++) {
                for (int j = 1;j <= i;j++) {
                    System.out.print("*");
                }
                System.out.println("");
            }
        }
    }
    ```
  - print는 한 줄에 이어서 쓸 수 있게 함 (python
  의 print와 동일)
  - `println`은 줄넘김인가 뭔가가 가능함
  - 중첩 반복문을 이용해서 별 1개부터 rows개까지 하나씩 띄워가면서 출력하는 것
  - 왜 자바는 문자열 연산자를 허용하지 않는걸까 그 편한걸...
  - 이러다가 파이썬 까먹으면 어떡하지 근데

- 자바는 스코프가 분명히 나눠져 있다는 것이 개빡치는 점이다. 선언한 변수는 어디서든 사용할 수 있게 하면 좋을텐데 말이다.