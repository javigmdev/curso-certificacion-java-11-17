# 8. Clases anidadas

# 8.1. Definición y tipos

- Clases que se definen dentro de otras clases
- Se pueden dar cuatro situaciones
  - Clases estándares
  - Clases estáticas
  - Clases locales a métodos
  - Clases anónimas

<br>

# 8.2. Clases estándares

- Se definen como un miembro más de otra clase
  ```
  class External {
       class Internal {
            // métodos y atributos
       }
  }
  ```
- Para instanciar una clase interna se necesita un objeto de la externa

  ```
  External external = new External();
  External.Internal internal = external.new Internal();

  ```

- Una clase interna puede definirse con cualquier modificador de acceso, incluso _private_

<br>

# 8.3. Clases estáticas

- Se definen como un miembro estático de la clase externa
  ```
  class External {
       static class Internal {
            // métodos y atributos
       }
  }
  ```
- Para instanciar una clase interna estática no se necesita un objeto de la externa
  ```
  External.Internal internal = new External.internal();
  ```
- La clase estática interna, solo puede acceder a otros miembros estáticos de la clase externa

<br>

# 8.4. Clases locales a método

- Se definen dentro de un método de la clase externa

  ```
  class External {
     void method() {
          class Local {
               // métodos y atributos
          }
     }
  }
  ```

- Únicamente pueden ser instanciadas desde el interior del método al que pertenecen, y no tienen acceso a otras variables locales del método, salvo que sean finales

<br>

# 8.5. Clases anónimas

- Son clases que no tienen nombre. Heredan una clase existente o implementan una interfaz
- Se definen al vuelo, en la misma instrucción de instanciación

  ```
  Runnable runnable = new Runnable() {
       public void run() {
       }
  }
  ```
