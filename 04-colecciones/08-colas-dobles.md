# 8. Colas dobles

# 8.1. Características

- Permite añadir elementos por ambos extremos, pudiendo comportarse como cola o como pila
- Implementan la interfaz _Deque_, que a su vez hereda _Queue_
- Como el resto de colecciones, son de tipo genérico
- La principal clase de _Deque_ es _ArrayDeque_

<br>

# 8.2. Clases e interfaces

               (interface)
                 Iterable
                    ↑
                (interface)
                 Collection
                    ↑
                (interface)
                   Queue
                      ↑
                (interface)
                   Deque
          ↗                   ↖
     ArrayDeque              LinkedList

<br>

# 8.3. Creación

- Se crearán como instancias de _ArrayDeque_ o de cualquiera de las otras clases que implementan la interfaz
  ```
  Deque<String> names = new ArrayDeque<>();
  Deque<Integer> numbers = new LinkedList<>();
  ```

<br>

# 8.4. Métodos Deque

- _boolean add(T data)_: añade el dato al final del _Deque_, comportándose como una cola (el primero en entrar será el primero en salir)
  ```
  Deque<String> cola = new ArrayDeque<>();
  cola.add("Mark");
  cola.add("Mikel");
  ```
- _boolean push(T data)_: añade el elemento a la cabecera del _Deque_, comportándose como una pila (último en entrar, primero en salir)

  ```
  Deque<String> cola = new ArrayDeque<>();
  cola.push("Mark");
  cola.push("Mikel");
  ```

- _E poll()_: extrae y elimina el elemento de la cabecera
  ```
  System.out.println(cola.poll()); // Mark
  System.out.println(pila.poll()); // Mikel
  ```
- _E remove()_: extrae y elimina el elemento de la cabecera. Funciona igual que _poll()_
  ```
  Deque<String> cola = new ArrayDeque<>();
  cola.add("Mark");
  cola.add("Mikel");
  System.out.println(cola.remove()); // Mark
  ```
- _E peek()_, _E element()_: devuelven el elemento de cabecera, pero sin eliminarlo
- _int size()_: indica el tamaño de la colección

<br>

# 8.5. Recorrido

- Se puede recorrer mediante un _for each_. Recupera cada elemento desde la cabecera hasta el final
  ```
  for(String name : deque) {
       System.out.println(name);
  }
  ```
- Método _forEach_ (ver en apartado lambdas)
