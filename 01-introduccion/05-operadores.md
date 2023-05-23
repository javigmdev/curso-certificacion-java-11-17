# 5. Operadores

# 5.1. Aritméticos

- Se emplean con tipos numéricos primitivos para realizar operaciones aritméticas en un programa: +,-,\*,/,%,++,--
  ```
  int a = 3;
  a++; // equivale a (int)(a+1)
  int x = 6, y = 10, z;
  z = y / x; // el resultado es 1, la división entre enteros es un entero
  ```
- Los operadores ++ y -- se aplican con tipos numéricos y pueden ir delante o detrás de la variable

  ```
  int a = 3, b;
  b = ++a; // b toma el valor 4

  int a = 3, b;
  b = a++; // b toma el valor 3 (primero asigna y luego incrementa)
  ```

<br>

# 5.2. Asignación

- El operador = asinga el resultado de una expresión a una variable
- Los operadores +=, -=, \*/, /=, %=, realizan la operación entre un dato y la variable y asignan el resultado a la variable
  ```
  int a = 3;
  a += 10; // equivale a a=a+10;
  byte b = 10;
  b += 5; // equivale a b=(byte)(b+5)
  b = b + 5; // error de compilación: una operación con int (los literales enteros son int) siempre da como resultado int
  ```

<br>

# 5.3. Condicionales

- Evalúan dos operadores y dan como resultado un valor boolean: <,>,<=,>=, ==, !=
- Salvo ==, que puede utilizarse con objetos, los demás solo pueden utilizar con tipos primitivos y entre tipos compatibles
  ```
  int a = 3;
  double c = 9.5;
  boolean x = false;
  if(a > c) // ok
  if(a < x) // error de compilación
  ```

<br>

# 5.4. Lógicos

- Evalúan expresiones de tipo boolean: &&, || y !
  ```
  int a = 3;
  int c = 9;
  int n = 0;
  if(a > n && a < c) // true
  if(!(n == 0)) // false
  ```

<br>

# 5.5. Otros

- **new**: creación de objetos a partir de la clase
  ```
  ArrayList list = new ArrayList();
  ```
- **instanceof**: comprueba si un objeto es de un tipo dado
  ```
  String name = "Jack";
  System.out.println(name instanceof String); // true
  ```
