# 3. Coincidencia de patrones con instanceof

# 3.1. Operador instanceof

- Se utiliza para comprobar si un objeto es de un tipo específico
  ```
  Object object = new ...
  if(object instanceof String) {
       ...
  }
  ```
- Se puede utilizar con clases e interfaces
- Si no hay relación de herencia entre el tipo del objeto y la clase indicada como segundo operador, error de compilación

  ```
  String text = "my text";
  if(text instanceof Integer) { // error de compilación

  }
  ```

<br>

# 3.2. Nueva funcionalidad

- Desde Java 16 se puede utilizar _instanceof_ para asignar el objeto a una variable de tipo específico, sin realizar un _cast_
- Antes de Java 16
  ```
  Object object = new String("My text");
  if(object instanceof String) {
       String s = (String) object;
       System.out.println("Length:" + s.length());
  }
  ```
- Después de java 16, se convierte y se asigna directamente a la variable
  ```
  Object object = new String("My text");
  if(object instanceof String s) {
       System.out.println("Length: " + s.length())
  }
  ```
