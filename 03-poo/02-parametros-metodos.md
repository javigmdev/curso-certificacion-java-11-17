# 2. Paso de parámetros a métodos

# 2.1. Paso de tipos primitivos

- Al pasar un tipo primitivo a un método, estamos pasando una copia del dato

- Si el método modifica su copia, no afecta al original

  ```
  class Test {

       public static void main(String[] args) {
            Calculator calculator = new Calculator();
            int number = 5;
            calculator.modify(number);
            System.out.println(number); // 5
       }

       class Calculator {

            public void modify(int number) {
                 number = number + 3;
                 System.out.println(number); // 8
            }
       }

  }
  ```

<br>

# 2.2. Paso de tipos objeto

- Al pasar un tipo objeto a un método, estamos pasando una copia de la referencia al objeto

  ```
  class Test {

       public static void main(String[] args) {
            Calculator calculator = new Calculator();
            StringBuilder sb = new StringBuilder("hello");
            calculator.modify(sb);
            System.out.println(sb.toString()); // hello bye
       }

       class Calculator {

            public int modify(StringBuilder sb) {
                 sb.append(" bye");
            }

       }

  }
  ```

<br>

# 2.3. Paso de String

- Las cadenas, aunque son objetos, son inmutables

  ```
  class Test {

       public static void main(String[] args) {
            Calculator calculator = new Calculator();
            String hello = new String("hello");
            hello.modify(hello);
            System.out.println(hello); // hello
       }

  }

  class Calculator {

       public void modify(String hello) {
            hello += " bye";
            System.out.println(hello); // hello bye
       }

  }
  ```
