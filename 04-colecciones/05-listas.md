# 5. Listas

# 5.1. Introducción

- Una colección es una agrupación de objetos sin tamaño fijo
- Se puede añadir y eliminar objetos de una colección dinámicamente
- Para gestionar colecciones disponemos de clases e interfaces específicas en _java.util_
- Tipos:
  - Listas
  - Tablas
  - Conjuntos
- Cada elemento tiene una posición asociada a partir del orden de llegada, siendo 0 la posición del primero
- Las listas implementan la interfaz _List_, que a su vez implementa _Collection_
- Son colecciones de tipo genérico (preparadas para admitir cualquier objeto Java)
- La princpal clase de collección es _ArrayList_

<br>

# 5.2. Clases e intorefaces

                (interface)
                 Iterable
                    ↑
                (interface)
                 Collection
                    ↑
                (interface)
                   List
          ↗         ↑          ↖
      ArrayList   Vector    LinkedList

<br>

# 5.3. Creación

- Como instancias de _ArrayList_
  ```
  List<Integer> numbers = new ArrayList<>();
  ```
- A partir del método _asList_ de _Arrays_ (Lista de tamaño **fijo**, no admite inserción ni eliminación)
  ```
  List<Integer> numbers = Arrays.asList(6,2,4,10,21);
  ```
- Mediante método de factoría de _List_ (**Inmutables**, no admiten la eliminación, modificación e inserción de elmentos, ni valores null)
  ```
  List<Integer> numbers = List.of(40,29,11,28);
  ```
- Mediante el método _copyOf_ de _List_ (**Inmutables**, no admiten la eliminación, modificación e inserción de elmentos, ni valores null)
  ```
  List<Integer> copy = List.copyOf(numbers);
  ```

<br>

# 5.4. Principales métodos

- _boolean add(T data)_: añade el dato a la colección y lo coloca al final de la misma. T representa el tipo indicado al crear el objeto de colección
  ```
  ArrayList<String> names = new ArrayList<>();
  names.add("Mery"); // Posición 0
  names.add("Tom");  // Posición 1
  ```
- _boolean add(int position, T data)_: añade el elemento en la posición indicada, desplazando hacia adelante los que se encuentren en dicha posición
  ```
  names.add("Mikel", 1);  // Desplaza a Tom a la posición 2
  ```
- _T set(int position, T data)_: sustituye el elemento existente en la posición indicada por el nuevo suministrado como parámetro. Devuelve el elemento sustituido
  ```
  name.set(0, "Angela"); // Sustituye Mery por Angela
  ```
- _int size()_: devuelve el total de elementos de la colección
- _T get(int position)_: devuelve el elemento que ocupa la posición indicada. Si la posición es menor que 0 o mayor o igual que _size()_, se producirá una excepción

<br>

# 5.5. Recorrido

- Se puede recorrer con un bucle _for_ estándar
  ```
  for(int i = 0; i < names.size(); i++) {
     System.out.println(names.get(i));
  }
  ```
- También mediante un for each
  ```
  for(String name: names) {
     System.out.println(name);
  }
  ```
- Método _forEach_ (ver en apartado lambdas)
