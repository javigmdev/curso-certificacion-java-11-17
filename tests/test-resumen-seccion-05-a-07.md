**Question 1**: Which module-info.java is correct for a service provider for a Print service defined in the module PrintServiceAPI?

```
a. module PrintServiceProvider {
     requires PrintServiceAPI;
     exports org.printservice.spi;
}

b. module PrintServiceProvider {
     requires PrintServiceAPI;
     provides org.printservice.spi.Print with com.provider.PrintService;
}

c. module PrintServiceProvider {
     requires PrintServiceAPI;
     uses com.provider.PrintService;
}

d. module PrintServiceProvider {
     requires PrintServiceAPI;
     exports org.printservice.spi.Print with com.provider.PrintService;
}
```

<br>

**Question 2**: Why would you choose to use a peek operation instead of a forEach operation on a Stream?

- a. to process the current item and return void
- b. to remove an item from the end of the stream
- c. to process the current item and return a stream
- d. to remove an item from the beginning of the stream
  <br>

**Question 3**: Which two are valid statements?(Choose two.)

- a. BiPredicate<Integer, Integer> test = (final Integer x, var y) -> (x.equals(y));
- b. BiPredicate<Integer, Integer> test = (var x, final var y) -> (x.equals(y));
- c. BiPredicate<Integer, Integer> test = (Integer x, final var y) -> (x.equals(y));
- d. BiPredicate<Integer, Integer> test = (final var x, y) -> (x.equals(y));
- e. BiPredicate<Integer, Integer> test = (Integer x, final Integer y) -> (x.equals(y));

<br>

**Question 4**: Given

```
var fruits = List.of("apple", "orange", "banana", "lemon");
```

You want to examine the first element that contains the character n. Which statement will accomplish this?

- a. String result = fruits.stream().filter(f -> f.contains("n")).findAny();
- b. fruits.stream().filter(f -> f.contains("n")).forEachOrdered(System.out::print);
- c. Optional<String> result = fruits.stream().filter(f -> f.contains ("n")).findFirst ();
- d. Optional<String> result = fruits.stream().anyMatch(f -> f.contains("n"));

<br>

**Question 5**: Given:

```
public class Classes implements Serializable {
     String id;
}

class Person{
     String name;
     transient String address;
}

class Student extends Person implements Serializable{
     String studentNo;
     Classes classes=new Classes();
}
```

Which fields are serialized in a Student object?

- a. studentNo and classes
- b. studentNo and name
- c. studentNo, classes and name
- d. studentNo, classes, name, and address

<br>

**Question 6**: Given:

```
Path p1 = Paths.get("/scratch/exam/topsecret/answers");
Path p2 = Paths.get("/scratch/exam/answers/temp.txt");
Path p3 = Paths.get("/scratch/answers/topsecret");
```

Which two statements print ..\..\..\answers\topsecret? (Choose two.)

- a. System.out.print(p3.relativize(p1));
- b. System.out.print(p2.relativize(p3));
- c. System.out.print(p1.relativize(p3));
- d. System.out.print(p3.relativize(p2));
- e. System.out.print(p1.relativize(p2));
- f. System.out.print(p2.relativize(p1));

<br>

**Question 7**: Given:

```
Integer[] intArray = {2,1,3,4,5};
List<Integer> list = new ArrayList<>(Arrays.asList(intArray));
list.parallelStream().forEach(e->System.out.print(e+" "));
```

Which two are correct? (Choose two.)

- a. The output will be exactly 2 1 3 4 5.
- b. The program prints 1 4 2 3 5, but the order is unpredictable.
- c. Replacing forEach() with forEachOrdered(), the program prints 2 1 3 4 5, but the order is
  unpredictable.
- d. Replacing forEach() with forEachOrdered(), the program prints 1 2 3 4 5.
- e. Replacing forEach() with forEachOrdered(), the program prints 2 1 3 4 5.

<br>

**Results**:

- **Question 1**: b
- **Question 2**: c
- **Question 3**: b, e
- **Question 4**: c
- **Question 5**: a
- **Question 6**: b, c
- **Question 7**: b, e
