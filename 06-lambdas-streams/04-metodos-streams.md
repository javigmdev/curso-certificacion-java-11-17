# 4. Métodos Streams

# 4.1. Conteo y procesado (finales)

- _long count()_: devuelve el número de elementos de un _Stream_

  ```
  Stream st = Stream.of(2,5,7,3,6,2,3);
  // indica el total de elementos
  System.out.println(st.count()); // 7
  ```

- _void forEach(Consumer<? super T> action)_: realiza una acción para cada elemento del _stream_

  ```
  Stream st = Stream.of(2,5,8,3,6,2,10);
  // muestra todos los elementos
  st.forEach(number -> System.out.println(number));

  System.out.println(st.count()); // error: tras llamar a un método, el stream se cierra y no puede volver a utilizarse
  ```

<br>

# 4.2. Extracción de datos (intermedios)

- _Stream<T> distinct()_: devuelve un _Stream_ eliminando los elementos duplicados, según aplicación de _equals()_
  ```
  Stream<Integer> st = Stream.of(2,5,3,3,6,2,4);
  // Cuenta el total de números no repetidos
  System.out.println(st.distinct().count()); // 5
  ```
- _Stream<T> limit(long n)_: devuelve un nuevo _Stream_ con los _n_ primeros elementos del mismo

  ```
  Stream<Integer> st = Stream.of(2,5,8,3,6,2,10);
  // Devuelve un Stream formado por 2,5 y 8
  Stream<Interger> st2 = st.limit(3);
  ```

- _Stream<T> skip(long n)_: devuelve un nuevo _Stream_, saltándose los _n_ primeros elementos

<br>

# 4.3. Comprobacions (finales)

- _boolean anyMatch(Predicat<? super T> predicate)_: devuelve _true_ si algún elemento de _Stream_ cumple con la condición del predicado
  ```
  Stream st = Stream.of(2,5,7,3,6,2,3);
  // indica si alguno es mayor de 5
  System.out.println("any > 5?" + st.anyMatch(n -> n > 5)); // true
  ```
- _boolean allMatch(Predicate<? super T> predicate)_: devuelve _true_ si todos cumplen con la condición del predicado
- _boolean noneMatch(Predicate<? super T> predicate)_: devuelve _true_ si ninguno cumple con la condición del predicado

<br>

# 4.4. Filtrado (intermedios)

- _Stream<T> filter(Predicate<? super T> predicate)_: aplica un filtro sobre el _Stream_, devolviendo un nuevo _Stream_ con los elementos que cumplen el predicado
  ```
  Stream<Integer> st = Stream.of(7,5,7,3,6,2,3,8,5);
  // cuenta el total de números mayores de 3 no duplicados
  System.out.println(st.distinct().filter(s -> s > 3).count());
                         ------------------------------------
                                     pipeline
  ```

<br>

# 4.5. Búsqueda (finales)

- _Optional<T> findFirst()_: devuelve el primer elemento del _Stream_, o un _Optional_ vacío si no hay nada
  ```
  Stream<Integer> st = Stream.of(11,5,8,3,9);
  // devuelve el primer par
  Optional<Integer> op = st
                 .filter(s -> s % 2 == 0)
                 .findFirst();
  if(op.isPresent()) {
       System.out.println(op.get());
  }
  ```
- _Optional<T> findAny()_: devuelve cualquiera de los elementos del _Stream_. Normalmente, el primero

<br>

# 4.6. La clase Optional<T>

- Encapsula resultados de una operación final de un _Stream_
- Podemos utilizar los siguientes métodos para manipularlo
  - _T get()_: devuelve el valorencapsulado. Si no hay ningún valor, lanza una _NoSuchElementException_
  - _T orElse(T other)_: devuelve el valor encapsulado. Si no hay ninguno, entonces devuelve el valor pasado como parámetro
  - _boolean isPresent()_: permite comprobar si contiene o no algún valor
- Existen las variantes _OptionalInt_ y _OptionalDouble_ que encapsulan tipos primitivos

<br>

# 4.7. Obtención de extremos (finales)

- _Optional<T> max(Comparator<? super T> comparator)_: devuelve el mayor de los elementos, según el criterio de comparación del objeto _Comparator_:
  ```
  Stream<Integer> nums = Stream.of(20,5,8,3,9);
  // muestra el mayor de los números del Stream
  Optional<Integer> op = nums.max((a,b) -> a - b);
  System.out.prinln("mayor:" + op.get());
  ```
- _Optional<T> mix(Comparator<? super T> comparator)_: Operación contraria a max

<br>

# 4.8. Transformación (intermedios)

- _Stream<R> map(Function<? super T, ? extends R> mapper)_: transforma cada elemento del _Stream_ en otro según el criterio definido por el objeto _Function_ que se le pasa como parámetro:
  ```
  Stream<String> st = Stream.of("Mark", "John", "Tom");
  // genera un Stream con los nombres en mayúsculas
  Stream<String> st2 = st.map(s -> s.toUpperCase());
  ```
- _IntStream mapToInt(ToIntFunction<? super T> mapper)_: aplica una función a cada elemento del _Stream_ que genera un _int_ de cada elemento. El resultado se devuelve como _IntStream_
  ```
  Stream<String> st = Stream.of("Mark", "John", "Tom");
  // muestra la suma de todos los caracteres de todos los nombres
  System.out.prinln(st
                 .mapToInt(s -> s.length())
                 .sum());
  ```

<br>

# 4.9. Stream de tipos primitivos

- Las interfaces _IntStream_, _DoubleStream_ y _LongStream_, cuyos objetos son obtenidos mediante los métodos _mapToInt_, _mapToDouble_ y _mapToLong_, respectivamente, proporcionan los siguientes métodos de cálculo
  - _int sum()_: método final que devuelve la suma de todos los elementos del stream. En _DoubleStream_ y _LongStream_ el tipo de devolución es double y long, respectivamente
  - _OptionalDouble average()_: método final que devuelve la media encapsulada en un _OptionalDouble_ en los tres casos
  - _OptionalInt max()_ y _min()_: devuelven el mayor y menor de los números, respectivamente. En _DoubleStream_ y _LongStream_ el tipo de devolución es _OptionalDouble_ y _OptionalLong_, respectivamente

<br>

# 4.10. Transformación y aplanamiento (intermedios)

- _Stream<R> flatMap(Function<T, Stream<R>> mapper)_: devuelve un nuevo _Stream_, resultante de unir los _Streams_ generados por la aplicación de una función sobre cada elemento
  - Ejemplo: partiendo de una lista de listas de nombres, calcular cuantos nombres en total tienen más de 4 caracteres
    ```
    List<List<String>> data = Arrays.asList(Arrays.asList("Tom", "Jack", "William"), Arrays.asList("Lisa", "Mary", "David"));
    System.out.println(data.stream()
                             .flatMap(l -> l.stream().map(s -> s.length()))
                             .filter(n -> n > 4)
                             .count());
    ```
