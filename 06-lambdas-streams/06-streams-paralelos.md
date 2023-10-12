# 6. Streams paralelos

# 6.1. Fundamentos

- _Streams_ que utilizan la multitarea para realizar las operaciones
- Dividen la operación a realizar entre varios procesos que se ejecutan de manera concurrente
- Los _Stream_ paralelos siguen siendo objetos _Stream_, que utilizan los mismos métodos estudiados, pero operando de forma más eficiente
- Precaución en operaciones que requieran realizarse en un determinado orden

<br>

# 6.2. Creación

- A partir de una colección. Utilizamos el método _parallelStream()_ en lugar de _stream()_
  ```
  List<Integer> nums = List.of(20,100,80,25);
  Stream<Integer> pst = nums.parallelStream();
  ```
- A partir de un _Stream_ secuencial. Si ya se dispone de un _Stream_ estándar o secuencial, se puede obtener un _Stream_ paralelo a través del método _parallel()_
  ```
  Stream<Integer> st = Stream.of(20,100,80,25);
  Stream<Integer> pst = st.parallel();
  ```

<br>

# 6.3. Uso

- Una vez creado, se utiliza de la misma manera que los _Streams_ secuenciales, ya que se trata del mismo tipo de objeto
  ```
  List<Integer> nums = List.of(20,100,80,25);
  Stream<Integer> pst = nums.parallelStream();
  // muestra total de números pares
  System.out.println(pst.filter(n -> n % 2 == 0).count());
  ```
- Precaución con:

  ```
  List<Integer> nums = List.of(20,100,80,25);
  Stream<Integer> pst = nums.parallelStream();
  // intenta mostrar los números ordenados
  pst.sorted().forEach(s -> System.out.println(s));

  // aunque el stream se ordena, a la hora de mostrar el resultado no sale ordenado
  ```
