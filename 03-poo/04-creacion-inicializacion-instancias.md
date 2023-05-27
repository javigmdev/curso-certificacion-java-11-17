# 4. Creación e inicialización de instancias

# 4.1. Constructores

- Bloques de código que se ejecutan al crear un objeto de la clase
- Al igual que los métodos, pueden recibir parámetros, aunque no tienen tipo de devolución y su nombre siempre es igual que el de la clase

  ```
  class Calculator {

       public Calculator(){}

  }

  Calculator calculator = new Calculator();

  class Test {

     private int number;

     public Test(int number) {
          this.number = number;
     }

  }

  Test test = new Test(10);
  ```

  <br>

# 4.2. Constructor por defecto

- Si no se define un constructor de forma explícita en una clase, el compilador añade un constructor por defecto, que no tiene parámetros y tampoco ninguna instrucción

  ```
  class Test {}

  // equivale a

  class Test {
     public Test() {}
  }
  Test test = new Test();
  ```

- Si se define explícitamente un constructor, el compilador ya no crea el constructor por defecto

  ```
  class Test {
       public Test(int number) {}
  }

  Test test = new Test(10); // error de compilación
  ```

<br>

# 4.3. Sobrecarga de constructores

- Una clase puede incluir varios constructores que permitan inicializar los objetos de diferente forma
- Se siguen las mismas reglas que con la sobrecarga de métodos

  ```
  class Test {
       public Test() {}
       public Test(int a) {}
       public Test(int a, int b) {}
  }

  Test test1 = new Test();
  Test test2 = new Test(5);
  Test test3 = new Test(3,1);
  ```

<br>

# 4.4. Llamadas a otro constructor

- Desde un constructor se puede llamar a otro constructor de la misma clase utilizando la expresión _this_(argumentos)
- Debe ser la primera instrucción del constructor

  ```
  class Test {

       public Test() {
            this(5); // ok
       }

       public Test(int a) {}

       public Test(int a, int b) {
            int s = a + b;
            this(s); // error de compilación
       }

  }
  ```

<br>

# 4.5. Bloque de inicialización de instancia

- Son bloques de código que se ejecutan cada vez que se crea un objeto de la clase, antes del contructor
- Se delimitan por llaves

  ```
  class Calculator {

     {
        System.out.println("calculator");
     }

     public Test() {
        System.out.println("constructor");
     }

  }

  class Test {

     public static void main(String[] args) {
          Calculator calculator = new Calculator();
          Calculator calculator2 = new Calculator();
     }

  }

  // Se imprime:
  //                calculator
  //                constructor
  //                calculator
  //                constructor
  ```
