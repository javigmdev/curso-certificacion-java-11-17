**Question 1**: Given:

```
var nums = List.of(1, 2, 3, 4, 5, 6, 7).stream();
Predicate<Integer> p = //a predicate goes here
Optional<Integer> value = nums.filter(p).reduce((a, b)->a+b);
value.ifPresent(System.out::println);
```

Choose 2:

- a. setting p to a->a<0; will produce no output.
- b. setting p to a->a<0; will generate a NullPointerException.
- c. setting p to a->a<0; will generate a NoSuchElementException.
- d. setting p to a->a%2==0; will produce 12.
- e. setting p to a->a%2==0; will produce 16.

<br>

**Question 2**: Given the Person class with age and name along with getter and setter methods, and this code fragment

```
List<Person> people = new ArrayList(List.of(new Person(44,"Tom"),
                                            new Person(40, "Aman"),
                                            new Person(40, "Peter")));
people.sort(Compartor.comparing((Person::getAge))
                                        .thenComparing(Person::getName)
                                        .reversed());
people.forEach(p1 -> System.out.prinln(" " + p1.getName()));
```

What will be the result?

- a. Aman Tom Peter
- b. Tom Aman Peter
- c. Aman Peter Tom
- d. Tom Peter Aman

<br>

**Question 3**: Given:

```
var numbers = List.of(0,1,2,3,4,5,6,7,8,9);
```

You want to calculate the average of numbers.
Which two codes will accomplish this? (Choose two.)

- a. double avg = numbers.stream().parallel().averagingDouble(a −> a);
- b. double avg = numbers.parallelStream().mapToInt(m −> m).average().getAsDouble();
- c. double avg = numbers.stream().mapToInt(i −> i).average().parallel();
- d. double avg = numbers.stream().average().getAsDouble();
- e. double avg = numbers.stream().collect(Collectors.averagingDouble(n −> n));

<br>

**Question 4**: Assuming the Widget class has a getPrice method, this code does not compile:

```
List widgets = List.of(new Widget("Basic Widget", 19.55), // line 1
                       new Widget("Enhanced Widget", 35.00),
                       new Widget("Luxury Edition Widget", 55.45));
Stream widgetStream = widgets.stream();          // line 4
widgetStream.filter(a -> a.getPrice() > 20.00)   // line 5
            .forEach(System.out::println);
```

Which two statements, independently, would allow this code to compile? (Choose two.)

- a. Replace line 5 with widgetStream.filter(a −> ((Widget)a).getPrice() > 20.00).
- b. Replace line 1 with List<Widget> widgetStream = widgets.stream();.
- c. Replace line 5 with widgetStream.filter((Widget a) −> a.getPrice() > 20.00).
- d. Replace line 4 with Stream<Widget> widgetStream = widgets.stream();.

<br>

**Question 5**: Given:

```
int arr[][] = {{5,10},{8,12},{9,3}};
long count = Stream.of(arr)
                    .flatMapToInt(IntStream::of)
                    .map(n -> n + 1)
                    .filter(n -> (n % 2 ==0))
                    .peek(System.out::println)
                    .count();
System.out.println(" " + count);
```

What is the result?

- a. 6910 3
- b. 10126 3
- c. 3
- d. 6104 3

<br>

**Results**:

- **Question 1**: a, d
- **Question 2**: d
- **Question 3**: b, e
- **Question 4**: a, d
- **Question 5**: d
