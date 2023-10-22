# 3. Lanzamiento y propagación de excepciones

# 3.1. Propagación

- Si un método que debe capturar una excepción no desea hacerlo, puede propagarla al lugar de llamada al método
- Se debe declarar la excepción en la cabecera del método con la instrucción _throws_
  ```
  method() throws IOException {
       BufferedReader bf = new ...;
       String s = bf.readLine();
  }
  // Si se produce la excepción, se propaga al punto de llamada a method(), que será donde haya que capturarla
  ```

<br>

# 3.2. Lanzamiento

- Desde un método de una clase se puede lanzar una excepción para que sea capturada desde el punto de llamada al método
- Para lanzar una excepción se utiliza la instrucción _throw objeto_exception_
  ```
  method() throws IOException {
       ...
       // creación y lanzamiento de la excepción
       throw new IOException();
  }
  ```
- Si se lanza una excepción _checked_, el compilador obliga a declararla con throws para que se propague, si es _RuntimeException_ no es necesario declararla
