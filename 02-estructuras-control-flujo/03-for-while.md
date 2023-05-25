# 3. For y while

# 3.1. For

- Ejecuta un grupo de instrucciones un número determinado de veces
  ```
  for(inicializacion : condicion : increment) {
       // instrucciones
  }
  ```
- Desde que la variable toma el valor de inicialización hasta que deje de cumplirse, se ejecutará el bloque de instrucciones

  ```
  for(int i = 1; i < 10 ; i++) {
       System.out.println(i); // del 1 al 9
  }
  ```

- Las llaves son obligatorias si hay más de una instrucción
- Las tres instrucciones de control son opcionales
  ```
  int i = 1;
  for( ;i < 10; ) {
       System.out.println(i); // del 1 al 10
       i++;
  }
  ```
- Si no se indicase instrucción de control tendríamos bucle infinito
  -Las instrucciones de control pueden contener más de una sentencia, separadas por una coma
  ```
  for(int = 0, b = 10; a < b ; a++, b--) {}
  ```

<br>

# 3.2. Enhanced for

- Se utiliza para el recorrido, en modo lectura, de arrays y colecciones
  ```
  for(tipo variable : array) {
       // instrucciones
  }
  ```
- La variable de control va pasando por todas las posiciones del array, NO es un índice

  ```
  int [] nums = {4,8,1,5};
  for(int n : nums) {
       System.out.println(n); // 4, 8, 1, 5
  }
  ```

<br>

# 3.3. While

- Ejecuta un grupo de instrucciones mientras se cumpla una condición (resultado sea _true_)
- La condición puede evaluarse al principio, o después de ejecutar el bloque de instrucciones
  ```
  while(condicion) {          do {
     // instrucciones            // instrucciones
  }                           } while(condicion);
  ```
- Las acciones dentro del bloque provocarán que en algún momento la condición deje de cumplirse, sino bucle infinito
  ```
  int n = 0; s = 0;             int n = 0;
  while(s < 1000) {             do {
       s += n++;                     n = readNumber();
  }                             } while(n < 0);
  ```
