# 4. Inferencia de tipos

# 4.1. Var

- Permite declarar variables locales sin indicar explícitamente el tipo (incorporado desde la versión 10)
  ```
  var num = 100; // entero
  var numbers = new ArrayList<Integer>(); // lista de enteros
  ```
- El tipo es inferido por el compilador a partir del valor asignado a la variable
- Simplifica la estructura de código.
- Ni mejora ni empeora el rendimiento de la aplicación
- Sólo es permitido con variables locales

  ```
  class Test {
       var number = 100; // error de compilación

       void print() {
            var response = "OK";
       }
  }
  ```

- Es obligatorio asignar explícitamente un valor a la variable, valor que no puede ser null

  ```
  var data; // error de compilación
  var number = null; // error de compilación
  ```

- No es posible utilizar inferencia de tipos en declaraciones múltiples
  ```
  var a,c = 10; // incorrecto
  var b = 5, x = 30; // incorrecto
  ```
- Se puede utilizar inferencia de tipos en bucles de tipo for:

  ```
  for(var i = 0; i < 10; i++) {}

  for(var user: users) {}
  ```

- En arrays, no puede utilizarse con inicialización abreviada
  ```
  var numbers = {5,9,10}; // incorrecto
  var numbers = new int[]{5,9,10}; // correcto
  ```
