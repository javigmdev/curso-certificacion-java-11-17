**Question 1**: Given:

```
System.out.println("6+3="+2+7);
System.out.println("6+3="+(2+7));
```

What is the result?

- a. 6+3=27, 6+3=27
- b. 6+3=2+7, 6+3=9
- c. 9=9, 9=9
- d. 6+3=27, 6+3=9

<br>

**Question 2**: Given the following:

```
public class Test {
     static int i;

     public static void main (String []args) {
          int a = 2, b = i + 1;
          if ((a++ > ++b) && (++a > 5)) {
               a += b;
          }
     }
}
```

What is the final value of a?

- a. 1
- b. 2
- c. 3
- d. 4
- e. 5

<br>

**Question 3**: Given the code fragment:

```
StringBuilder sb1 = new StringBuilder("hello");
String str1 = sb1.toString();
//insert code here
System.out.println(str1 == str2);
```

Which code fragment, when inserted at "insert code here", enables the code to print true?

- a.String str2 = str1;
- b.String str2 = new String(str1);
- c.String str2 = sb1.toString();
- d.String str2 = "hello";

<br>

**Question 4**: Given the following:

```
class Test{

     public static void main(String args[]){
          String arg = "hello";
          change(arg);
          System.out.println(arg);
     }

     static void change(String s){
          s = s + " bye";
     }
}
```

What is the result?

- a. hello
- b. hello bye
- c. compilations fails
- d. exception

<br>

**Question 5**: Given the code fragment

```
public class Test{

     public static void main(String[] args){
          StringBuilder sb = new StringBuilder(5);
          String s = "";
          if(sb.equals(s)){
               System.out.println("option A");
          } else if(sb.toString().equals(s.toString())){
               System.out.println("option B");
          }else{
               System.out.println("option C");
          }
     }

}
```

What is the result?

- a. option A
- b. option B
- c. option C
- d. NullPointerException is thrown at runtime

<br>

**Question 6**: Which of the following statements are true? (choose 2)

- a. System.out.println(1 + 2 + "3"); will print 33.
- b. System.out.println("1" + 2 + 3); will print 15.
- c. System.out.println(4 + 1.0f); will print 5.0
- d. System.out.println(5/4); will print 1.25
- e. System.out.println('a' + 1 ); will print b.

<br>

**Results**:

- **Question 1**: d
- **Question 2**: c
- **Question 3**: a
- **Question 4**: a
- **Question 5**: b
- **Question 6**: a, c
