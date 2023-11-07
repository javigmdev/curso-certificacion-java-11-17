# 1. Novedades en la instrucción switch

# 1.1. Múltiples valores en case

- Desde la versión Java 14, la cláusula _case_ de un _switch_, puede incluir varios valores, separados por _","_

  ```
  int res = 3;
  switch(res) {
       case 1:
            System.out.println("Very low value");
            break;
       case 2,3,4:
            System.out.println("Lower that normal value");
            break;
  }
  ```

- Al igual que en un _case_ simple, los valores del _case_ múltiple deben ser literales, constantes o tipos enumerados

<br>

# 1.2. Expresiones switch

- Desde Java 14, es posible utilizar la instrucción _switch_ para devolver un resultado en una expresión
  ```
  variable = switch(operation){...};
  ```
- Ejemplo:

  ```
  int grade = 6;
  String result = switch(grade) {
       case 1,2,3,4: -> "Fail";
       case 5,6: -> "Pass";
       case 7,8: -> "Good";
       case 9,10: -> "Excellent";
       default -> "Invalid";
  };
  System.out.println(result); // Pass
  ```

- Se utiliza _->_ en lugar de _:_ para indicar las instrucciones de cada bloque _case_
- Si hay más de una instrucción, se delimita por llaves y el valor se devuelve mediante la instrucción _yield_
  ```
  case 5 -> {
       int p = 20 * 2;
       yield p;
  }
  ```
- No se utiliza la instrucción _break_
- Es obligatorio el uso de _default_, salvo que estén contemplados todos los posibles valores en los _case_
