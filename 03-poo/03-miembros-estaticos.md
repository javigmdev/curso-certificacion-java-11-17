# 3. Miembros estáticos

# 3.1. Métodos estáticos

- Son métodos que no están asociados a ningún objeto particular de la clase
- Se declaran con la palabra _static_

  ```
  class Calculator {

       public static int calculateSquare(int number) {
            return number * number,
       }

  }
  ```

- No es necesario crear un objeto para llamar a estos métodos, se utiliza el nombre de la clase
  ```
  int square = Calculator.square(4);
  ```
- Aunque esta es la forma habitual de usarlos, también se les puede llamar con cualquier instancia de la clase

- Solo pueden llamar a otros miembros de su misma clase que también sean static

  ```
  class Test {
       int a = 2;
       static int b = 5;

       public static int method() {
            int c = a * 3; // error de compilación
            int n = b + 1; // ok
            print(n); // ok
       }

       static void print(int n) {}

  }
  ```

  - No se puede usar en su interior ni _this_ ni _super_

<br>

# 3.2. Atrubutos estáticos

- Son compartidos por todos los objetos de la clase
- Se definen con la palabra _static_

  ```
  class Calculator {
       static int number = 0;

       public void increment() {
            number++;
       }

       public int getNumber() {
            return number,
       }
  }

  class Test {

     public static void main(String[] args) {

          Calculator calculator = new Calculator();
          calculator.increment();
          Calculator calculator2 = new Calculator();
          calculator2.increment();
          System.out.println(calculator.getNumber()); // 2
          System.out.println(calculator2.getNumber()); // 2

     }

  }
  ```

<br>

# 3.3. Bloques estáticos

- Se ejecutan una vez durante la vida de una clases
- Solo pueden acceder a otros miembros estáticos

  ```
  class Calculator {
       static int number = 0;

       static {
            number++;
       }

       public int getNumber() {
            return number;
       }
  }

  class Test {

       public static void main(String[] args) {
            Calculator calculator = new Calculator();
            Calculator calculator2 = new Calculator();
            System.out.println(calculator.getNumber()); // 1
            System.out.println(calculator2.getNumber()); // 1
       }

  }
  ```
