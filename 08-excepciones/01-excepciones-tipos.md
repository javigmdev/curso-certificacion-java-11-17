# 1. Excepciones

# 1.1. Excepciones y tipos

- Una excepción es una situación anómala que se puede producir durante la ejecución de un programa
- Se producen debido a fallos de programación. Son debidas a situaciones que escapan al control del programador (error en la introducción de un dato de usuario, corrupción de un fichero, etc)
- Un programa puede recuperarse de una excepción a través de una gestión de excepciones

<br>

# 1.2. Clases

```
                         Exception

RuntimeException         IOException         SQLException
   ArithmeticException
   NullPointerException
   IndexOutOfBoundsException
   ClassCastException
```

<br>

# 1.3. Clasificación

- En función de su naturalez, una excepción puede ser
  - _unchecked_: conocidas también como excepciones de sistema, son todas las excepciones subclases de _RuntimeException_. Se producen por errores de programación y no es obligatorio capturarla
  - _checked_: son lanzadas por métodos de clases del API Java, específicas de cada clase. Es obligatorio capturarlas

<br>

# 1.4. Excepciones unchecked

- _ArrayIndexOutOfBoundsException_: intento de acceder fuera de los límites de un array
  ```
  int[] data = new int[10];
  data[10] = 3; // arrayIndexOutOfBoundsException
  ```
- _NullPointerException_: acceso a métodos de un objeto con referencia a null

  ```
  class Test {
       String s; // inicializada a null

       public static void main(String[] args) {
            int n = s.length(); // NullPointerException
       }
  }
  ```

- _SecurityException_: producida por una violación de seguridad
- _ClassCastException_: error al realizar una conversión de tipos
  ```
  Object object = new String("34");
  Integer number = (Integer)object; // ClassCastException
  ```
- _ArithmeticException_: operación matemática incorrecta
  ```
  int n = 5/0; // ArithmeticException
  double r = 3/0.0; // ok
  ```
- _IllegalArgumentException_: un método recibe como parámetro un valor que no es válido
  ```
  Thread.sleep(-100); // IllegalArgumentException
  ```

<br>

# 1.5. Errores

- A diferencia de una excepción, un error es una situación que se produce en un programa de la que este no se puede recuperar, como un fallo en la _JVM_, falta de espacio en memoria, etc
- Sin embargo, los erroes también están representados por clases que heredan _Error_: _OUtOfMermoryError_, _StackOverFlowError_, _InternalError_, etc
