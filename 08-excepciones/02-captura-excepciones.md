# 2. Captura de excepciones

# 2.1. Bloques try catch

- Las excepciones se capturan en un programa java a través de los bloques _try catch_

  ```
  try  {
       // instrucciones
  } catch(TipoExcepcion1 ex) {
       // tratamiento excepción
  } catch(TipoExcepcion2 ex) {
       // tratamiento excepción
  }
  ```

- No puede haber ninguna instrucción entre los bloques _try catch_
  ```
  try { ... }
  System.out.println("hello"); // error de compilación
  catch(...) {}
  ```
- Si se capturan varios tipos de excepciones que tienen relación de herencia entre ellas, los _catch_ de las subclases deben ir antes que los de las super clases

  - Compilación correcta
    ```
    catch(FileNotFoundException ex) {
         ...
    }
    catch(IOException ex) {
         ...
    }
    ```
  - Error de compilación
    ```
    catch(RuntimeException ex) {
         ...
    }
    catch(ArithmeticException ex) {
         ...
    }
    ```

<br>

# 2.2. Multicatch

- Si los _catch_ de varis excepciones van a realizar la misma tarea, podemos agruparlos en un _multicatch_

  ```
  catch(IOException ex) {
       System.out.println("error");
  }
  catch(SQLException ex) {
       System.out.println("error");
  }

  =

  catch(IOExcepion | SQLException ex) {
       System.out.println("error");
  }
  ```

- Las exceptiones del _multicatch_ no pueden tener relación de herencia, se produciría un error de compilación

<br>

# 2.3. Métodos

- Todas las clases de excepción heredan los siguientes métodos de _Exception_
  - _String getMessage()_: devuelve una cadena de caracteres con un mensaje de error asociado a la excepción
  - _void printStackTrace()_: genera un volcado de error que es enviado a la consola

<br>

# 2.4. Bloque finally

- Se ejecuta siempre, tanto si se produce la excepción como si no

  ```
  try {
       int n = 4/0;
  } catch(ArithmeticException ex)  {
       System.out.println("Error");
       return;
  } finally {
       System.out.println("Final");
  }

  // Error
  // Final
  ```

- Si se produce una excepción y no hay ningún _catch_ para capturarla, se propagará la excepción al punto de llamada, pero antes ejecutará el bloque _finally_
