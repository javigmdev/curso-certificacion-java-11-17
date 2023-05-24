# 2. Switch

# 2.1. Instrucción switch

- Evalúa una expresión cuyo resultado debe ser entera (hasta que a partir de la versión 7 de java se permite _String_). Se ejecutarán diferentes bloques de sentencias en función de los posibles resultados

  ```
  switch(expresion) {           switch(code) {
       case valor1:                  case 200:
            // sentencia                  System.out.println("ok");
            break;                        break;
       case valor2:                  case 201:
            // sentencia                  System.out.println("created");
            break;                        break;
       default:                      default:
            // sentencias                 System.out.println("not found");
  }                              }
  ```

- Si el resultado de la expresión coincide con uno de los valores indicados en los _case_, ejecutará el bloque correspondiente de sentencias, si no, entrará en el bloque _default_

- La instrucción _break_ al final de cada bloque _case_ es opcional. Si no se indica, el programa entrará en el siguiente bloque
  ```
  int number = 10;
  switch(number) {
       case 10:
            System.out.println("Number 10");
       default:
            System.out.println("Without value");
  }
  // Resultado: Number 10
  //            Without value
  ```

<br>

# 2.2. Valores de los case

- Los valores de los _case_ deben ser literales o constantes enteras int, o convertibles implícitamente en int

  ```
  int p = 5;
  final int k = 30;
  int n = 3;
  switch(p) {
       case 10:  // ok, literal int
       case k:   // ok, constante
       case p:   // error de compilación, no es una constante
       case '@': // ok, char convertible implícitamente a int
  }
  ```

  <br>

# 2.3. Bloque default

- Es opcional
- No es obligatorio ponerlo al final
  ```
  int p = 5;
  switch(p) {
       case 10:
            System.out.println("Number 10");
       default:
            System.out.println("Default");
       case 2:
            System.out.println("Number 2");
  }
  // Resultado: Default
                Number 2
  ```

<br>

# 2.4. Switch con valores String

- Desde la versión 7 de java, se permite hacer _switch_ con expresiones cuyo resultado sea un _String_
  ```
  String name = "Tom";
  final String HELLO = "hello";
  switch(name) {
       case "uno": // ok
       case s: // ok, constante
       case 10: // error de compilación
  }
  ```
- Si la expresión es evaluada como _String_, no se admiten valores enteros en los _case_ y viceversa
