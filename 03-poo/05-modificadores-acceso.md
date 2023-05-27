# 5. Modificadores de acceso

# 5.1. Función y tipos

- Determinan la visibilidad de los miembros de una clase
- La siguiente tabla indica los tipos de modificadores y donde se aplican

  |             | public | protected | (default) | private |
  | ----------- | ------ | --------- | --------- | ------- |
  | class       | yes    | no        | yes       | no      |
  | attribute   | yes    | yes       | yes       | yes     |
  | method      | yes    | yes       | yes       | yes     |
  | constructor | yes    | yes       | yes       | yes     |

- Modificadores de acceso por clase, paquete, subclase y otros

  | modifiers | class | package | subclass | others |
  | --------- | ----- | ------- | -------- | ------ |
  | public    | yes   | yes     | yes      | yes    |
  | protected | yes   | yes     | yes      | no     |
  | (default) | yes   | yes     | no       | no     |
  | private   | yes   | no      | no       | no     |

- _Protected_ se estudia en herencia

<br>

# 5.2. Public

- Si una clase o miembro de esta es _public_, puede utilizarse desde cualquier clase que esté en su mismo paquete o en cualquier otro

  ```
  package p1;

  public class Test {
       public Test(int a){}
       public void method(){}
  }
  ```

  ```
  package p2;
  import p1.Test;

  class Other {
  void method() {
       Test test = new Test(10);
       test.method();
  }
  }
  ```

  <br>

# 5.3. Default

- Es el ámbito que se aplica cuando no se indica ningún modificador. El elemento que lo lleve solo es accesible desde clases de su mismo paquete

  ```
  package p1;

  public class Calculator {
       Calculator(){}

       public Calculator(int a) {}

       void method() {}
  }

  public class Calculator2 {

     void tester() {
          Calculator calculator = new Calculator(); // ok
          calculator.method(); // ok
     }

  }
  ```

  ```
  package p2;
  import p1.Calculator;

  class Test {

     void method() {
          Calculator calculator = new Calculator(); // ok
          calculator.method(); // error de compilación
          Calculator calculator2 = new Calculator(); // error de compilación (constructor no public)
     }

  }
  ```

<br>

# 5.4. Private

- El miembro solo es accesible desde el interior de la clase. Muy habitual en atributos para encapsulación

  ```
  public class Table {
       private String color;
  }

  class Test {

       void method() {
            Table table = new Table();
            table.color = "Black"; // error de compilación
       }

  }
  ```
