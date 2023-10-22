# 5. Try con recursos

# 5.1. Cierre de objetos

- Algunos objetos utilizados para acceder a datos (_Connection_, _PrintStream_, _BufferedReader_, etc) deben ser cerrados después de su uso
- Estos objetos exponen el método _close()_ para realizar el cierre de los mismos
- Para garantizar el cierre, la llamada al método _close()_ se debe realizar en el bloque _finally_

  ```
  Connection connection = null;
  try {
       connection = DriverManager.getConnection(...);
       ...
  } catch(SQLException ex) {
       // tratamiento excepción
  } finally {
       if(connection != null) {
            try {
                 connection.close();
            } catch(SQLException ex) {
                 ...
            }
       }
  }
  ```

<br>

# 5.2. Interfaz AutoCloseable

- Interfaz del paquete _java.lang_ que incorpora un único método llamado _close()_
- Implementada desde Java 7 por las clases de objetos que gestionan recursos, como las de entrada y salida de _java.io_, o los objetos _JDBC_ de acceso a datos
- Objetivo: que sea el propio entorno de ejecución el que llame automáticamente al método _close()_ de cualquier objeto _AutoCloseable_, ahorrando código al programador

<br>

# 5.3. Try con recursos

- Variante del _try_ en la que se crean objetos autocerrables al principio del mismo
- Al salir del bloque _try_, tanto de forma natural como por una excepción, los objetos son cerrados automáticamente
- Sintaxis

  ```
  try(Tipo variable = new ...) {

  } catch(TipoException ex) {

  }
  ```

  ```
  Tipo variable = new ...;
  try(variable) {

  } catch(TipoException ex) {

  }
  ```

- Cuando se deja el _try_, automáticamente se hace una llamada implícita a _close()_

<br>

# 5.4. Cierre con try con recursos

- No se requiere bloque _finally_ para el cierre de objetos

  ```
  try(Connection connection = DriverManager.getConnection(...)){

  } catch(SQLException ex) {
       // tratamiento excepción
  }
  ```

- Cierre con múltiples objetos. Se cierra en orden inverso a su creación
  ```
  try(FileReader fr = new FileReader("data.txt");
       BufferedReader bf = new BufferedReader(fr)) {
            ...
  } catch(IOException ex) {
       // tratamiento excepción
  }
  // 1. bf.close()
  // 2. fr.close()
  ```
- La creación del objeto puede realizarse antes del _try_, indicando después la variable entre paréntesis. En este caso, la variable se trata como constante efectiva
  - Correcto
    ```
    Connection connection = DriverManager.getConnection(...);
    try(con) { ...}
    ```
  - Error de compilación
    ```
    Connection connection = DriverManager.getConnection(...);
    con = DriverManager.getConnection(...); // error
    try(connection) {
         ...
    }
    ```
- El método _close()_ es llamado nada más abandonar el bloque _try_, antes de entrar en un posible bolque _catch_ o _finally_
