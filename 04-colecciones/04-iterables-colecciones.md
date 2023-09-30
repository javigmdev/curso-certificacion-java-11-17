# 4. Iterables y colecciones

# 4.1. Iterables

- Un iterable es un objeto que puede ser recorrido mediatne un enhaced for (for each)
- Los objetos iterables implementan la interfaz _java.lang.Iterable_, que entre sus métodos más destacados está

  ```
     Iterator<T> iterator() // devuelve un objeto Iterator
  ```

- Las litas y los conjuntos son ejemplos de objetos Iterables

<br>

# 4.2. Interfaz Iterator<E>

- Objeto tipo cursor que permite recorrer el contenido de un iterable
- Entre sus métodos destacan

  - boolean hasNext(): indica si hay más elementos que recorrer
  - T next(): se desplaza al siguiente elemento y devuelve una referencia al mismo

  ```
  Iterator<Integer> iterator = list.iterator();
  while(iterator.hasNext()) {
       System.out.println(iterator.next());
  }
  ```

<br>

# 4.3. Collection

- Objeto que contiene una agrupación de datos
- La interfaz _java.util.Collection_ representa la interfaz raíz de las colecciones Java
- Hereda _Iterable_ y es heredada por listas y conjuntos, proporcionando gran parte de los métodos de estas colecciones (_add_, _contains_, _remove_, _removeif_, _size_ o _stream_)
