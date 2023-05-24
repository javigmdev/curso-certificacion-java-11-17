# 1. Operador if y ternario

# 1.1 If

- Comprueba una condición de tipo boolean y ejecuta un bloque de sentencias si se cumple. Opcionalmente, se puede indicar bloque _else_

  ```
  if(condicion) {           if(a > 5) {
       // sentencias            a++;
  }                         }

  if(condicion) {           if(a % 2 == 0) {
       // sentencias            System.out.println("par");
  } else {                  } else {
       // sentencias            System.out.println("impar");
  }                         }
  ```

- Las llaves son obligatorias si el bloque contiene más de una instrucción
- Si la condición no es boolean, se produce error de compilación
  ```
  int number = 10;
  if(number) { // error de compilación
       ...
  }
  ```

<br>

# 1.2 Operador ternario

- Forma abreviada de la instrucción _if_
- _variable = expresión ? true : false_;
- Evalúa una expresión de tipo boolean, si el resultado es _true_, se devuelve el valor indicado después de la interrogación, si es _false_, devolverá el valor a continuación de los _:_
  ```
  int a = 3, b = 5, c;
  c = (a > b) ? a * a : b--;
  System.out.println(c); // 5, primero se asigna b a c y luego se decrementa la variable
  ```
