# 1. Declaración, inicialización y tipos de variables

# 1.1 Declaración de variables

Declaración: tipo + identificador

```
int age;
```

Declaración e inicialización:

```
int age = 20;
```

Declaración múltiple:

```
int age, counter, result = 0;
```

<br>

# 1.2. Identificadores

- Se puede utilizar cualquier combinación de letras, números, $ y \_
- Existen las siguiente restricciones:
  - No se pueden usar palabras reservadas como identificador (if, for, switch...)
  - No puede comenzar por caracter numérico

```
int _1 = 10;   //ok
char break;    //error de compilación
int 3aj;       //error de compilación
float car.t;   //error de compilación
```

<br>

# 1.3. Ámbito de las variables

Las variables pueden declararse:

- A nivel de clase compartidas por todos los métodos (atributos o campos)
- En el interior de un método (locales). Sólo son visibles dentro del método

```
class User {
     private int age; // variable atributo

     public void calculateRetirementAge(){
          int retirementAge; // variable local
          int age; // variable local con el mismo nombre que el atributo
          age = 20; acceso a variable local
          this.age = 30; acceso a variable atributo
          ...
     }
}
```

<br>

# 1.4. Inicialización por defecto

- **Variables locales**: NO se inicializan por defecto. Es necesario asignarles un valor antes de utilizarlas.

```
public void method(){
     int c;
     c=c+3; // error de compilación
}
```

- **Variables de atributo**: se inicializan por defecto
  - enteros: 0
  - decimales: 0.0
  - boolean: false
  - char: '\u0000' (caracter nulo)

```
class User {
     int age;
     boolean hasCar;

     public void method(){
          c = c + 3; // 0 + 3
          System.out.println(hasCar); // false
     }
}
```

<br>

# 1.5. Variables primitivas y variables de referencia (objetos)

- **Variables primitivas**: son tipos de datos básicos y representan valores simples. Hay 8 tipos primitivos:

  - _byte_: entero de 8 bits
  - _short_: entero de 16 bits
  - _int_: entero de 32 bits
  - _long_: entero de 64 bits
  - _float_: número de punto flotante de 32 bits
  - _double_: número de punto flotante de 64 bits
  - _char_: carácter unicode de 16 bits
  - _boolean_: valor booleano (true o false)

<br>

- **Variables de referencia (objetos)**:
  - Se utilizan para referenciar objetos (la variable contiene una referencia del objeto)
  - Almacenan la dirección de memoria del objeto, la referencia al dato
  - Mediante la variable se accede a los métodos del objeto
    ```
    String name = new String("Tom");
    name.length();
    ```

<br>

## Asignación de variables primitivas y de referencia

- Las variables primitivas almacenan los valores directamente, mientras que las variables de referencia almacenan direcciones de memoria que apuntan a objetos
- Al asignar variables primitivas, se copia el valor real, mientras que al asignar variables de referencia, se copia la referencia al objeto

<br>

Ejemplo asignación de variables primitivas:

```
int a = 10;
int b = a; // Se copia el valor de 'a' en 'b'
b = 20; // Modificación de 'b'
System.out.println(a); // Imprime 10 (valor original de 'a')
System.out.println(b); // Imprime 20
```

Ejemplo de asignación de variables de referencia:

```
Company company1 = new Company("Twitter");
Company company2 = company1; // Se copia la referencia de 'company1' en 'company2'

company2.name = "Facebook"; // Modificación del nombre a través de 'company2'

System.out.println(company1.name); // Imprime "Facebook" (se refleja en 'company1')
System.out.println(company2.name); // Imprime "Facebook"
```

<br>

# 1.6. Literales

- Los literales enteros se pueden representar en:

  - _decimal_: 289
  - _octal_: 0453
  - _hexadecimal_: 0xAF7
  - _binario_: 0b100011

- Se puede utilizar el símbolo \_ para representar un literal numérico, para mejorar la legibilidad de los literales numéricos:
  ```
  int number1 = 1_000_000;
  long number2 = 9_876_543_210L;
  double number3 = 3.14_15_93;
  float number4 = 1234.5678_9f;
  ```
- No se puede utilizar el símbolo \_ al principio, al final o junto al punto decimal. Los siguientes ejemplos dan errores de complicación:

  ```
  int number1 = _345;
  double number2 = 45._9;
  long number3 = 234_;
  ```

- Los literales enteros son int. Para que sean long hay que añadir l
  ```
  int number1 = 10;
  long number2 = 10l;
  ```
- Los literales decimales son double. Para que sean float hay que añadir f
  ```
  double number1 = 6.7;
  float number2 = 6.7f;
  float number3 = 6.7; // error de compilación
  ```

<br>

# 1.7. Conversiones de tipos (casting)

- Todos los tipos primitivos son convertibles en otros, salvo boolean
- NO se puede hacer conversión implícita ni explícita entre tipos primitivos y objetos
  ```
  String name = new String("Tom");
  int number = (int)name; // error de compilación
  ```
- Las conversiones pueden ser

  - **implícitas** (casting implícito): cuando se realiza una conversión de un tipo de dato de menor rango a uno de mayor rango. En este caso, se realiza la conversión de forma automática sin necesidad de especificar ningún operador de casting

    ```
    int intNumber = 10;
    double decimalNumber = intNumber;
    ```

    El valor entero _10_ se convierte implícitamente a un valor de punto flotante _10.0_ al asignarlo a la variable _decimalNumber_

  - **explícitas** (casting explícito): cuando se realiza una conversión de un tipo de dato de mayor rango a uno de menor rango. En este caso, es necesario especificar un operador de casting para indicar explícitamente la conversión

    ```
    double decimalNumber = 3.14;
    int intNumber = (int) decimalNumber;
    ```

    El valor de punto flotante _3.14_ se convierte explícitamente a un valor entero _3_ utilizando el operador de casting _(int)_

<br>

## Reglas de conversiones implícitas

- El tipo de destino tiene que ser de igual o mayor tamaño que el de origen
  - Excepciones
    - El tipo de origen es numérico (cualquier tipo) y el de destino es char:
      ```
      byte number = 5;
      char character = number; // error de ejecución
      ```
    - El tipo de destino es entero y el de origen es decimal
      ```
      float decimalNumber = 3.4f;
      int number = decimalNumber; // error de ejecución
      ```
- Cuando no sea posible conversión implícita, siempre se podrá utilizar realizar explícitamente:

  ```
  char character = (char)number;
  int number = (int)decimalNumber;
  ```

<br>

## Ejemplos de conversiones

- Conversiones correctas:

  ```
  char c = '@';
  int p = c; // 64 (ASCII)
  int number1 = 3450;
  byte number2 = (byte) number1; // 122
  ```

  El resultado es 122 porque los bits menos significativos del valor entero 3450 (00000000000000000011011010010 en binario) se ajustan dentro del rango de un byte, y esos bits forman el valor binario 01111010, que es 122

- Conversiones incorrectas:
  ```
  char character = '@';
  byte number = character; // error de ejecución
  boolean hasCar = false;
  int n = (int)hasCar; // error de ejecución
  ```
