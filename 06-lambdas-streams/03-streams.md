# 3. Stream

# 3.1. Introducción

- Un _Stream_ es un objeto que permite realizar de forma rápida y sencilla operaciones de búsqueda, filtrado, recolección, etc sobre un grupo de datos (array, colección o serie discreta de datos)
- Para manipular un _Stream_ utilizamos la interfaz _Stream_ de _java.util.stream_
- Otras variantes como _IntStream_, _LongStream_ o _DoubleStream_ se emplean para trabajar con tipos primitivos
- Recorre los datos desde el principio hasta el final y durante el recorrido realiza algún tipo de cálculo u operación
- Una vez realizado el recorrido, el _stream_ se cierra y no puede volver a utilizarse

<br>

# 3.2. Creación

- A partir de una colección
  ```
  ArrayList<Integer> numbers = new ArrayList<>();
  numbers.add(20);
  numbers.add(100);
  numbers.add(8);
  Stream<Integer> st = numbers.stream();
  ```
- A partir de un array
  ```
  String[] texts = {"a", "xy", "jk", "mv"};
  Stream<String> st = Arrays.stream(texts);
  ```
- A partir de una serie discreta de datos
  ```
  Stream<Double> st = Stream.of(2.4, 7.4, 0.1);
  ```
- A partir de un rango de datos (_Stream_ de tipos primitivos)
  ```
  IntStream stint = IntStream.range(1, 10);
  IntStream stint2 = IntStream.rangeClosed(1,10);
  ```

<br>

# 3.3. Tipos de métodos

- **Métodos intermedios**: el resultado de su ejecución es un nuevo _Stream_. Ejemplos: filtrado y transformación de datos, ordenación, etc
- **Métodos finales**: generan un resultado. Pueden ser _void_ o devolver un valor resultado de alguna operación. Ejemplos: calculo(suma, mayor, menor, ...), búsquedas, reducción, etc
