**Question 1**: Which of the following are valid code snippets appearing in a method: (choose 3)

- a. var a = b = c = 100;
- b. var a = 100, b = 10; var a = b;
- c. int a, b, c = 100;
- d. int a = 100, b, c;
- e. int a = 100 = b = c;
- f. int a = b = c = 100;
- g. int a, b, c; a = b = c = 100;

<br>

**Question 2**: What will be the result of attempting to compile and run the following code?

```
public class PromotionTest{
     public static void main(String args[]){
          int i = 5;
          var f = 5.5f;
          double d = 3.8;
          var c = 'a';
          if (i == f) c++;
          if (((int) (f + d)) == ((int) f + (int) d)) c += 2;
          System.out.println(c);
     }
}
```

- a. The code will fail to compile.
- b. It will print d.
- c. It will print c.
- d. It will print b
- e. It will print a.

<br>

**Exercise 3**: Consider the following code appearing in a file named TestClass.java:

```
class Test{ } // 1
public class TestClass {
     var v1; // 2

     public int main(String[] args) { // 3
          var v2; //4
          double x = 10, double y; // 5
          System.out.println[]; // 6
          for(var k = 0; k < x; k++){ } //7
          return 0;
     }
}
```

Which of the lines are valid? (choose 3)

- a. 1
- b. 2
- c. 3
- d. 4
- e. 5
- f. 6
- g. 7

<br>

**Question 4**: Which of the lines are valid? (choose 3)

- a. var connection = DriverManager.getConnection(host, user, pass);
- b. var ej = 3/0;
- c. var cad = "";
- d. var n = null;
- e. var c, p = 10;
- f. var [] n = new int[4];

<br>

**Results**:

- **Question 1**: c, d, g
- **Question 2**: e
- **Question 3**: a, c, g
- **Question 4**: a, b, c
