# 2. Compilación y ejecución de módulos

# 2.1. Estructura de ejemplo

- Partimos de la siguiente estructura de módulos y clases de ejemplo

  ```
  raiz

       - module1
                      -module-info.java   --> com.module1
                      -Test.java

       - module2      -module-info.java   --> com.module2
                      -Operation.java
  ```

- com.module2

  - Contiene una clase que va a ser utilizada desde otro módulo (_com.module1_)

    - Oper.java

      ```
      package com.operations;

      public class Operation {
           public int sum(int number1, int number2) {
                return number1 + number2;
           }

           public int multiply(int number2, int number2) {
                return number1 * number2;
           }

      }
      ```

    - module-injo.java
      ```
      module com.module2 {
           exports com.operations;
      }
      ```

- com.module1

  - Incluye una clase que hace uso del paquete expuesto por el módulo _com.module2_

    - Test.java

      ```
      package com.client;
      import com.operations.Operation;

      public class Test {
           public static void main(String[] args) {
                Operation operation = new Operation();
                System.out.println(operation.sum(2,9));
                System.out.println(operation.sum(2,9));
           }
      }
      ```

    - module-info.java
      ```
      module com.module1 {
           requires com.module2;
      }
      ```

<br>

# 2.2. Compilación de un módulo

- Desde el directorio raíz, el que contiene al módulo a compilar

  ```
  javac --module-path dir_modulo_dep -d dir_destino ficheros

  dir_modulo_dep: dirección módulos de los que depende
  ```

- Ejemplo compilación _module1_ y _module2_ desde raiz
  - Módulo 2: no necesita module-path ya que no depende de ningún otro módulo
    ```
    javac -d module2 module2/*.java
    ```
  - Módulo 1: el módulo del que depende cuelga del directorio _module2_
    ```
    javac --module-path module2 -d module1 module1/*.java
    ```

<br>

# 2.3. Ejecución de un módulo

- Desde el directorio raíz, el que contiene al módulo a ejecutar

  ```
  java --module-path dir_modulos --module nombre_modulo/loc_clase

  dir_modulos: path de todos los módulos separados por ;
  loc_clase: nombre completo de la clase a ejecutar
  ```

- Ejemplo ejecución _module1_:

  ```
  java --module-path module1;module2 --module com.module1/com.client.Test

  java --module-path . --module com.module1/com.client.Test
  ```

<br>

# 2.4. Abreviaturas

- La siguiente tabla muestra las abreviaturas que se pueden utilizar para algunos de los parámetros de los comandos _java_ y _javac_

  | parámetro     | abreviatura |
  | ------------- | ----------- |
  | --module-path | -p          |
  | --module      | -m          |

- La compilación y ejecución del módulo _module1_ podría realizarse
  ```
  javac -p module2 -d module1 module1/*.java
  java -p . -m module1/com.client.Test
  ```
