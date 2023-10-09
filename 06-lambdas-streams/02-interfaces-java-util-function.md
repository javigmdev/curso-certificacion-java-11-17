# 2. Interfaces java.util.function

# 2.1. Introducción

- Conjunto de interfaces funcionales incorporadas en Java SE 8 dentro del paquete _java.util.function_
- Utilizadas como argumentos en métodos que manipulan datos para el establecimiento de criterios de filtrado, operación sobre elementos, transformación, etc
- Implementadas habitaualmente mediante expresiones lambda

<br>

# 2.2. Interfaz Predicate

- Dispone del método abstracto _test_, que a partir de un objeto realiza una comprobación y devuelve un _boolean_
  ```
  boolean test(T t);
  ```
- Utilizada para la definición de criterios de filtrado, por ejemplo, método _removeIf()_ de _Collection_

  ```
  // elimina los elementos que cumplen la condición del filtro
  boolean removeIf(Predicate<? super T> filtro)

  // eliminación de números pares
  list.removeIf(number -> number % 2 == 0);
  ```

- Variable _BiPredicate<T,U>_ con dos parámetros
  ```
  boolean test(T t, U u)
  ```

<br>

# 2.3. Interfaz Function

- Método abstracto _apply_, que a partir de un objeto realiza una operación y devuelve un resultado
  ```
  R apply(T t)
  ```
- Utilizado en operaciones de transformación de datos. Por ejemplo, método _map()_ de Stream

  ```
  // Transforma cada elemento del Stream del tipo T en otro de tipo R
  Stream<R> map(Function<? super T,? extends R> mapper)

  // genera un nuevo Stream con la longitud de las cadenas del Stream original
  stream.map(text->text.legth());
  ```

- Variante _BiFunction<T,U,R>_ con dos parámetros
  ```
  R apply(T t, U u)
  ```

<br>

# 2.4. Interfaz Consumer

- Dispone del método abstracto _accept_, que realiza algún tipo de procesamiento con el objeto recibido
  ```
  void accept(T t)
  ```
- Utilizada en operaciones de procesamiento de datos. Por ejemplo, método _forEach()_ de listas y conjuntos

  ```
  // aplica las operaciones del método a cada elemento de la lista
  void forEach(Consumer<? super T> action)

  // imprime el contenido de la lista
  list.forEach(number -> System.out.println(number));
  ```

- Variante _BiConsumer<T,U>_ con dos parámetros
  ```
  void accept(T t, U u)
  ```

<br>

# 2.5. Interfaz Supplier

- Dispone del método abstracto _get_, que no recibe ningún parámetro y devuelve como resultado un objeto
  ```
  T get()
  ```
- Utilizada para implementar operaciones de extracción de datos. Por ejemplo, método _generate()_ de _Stream_

  ```
  // genera una secuencia infinita de elementos proporcionados por llamadas a get()
  static Stream<T> generate(Supplier<T> s)

  // devuelve un Stream de números aleatorios entre 1 y 500
  Stream.generate(() -> (int)(Math.random() * 500 + 1));
  ```

<br>

# 2.6. Interfaz UnaryOperator

- Subinterfaz de _Function_ donde el tipo de entrada coincide con el de devolución
  ```
  T apply(T t)
  ```
- Al igual que _Function_, se emplea en contextos de transformación de datos. Ejemplo, método _replaceAll()_ de _Collection_

  ```
  // reemplaza cada elemento de la colección por otro resultante de aplicar la función
  void replaceAll(UnaryOperator<? super T> oper)

  // sustituye cada elemento de la colección por su cuadrado
  list.replaceAll(n -> n * n);
  ```

- Variante _BinaryOperator<T>_ equivalente a _BIFunction<T,T,T>_

<br>

# 2.7. Interfaces para tipos primitivos

```
IntPredicate --> boolean test(int t)
IntFunction<R> --> R apply(int t)
IntConsumer --> void accept(int t)
IntSupplier --> int getAsInt()
IntUnaryOperator --> int applyAsInt(int t)

Versiones también para long y double
```
