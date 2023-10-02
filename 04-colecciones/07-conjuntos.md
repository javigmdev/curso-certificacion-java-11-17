# 7. Conjuntos

# 7.1. Características

- Los elementos no tienen posición ni clave asociada, cada elemento es único, no se puede repetir
- Emplea internamente los métodos equal y hashcode para determinar la igualdad de objetos
- Los conjuntos implementan la interfaz _Set_, que es de tipo genérico
- La principal clase de conjuntos es _HashSet_

<br>

# 7.2. Clases e interfaces

               (interface)
                 Iterable
                    ↑
                (interface)
                 Collection
                    ↑
                (interface)
                   Set
          ↗                   ↖
     HashSet                TreeSet

<br>

# 7.3. Creación

- Como instancias de _HashSet_
  ```
  Set<String> names = new HashSet<>();
  ```
- Mediante método de factoría de _Set_ (Inmutable)
  ```
  Set<String> names = Set.of("Mary", "Tom", "Elisabeth");
  ```
- Mediante el método _copyOf_ de _Set_ (Inmutable)
  ```
  Set<String> copy = Set.copyOf(names);
  ```

<br>

# 7.4. Métodos HashSet

- _boolean add(T data)_: añade el dato a la colección si no está presente. Devuelve _true_ si lo ha podido añadir
  ```
  HashSet<String> days = new HashSet<>();
  days.add("monday");
  days.add("tuesday");
  days.add("monday"); // no se añade
  ```
- _boolean remove(T data)_: elimina el elemento si se encuentra en la colección
- _int size()_: devuelve el tamaño de la colección
- _boolean contains(Object object)_: devuelve _true_ si el objeto existe en la colección

<br>

# 7.5. Recorrido

- Un conjunto puede ser recorrido con un _for each_
  ```
  for(String day : days) {
       System.out.println(day);
  }
  ```
- Método _forEach_ (ver en apartado lambdas)
