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

# 4.4. Filtrado (intermedio)

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

<br>

# 4.11. Procesamiento intermedio (intermedio)

- _Stream<T> peek(Consumer<? super T> proceso)_: aplica el consumer a cada elemento del _Stream_, devolviendo un nuevo stream idéntico para continuar con la manipulación de los elementos

  ```
  Stream<Integer> nums = Stream.of(20,5,8,3,9);
  // muestra los pares y el total de estos
  System.out.println("total: " + nums
                           .filter(n -> n % 2 == 0)
                           .peek(n -> System.out.println("par: " + n))
                           .count());

  // par: 20
  // par: 8
  // total: 2
  ```

<br>

# 4.12. Ordenación (intermedios)

- _Stream<T> sorted()_: devuelve un _Stream_ con los elementos ordenados, según el orden natural de los mismos
- _Stream<T> sorted(Comparator<? super T> comparator)_: devuelve un _Stream_ con los elementos ordenados, según el criterio de comparación especificado

  ```
  Stream<String> st = Stream.of("house", "ball", "lamp", "disc");
  // muestra los nombres ordenados por número de caracteres
  st.sorted((a,b) -> a.length() - b.length())
       .forEach(s -> System.out.println(s));
  ```

  ```
  Stream<Person> st = Stream.of(new Person("Jack", 34), new Person("Mery", 28));
  // muestra los nombres de las personas, ordenadas por edad
  st.sorted(Comparator.comparing(p -> p.getAge()))
       .forEach(p -> System.out.println(p.getName()));
  ```

<br>

# 4.13. Reducción (final)

- _Optional<T> reduce(BinaryOperator<T> accumulator)_: realiza la reducción de los elementos del stream a un único valor, utilizando la función proporcionada como parámetro
  ```
  Stream<Integer> nums = Stream.of(20, 5, 8, 3, 9);
  // Calcula la suma de todos los elementos del Stream
  System.out.println(nums
                 .reduce((a, b) -> a + b)
                 .get());
  ```

# 4.14. Reducción a colección (final)

- _R collect(Collector<? super T, A, R> collector)_: devuelve un _List_, _Map_ o _Set_ con los datos del _Stream_, en función de la implementación de _Collector_ proporcionada
  ```
  Stream<Integer> nums = Stream.of(20,5,8,5,3,3,9);
  // Genera una lista con los elementos del Stream sin duplicados
  List<Integer> list = nums.distinct().collect(Collectors.toList());
  ```
  ```
   Stream<Person> st = Stream.of(new Person("Jack", 34), new Person("Mery", 28));
   // genera una tabla con los datos de las personas, utilizando la edad como clave y el nombre como valor
   Map<Integer, String> map = st.collect(Collectors.toMap(p -> p.getAge(), p -> p.getName()));
  ```

<br>

# 4.15. Agrupación

- Utilizando el método _collect()_ de _Stream_, se puede generar una agrupación de objetos utilizando el siguiente método de _Collectors_
  - _Collector<T,?,Map<K,List<T>>> groupingBy(Function<? super T, ? extends K> classifier)_: devuelve un _Collector_ que implementa una agrupación de tipo _groupBy_ . El método recibe como parámetro un objeto _Function_ con el criterio de agrupación. Con este tipo de _Collector_, la llamada a _collect()_ devolverá un _Map_ de listas. Cada elemento del mapa tiene una clave, que es el dato por el que se hace la agruación, y un valor con la lista de objetos de cada grupo
    ```
    Stream<Person> st = Stream.of(new Person("John", 30, "john@mail.com"),
                                  new Person("Mery", 40, "mery@mail.com"),
                                  new Person("Anne", 35, "anne@mail.com"),
                                  new Person("Peter", 40, "peter@mail.com"));
     // agrupa las personas por edad
     Map<Integer, List<Person>> people = st.collect(Collectors.groupingBy(p -> p.getEdad()));
     people.forEach((k, v) -> System.out.println(v));
    ```

<br>

# 4.16. Partición

- Mediante el siguiente método de _Collectors_ podemos proporcionar una implementación de _collect()_ que genere una partición
  - _Collector<T,?,Map<Boolean,List<T>>> partitioningBy(Predicate<? super T> predicate)_: devuelve un _Collector_ para generar una agrupación _Map_ de clave _boolean_ y valor lista de objetos. El método recibe como parámetro un _predicate_ para aplicar la condición a cada elemento, de modo que los que la cumplan serán agrupados en una lista con clave _true_, y los que no en otra lista con clave _false_
  ```
  Stream<Person> st = Stream.of(new Person("John", 11, "john@mail.com"),
                               new Person("Mery", 40, "mery@mail.com"),
                               new Person("Anne", 16, "anne@mail.com"),
                               new Person("Peter", 40, "peter@mail.com"));
  // agrupa las personas menores de edad por un lado, y mayores por otro
  Map<Boolean, List<Person>> people = st.collect(Collectors.partitionBy(p -> p.getAge() > 18));
  ```

<br>

# 4.17. Otras implementaciones de Collector

- _Collectors_ ofrece estos otros métodos de interés
  - _Collector<T,?,Double> averagingDouble(ToDoubleFunction<? super T> mapper)_: calcula la media a partir de los valores devueltos por la función. Existe también _averagingInt_ y _averaginLong_
  - _Collector<T,?,Integer> summingInt(ToIntFunction<? super T> mapper)_: calcula la suma a partir de los valores devueltos por la función. Existe también _summingLong_ y _summingDouble_
  - _Collector<CharSequence,?.String> joining(CharSequence delimiter)_: devuelve un _Collector_ que concatena en un único _String_ todos los _String_ resultantes de la llamada a _toString()_ sobre cada objeto del _Stream_
    ```
    Stream<Person> st = Stream.of(new Person("John", 11, "john@mail.com"),
                              new Person("Mery", 40, "mery@mail.com"),
                              new Person("Anne", 16, "anne@mail.com"));
     // imprime los nombres de todas las personas, separados por una coma
     System.out.println(st
                    .map(p -> p.getName())
                    .collect(Collectors.joining(",")));
    ```
