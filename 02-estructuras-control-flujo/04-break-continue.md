# 4. Break y continue

# 4.1. Break

- Provoca salida forzada, abandonando el bucle
- Puede utilizarse tanto en for como en while
  ```
  int n = readNumber();
  int s = 0;
  for(int i = 0; i < n ; i++) {
       s += i;
       if(s > 100) {
            break;
       }
  }
  // Si se ejecuta el break, se sale del for
  ```

<br>

# 4.2. Continue

- Provoca salida forzada, pasando a la siguiente interación
- Puede utilizarse tanto en for como en while
  ```
  for(int i k= 1; i < 10 ; i++) {
       if(i == 5)
            continue;
       System.out.println(i);
  }
  // muestra los números del 1 al 10, excepto el 5
  ```

<br>

# 4.3. Bucles etiquetados

- Es posible asignar una etiqueta a una instrucción _for_ o _while_
- En bucles anidados, se permite indicar a las instrucciones _break_ o _continue_ el bucle que se quiere abandonar
  ```
  externo: for(..) {
       while(..){
            break externo; // sale del bucle principal
       }
  }
  ```
- Si no se indica etiqueta después de _break_ o _continue_, afectará al bucle mas interno
