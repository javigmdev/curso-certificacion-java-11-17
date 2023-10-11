**Question 1**: What will the following code print?

```
List<Integer> str = Arrays.asList(1,2, 3, 4 );
     str.stream().filter(x->{
     System.out.print(x+" ");
     return x>2;
});
```

- a. 1 2 3 4
- b. 1 2 3 4 4
- c. 4
- d. It will not print anything

<br>

**Question 2**: Given the following code

```
import java.util.Arrays;
import java.util.List;
public class TestClass {
     public static void main(String[] args) {
          List<Integer> al = Arrays.asList(100, 200, 230, 291, 43);
          System.out.println( *INSERT CODE HERE* );
     }
}
```

Which of the following options will correctly print the number of elements that are less than 200?

- a. al.asStream().reduce((i)->i<200).count();
- b. al.stream().map((i)->i<200, i).count();
- c. al.stream().filter((i)->i<200).list().count();
- d. al.stream().filter((i)->i<200).count();
- e. al.asStream().filter((i)->i<200).count();

<br>

**Question 3**: Given:

```
public class Student {
     private String name;
     private int marks;
     //constructor and getters and setters not shown
     public void addMarks(int m){
          this.marks += m;
     }
     public void debug(){
          System.out.println(name+":"+marks);
     }
}
```

What will the following code print when compiled and run?

```
List<Student> slist = Arrays.asList(new Student("S1", 40), new Student("S2", 35), new Student("S3", 30));
Consumer<Student> increaseMarks = s->s.addMarks(10);
slist.forEach(increaseMarks);
slist.stream().forEach(s->s.debug());
```

```
a.
     S1:50
     S2:45
     S3:40
b.
     S1:40
     S2:35
     S3:30
c. It will not print anything.
d. It will not compile
```

<br>

**Question 4**: What will the following code print when compiled and run?

```
List<String> values = Arrays.asList("Java EE", "C#", "Python");
boolean flag = values.stream().allMatch(str->{
System.out.println("Testing: "+str);
return str.equals("Java");
});
System.out.println(flag);
```

```
a.
     Testing: Java EE
     false
b.
     Testing: Java EE
     Testing: C#
     Testing: Python
     false
c.
     Testing: Java EE
     true
d. It will not compile because lambda expression is built incorrectly.
```

<br>

**Question 5**: Given:

```
String sentence1 = "Carpe diem. Seize the day, boys. Make your lives extraordinary.";
String sentence2 = "Frankly, my dear, I don't give a damn!";
String sentence3 = "Do I look like I give a damn?";
List<String> sentences = Arrays.asList(sentence1, sentence2, sentence3);
```

Which of the following options will create a stream containing all the words in the three sentences without repetition?

```
a.
Stream<String> strm = sentences.stream()
               .flatMap(str->Stream.of(str.split("[ ,.!?\r\n]")))
               .filter(s->s.length()>0)
               .distinct();
b.
Stream<String> strm = sentences.stream()
               .map(str->Stream.of(str.split("[ ,.!?\r\n]")))
               .filter(s->s.length()>0)
               .distinct();
c.
Stream<String> strm = sentences.stream()
               .forEach(str->Stream.of(str.split("[ ,.!?\r\n]")))
               .filter(s->s.length()>0)
               .distinct();
d.
Stream<String> strm = sentences.stream()
               .flatMap(str-> str.split("[ ,.!?\r\n]"))
               .filter(s->s.length()>0)
               .distinct();
e.
Stream<String> strm = sentences.stream()
               .forEach(str->Stream.of(str.split("[ ,.!?\r\n]")))
               .filter(s->s.length()>0)
               .merge();
```

<br>

**Results**:

- **Question 1**: d
- **Question 2**: d
- **Question 3**: a
- **Question 4**: a
- **Question 5**: a
