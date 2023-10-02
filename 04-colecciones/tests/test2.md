**Question 1**: given:

```
public static void main(String[] args){
     List<Integer> even = List.of();
     even.add(0, 10);
     even.add(0, 20);
     System.out.println(even);
}
```

What is the output?

- a. The compilation fails.
- b. [10,20]
- c. [20,20]
- d. A runtime exception is thrown

<br>

**Question 2**: Select the correct sentences (choose 3):

```
 a. Iterable<Integer> it = List.of(4,9,1);
 b. var data = new ArrayList<>();
 c. Collection<?> values = List.of(9,2,5);
 d. List<Object> objs = new ArrayList<Integer>();
 e. List<Integer> ints = new Integer[] {4,1,0};
 f. ArrayList<String> cads = List.of("year","now");
```

<br>

**Question 3**: What will the following code print?

```
List s1 = new ArrayList( );
s1.add("a");
s1.add("b");
s1.add("c");
s1.add("a");
System.out.println(s1.remove("a") + " " + s1.remove("x"));
```

- a. a 0
- b. 0 1
- c. 1 -1
- d. true false

<br>

**Question 4**: Given

```
var data = new ArrayList<>();
data.add("Help");
data.add(30);
data.add("Main Name");
data.set(1, 25);
data.remove(2);
data.set(3, 1000L);
System.out.print(data);
```

What is the output?

- a. [Main Name, 1000]
- b. [Help, 30, Main Name]
- c. [Help, 25, null, 1000]
- d. An exception is thrown at runtime

<br>

**Question 5**: Given:

```
HashMap<Integer, String> people  = new HashMap<>(Map.ofEntries(
     Map.entry(100, "Peter"),
     Map.entry(555, "Mary"),
     Map.entry(222, "Anne")));
people.putIfAbsent(666, "Arnold"); //1
ArrayList<String> list = new ArrayList<>(people.values());
System.out.println(list);
```

Which is the result?

- a. [Peter, Mary, Anne, Arnold]
- b. [Peter, Anne,Mary,Arnold]
- c. It prints Peter, Mary, Anne and Arnold in any order
- d. Exception in line 1

<br>

**Question 6**: Given:

```
String[] p = {"1","2","3"};
```

Which of the following lines of code is/are valid?

- a. List<?> list2 = new ArrayList<Integer>(Arrays.asList(p));
- b. List<Integer> list2 = new ArrayList<Integer>(Arrays.asList(p));
- c. List<Integer> list2 = new ArrayList<>(Arrays.asList(p));
- d. List<?> list2 = new ArrayList<>(Arrays.asList(p));

<br>

**Results**:

- **Question 1**: d
- **Question 2**: a, b, c
- **Question 3**: d
- **Question 4**: d
- **Question 5**: c
- **Question 6**: d
