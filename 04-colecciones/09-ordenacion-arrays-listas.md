# 9. Ordenación de arrays y listas

# 9.1. Fundamentos sobre la ordenación

- Arrays y listas pueden ser ordenados según el orden natural de los objetos
- El orden natural se define a través de la interfaz _Comparable_, que deberá ser implementada por los objetos a ordenar
- Si las clases no implementan _Comparable_, se deberá definir el orden natural en otra interfaz llamada _Comparator_

<br>

# 9.2. Interfaz Comparable

- Se encuentra en el paquete _java.lang_:

  ```
  interface Comparable<T> {
       int compareTo(T object);
  }
  ```

  ```
  si objeto > objeto resultado --> >0
  si objeto == objeto resultado --> 0
  si objeto < objeto resultado --> <0
  ```

- Es implementada por clases de envoltorio y _String_
- Para poder ordenar listas y arrays de otro tipo de objetos, sus clases deberán implementar esta interfaz
- Ejemplo: se delega el orden natural de _Person_ al nombre de la misma y, en caso de igualdad, al de la edad

  ```
  class Person implements Comparable<Person> {
       private String name;
       private int age;

       // constructor, getters, setters

       public int compareTo(Person person) {
            if(this.name.compareTo(person.getName())== 0) {
                 return ((Integer) this.age).compareTo(person.getAge());
            } else {
                 return this.name.compareTo(person.getName());
            }
       }
  }
  ```

<br>

# 9.3. Ordenación de arrays

- Se emplea el método _sort(T[] data)_ de la clase _Arrays_
  ```
  int[] numbers = {7,2,34,11,6};
  Arrays.sort(numbers);
  for(int number : numbers) {
       System.out.println(number);
  }
  // 2,6,7,11,34
  ```
  ```
  Person[] people = {
       new Person("Jack", 25),
       new Person("Tom", 19),
       new Person("Jack", 21)
  };
  Arrays.sort(people);
  for(Person person : people) {
       System.out.println(person.getName() + "_" + people.getAge());
  }
  // Jack 21
  // Jack 25
  // Tom 19
  ```

<br>

# 9.4. Ordenación de listas

- Se emplea el método _sort(List<T> data) de \_Collections_

  ```
  List<Integer> numbers = new ArrayList<>();
  numbers.add(23);
  numbers.add(8);
  numbers.add(13);
  Collections.sort(numbers);
  for(int number : numbers) {
       System.out.println(number);
  }
  // 8, 13, 23
  ```

  ```
  List<Person> people = new ArrayList<>();
  people.add(new Person("Jack", 25));
  people.add(new Person("Tom", 19));
  people.add(new Person("Jack", 21));
  Collections.sort(people);
  for(Person person : people) {
     System.out.println(person.getNom() + "-" + person.getEdad());
  }
  // Jack 21
  // Jack 25
  // Tom 19
  ```

<br>

# 9.5. Interfaz Comparator

- Utilizada para poder definir el orden natural para aquellos tipos de objetos cuyas clases no implementan _Comparable_
- Se encuentra en _java.util_

```
 interface Comparator<T> {
      int compare(T object1, T object2);
 }
```

```
si objeto1 > objeto2 resultado --> >0
si objeto1 == objeto2 resultado --> 0
si objeto1 < objeto2 resultado --> <0
```

- Se utiliza en los siguientes métodos

  - _Arrays.sort(T[] data, Comparator<T> comparator)_
  - _sort(Comparator<T> comparator)_ --> método de List

- Ejemplo: ordenar la siguiente lista de cadenas por número de caracteres de menor a mayor
  ```
  List<Strig> texts = new ArrayList<>();
  texts.add("my text");
  texts.add("hello");
  texts.add("other text");
  ```
  ```
  public class TextComparator implements Comparator<String> {
       public int compare(String text1, String text2) {
            return text1.length() - text2.length();
       }
  }
  ```
  ```
  texts.sort(new TextComparator());
  ```

<br>

# 9.6. Búsqueda binaria en arrays

- La clase _Arrays_ proporciona el siguiente método para realizar una búsqueda en un array
  - _int binarySearch(type[] array, type value)_: devuelve la posición del valor dentro del array, que previamente debe estar ordenado
- Consideraciones sobre el método
  - Si el array no está ordenado, el resultado es impredecible
  - Si el array está ordenado y el elemento no se encuentra, se devuelve -plns-1, donde plns es la posición que le corresponde al elemento
  ```
  int[] numbers = {3,5,7,9,15,20};
  System.out.println(Arrays.binarySearch(numbers, 9)); // 3
  System.out.println(Arrays.binarySearch(numbers, 10)); // -5 (le correspondería la posición -4 en ese orden -1)
  ```

<br>

# 9.7. Comparación de arrays

- La clase _Arrays_ incorpora en Java 11, el siguiente método para comparar arrays
  - _int compare(type[] array1, type[] array2)_: devuelve el resultado de la comparación lexicográfica de ambos arrays
- El resultado de la comparación será
  - Si el array1 es menor que el array2 --> -1
  - Si ambos arrays son iguales --> 0
  - Si array1 es mayor que array2 --> 1
    ```
    int[] array1 = {1,2,5};
    int[] array2 = {1,2,1,4};
    int[] array3 = {1,2,1,4,1};
    System.out.println(Arrays.compare(array1, array2)); // 1
    System.out.println(Arrays.compare(array2, array3)); // -1
    ```
- La clase _Arrays_ incorpora en Java 9, el siguiente método para comprobar diferencias entre arrays
  - _int mismatch(type[] array1, type[] array2)_: devuelve la posición de la primera diferencia entre los dos arrays, o -1 si no hay diferencias
    ```
    int[] array1 = {1,2,5};
    int[] array2 = {1,2,1,4};
    int[] array3 = {1,2,1,4};
    System.out.println(Arrays.compare(array1, array2)); // 2
    System.out.println(Arrays.compare(array2, array3)); // -1
    ```
