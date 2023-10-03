**Question 1**: given:

```
Collection<Number> col = new HashSet<>();
col.add(1);
var list1 = List.of(col); //1
col.add(2); //2
var list2 = List.copyOf(col); //3
System.out.println(list1 +", " + list2);
```

What is the output?

- a. It will not compile.
- b. Exception at run time at line marked //1.
- c. Exception at run time at line marked //2.
- d. Exception at run time at line marked //3.
- e. [[1,2]],[1,2]
- f. [1],[1,2]

<br>

**Question 2**: Given:

```
List<String> list1=new LinkedList<String>();
Set<String> set1 = new HashSet<String>();
String[] data = {"a","b","c","b","a"};
for(String s : data){
     list1.add(s);
     set1.add(s);
}
System.out.print(set1.size()+" "+list1.size()+" ");
HashSet set2 = new HashSet(list1);
LinkedList list2 = new LinkedList<>(set1);
System.out.print(set2.size() + " " + list2.size() + " ");
```

What is the result?

- a. 3 5 3 3
- b. 3 3 3 3
- c. 3 5 3 5
- d. 5 5 3 3

<br>

**Question 3**: Given

```
String[] sa = { "charlie", "bob", "andy", "dave" };
Collections.sort(Arrays.asList(sa), null);
System.out.println(sa[0]);
```

What will the following code print when run?

- a. charlie
- b. andy
- c. dave
- d. It will throw a NullPointerException
- e. It will not compile

<br>

**Question 4**: Given

```
import java.util.*;

class MyStringComparator implements Comparator{
     public int compare(Object o1, Object o2) {
          int s1 = ((String) o1).length();
          int s2 = ((String) o2).length();
          return s1 - s2;
     }
}
```

```
static String[] sa = { "d", "bbb", "aaaa" };
```

Select correct statements (2).

- a. This is not a valid Comparator implementation.
- b. Arrays.binarySearch(sa, "cc", new MyStringComparator()); will return -2.
- c. Arrays.binarySearch(sa, "c", new MyStringComparator()); will return 0.
- d. Arrays.binarySearch(sa, "c", new MyStringComparator()); will return -1.
- e. Arrays.binarySearch(sa, "c", new MyStringComparator()); will throw an exception.

<br>

**Question 5**: Which of the following are valid implementations of java.util.Comparator? (choose 2)

```
a.
Comparator<Integer> cin = new Comparator<Integer>(){
     public int compareTo(Integer i1, Integer i2){
          return i1 - i2;
     }
};
```

```
b.
var cin = new Comparator<Integer>(){
     public int compare(Integer i1, Integer i2){
          return i1 - i2;
     }
};
```

```
c.
var cin = new Comparator<Integer>(){
     public int compareTo(Integer i1, Integer i2){
          return i1 - i2;
     }
};
```

```
d.
Comparator<Integer> cin = new Comparator<?>(){
     public int compare(Integer i1, Integer i2){
          return i1 - i2;
     }
};
```

```
e. var cin = new Comparator<Integer>(){
     public int compare(Integer i1, Integer i2){
          return i1.compareTo(i2);
     }
};
```

<br>

**Question 6**: What will the following code print?

```
var a = new int[]{ 1, 2, 3, 4, 5};
var b = new int[]{ 1, 2, 3, 4, 5, 3};
var c = new int[]{ 1, 2, 3, 4, 5, 6};
int x = Arrays.compare(a, c);
int y = Arrays.compare(b, c);
System.out.println(x + " " + y);
```

- a. -1 -1
- b. 1 1
- c. -1 -3
- d. 1 3

<br>

**Results**:

- **Question 1**:
- **Question 2**:
- **Question 3**:
- **Question 4**:
- **Question 5**:
- **Question 6**:
