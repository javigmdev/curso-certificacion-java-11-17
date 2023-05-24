**Question 1**: given the code fragment:

```
public class Test {
     public static void main(String[] args) {
          int x = 100;
          int a = x++;
          int b = ++x;
          int c = x++;
          int d = (a > b) ? (a < c) ? a: (b < c) ? b : c : b;
          System.out.println(d);
     }
}
```

What is the result?

- a. 100
- b. 102
- c. 101
- d. 103
- e. Compilation will fail

<br>

**Question 2**:

```
class Test{

     public static void main(String args[]){
          final int j;
          j = 2;
          int x = 0;
          switch(x){
               case 0:
                    {
                         System.out.print("A");
                    }
               case 1:
                    System.out.print("B");
                    break;
               case j:
                    System.out.print("C");
          }
     }
}
```

What is true?

- a. The output could be A
- b. The output could be AB
- c. The output could be ABC
- d. Compilation fails.
- e. There could be no output

<br>

**Question 3**: Given the code fragment

```
public class Test{
     public static void main(String[] args){
          //line 1
          switch(x){
               case 1:
                    System.out.println("One");
                    break;
               case 2:
                    System.out.println("Two");
                    break;
          }
     }
}
```

Which three code fragments can be independently inserted at line 1 to enable the code to print one?

- a. byte x = 1;
- b. short x = 1;
- c. String x = "1";
- d. long x = 1;
- e. double x = 1;
- f. Integer x = new Integer ("1");

<br>

**Question 4**: Given the following:

```
public void switchTest(byte x){
     switch(x){
          case 'b': // 1
          default:  // 2
          case -2:  // 3
          case 80:  // 4
     }
}
```

Select the correct:

- a. Compilation error in line 1
- b. Compilation error in line 2
- c. Compilation error in line 3
- d. Compilation error in line 4
- e. The code compile without errors

<br>

**Question 5**: What will the following program print when run without any command line argument?

```
public class TestClass {
     public static void main(String[] args) {
          var res = (args == null ? false : true);
          if(res){ //1
               System.out.print ("with params");
          }{
               System.out.println("no params");
          }
     }
}
```

- a. with params
- b. no params
- c. with paramsno params
- d. Compilation error in line 1
- e. It throws a runtime exception

<br>

**Results**:

- **Question 1**: b
- **Question 2**: d // switch permite constantes siempre que se les asignen su valor durante la declaración
- **Question 3**: a, b, e // byte, short e Integer se pueden convertir implícitamente a int (unboxing)
- **Question 4**: e
- **Question 5**: c
