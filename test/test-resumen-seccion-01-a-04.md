**Question 1**: given:

```
public class Tester {
     public static void main(String[] args) {
          int x=0, y=6;
          for(;x<y;x++,y--) { //line 1
               if(x%2==0) {
                    continue;
               }
               System.out.println(x+"-"+y);
          }
     }
}
```

What is the result?

- a. 2-4
- b.
  - 0-6
  - 1-5
  - 2-4
- c. 1-5
- d.
  - 1-5
  - 2-4
- e. Compilations fails due an error in line 1
- f. 0-6

<br>

**Question 2**: Given:

```
class Padre{
     public List<Integer> mt(Set<CharSequence> data){...}
}
public class Hija extends Padre{
}
```

Which two method definitions at line n1 in the Hija class compile? (Choose two.)

```
 a. public List<Number> mt(Set<String> m) {...}
 b. public List<Integer> mt(Set<CharSequence> m) {...}
 c. public List<Integer> mt(TreeSet<String> m) {...}
 d. public List<Object> mt(Set<CharSequence> m) {...}
 e. public ArrayList<Integer> mt(Set<String> m) {...}
 f. public ArrayList<Number> mt(Set<CharSequence> m) {...}
```

<br>

**Question 3**: Which three initialization statements are correct?(Choose three.)

- a. int[][][] e = {{1,1,1},{2,2,2}};
- b. short sh = (short)'A';
- c. float x = 1f;
- d. byte b = 10; char c = b;
- e. String contact# = "(+2) (999) (232)";
- f. int x = 12_34;
- g. boolean false = (4 != 4);

<br>

**Question 4**: Given

```
List<Integer> lst1 = new ArrayList<>(List.of(3,9,4));
List<Integer> lst2 = Collections.unmodifiableList(lst1);
lst1.remove(0);
System.out.println(lst1);
System.out.println(lst2);
```

What is the output?

- a.
  - [9,4]
  - [3,9,4]
- b.
  - [3,9,4]
  - [3,9,4]
- c.
  - [9,4]
  - [9,4]
- d. An exception is thrown at runtime

<br>

**Question 5**: Given

```
public class Tester {
     public static void main(String[] args) {
          char letter = 'b';
          int i = 0;
          switch(letter) {
               case 'a':
                    i++;
                    break;
               case 'b':
                    i++;
               case 'c': | case 'd': //line 1
                    i++;
               case 'e':
                    i++;
                    break;
               case 'f':
                    i++;
                    break;
               default:
                    System.out.print(letter);
          }
          System.out.println(i);
     }
}
```

Which is the result?

- a. b1
- b. 2
- c. b2
- d. 1
- e. b3
- f. 3
- g. The compilation fails due to an error in line 1.

<br>

**Question 6**: Given

```
public class Datas {
     int aData;
     int bData;
     int cData;
     int dData;
     Datas(int a, int bData, int c, int dData) {
          //line 1
     }
     int setCData(int c){
          return c;
     }
     void setDData(int dData){
          this.dData=dData;
     }
}
```

Which two lines of code when inserted in line 1 correctly modifies instance variables? (Choose two.)

- a. setDData(dData);
- b. setCData(c) = cData;
- c. bData = bData;
- d. aData = a;
- e. dData = setCData(c);

<br>

**Question 7**:

```
public class Super {
     final int num; //line n1
     public Super(int num) {
          this.num=num;
     }
     final void method() {
          System.out.println("Output from Super");
     }
}

class Sub extends Super{
     int num; //line n2
     Sub(short num){ //line n3
          super(num);
     }
     protected void method() { //line n4
          System.out.println("Output from Sub");
     }
}
```

Which line of code results in a compilation error?

- a. line n1
- b. line n3
- c. line n2
- d. line n4

<br>

**Results**:

- **Question 1**: c
- **Question 2**: b, c
- **Question 3**: b, c, f
- **Question 4**: c (las dos listas apuntan a la misma referencia)
- **Question 5**: g
- **Question 6**: a, d
- **Question 7**: d
