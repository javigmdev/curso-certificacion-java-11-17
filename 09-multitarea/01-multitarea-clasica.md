# 1. Multitarea clásica

# 1.1. Definición

- Ejecución de varios procesos simultáneamente
- A diferencia de la ejecución secuencial, el gestor de multitarea de Java reparte el tiempo de CPU entre los procesos

<br>

# 1.2. Implementación de tareas

- Para implementar el código de las tareas existen dos posibilidades en la multitarea clásica
  - Extender de la clase _Thread_
  - Implementar la interfaz _Runnable_

<br>

# 1.3. Extensión de la clase Thread

- Proporciona el método _run()_, que debe ser sobrescrito para incluir el código de la tarea/tareas
- Se define una o varias subclases de Thread, dependiendo de si las tareas realizarán la misma función o diferente
  ```
  public class Task extends Thread {
       public void run() {
            // código de la tarea
       }
  }
  ```
- Para poner en ejecución concurrente las tareas, se llamará al método _start()_ de _Thread_, que invoca al gestor de multitarea de Java para que ponga los objetos en ejecución concurrente
  ```
  Task task1 = new Task();
  Task task2 = new Task();
  task1.start();
  task2.start();
  ```

<br>

# 1.4. Implementación de la interfaz Runnable

- Incluye el método _run()_ y permite a las clases que la implementan poder heredar otras clases
  ```
  public class Task implements Runnable {
       public void run() {
            // código de la tarea
       }
  }
  ```
- Para poner las tareas en ejecución, se crearán instancias de _Thread_ a partir del objeto _Runnable_

  ```
  Task task = new Task();
  Thread thread1 = new Thread(task);
  Thread thread2 = new Thread(task);
  thread1.start();
  thread2.start();
  ```

<br>

# 1.5. Condiciones de carrera

- Se da cuando dos o más hilos acceden a un recurso compartido
- Si un hilo debe completar un proceso con el recurso (sección crítica) antes de que el otro lo manipule, se puede producir una situación anómala
- Solución: sincronización

<br>

# 1.6. Sincronización

- Consiste en bloquear el acceso a un bloque de código a otros hilos, hasta que el hilo que entró primero complete su ejecución
- Se utiliza la palabra _synchronized_ para deliminar el bloque sincronizado
- Cuando un hilo entra en el bloque sincronizado, adquiere el monitor del objeto y no lo suelta hasta completarlo
  ```
  // obj: recurso compartido
  synchronized(obj) {
       int value = obj.getValue();
       value++;
       obj.setValue(value);
  }
  ```
- La palabra _synchronized_ se puede utilizar en la definición de un método para sincronizar el método completo
