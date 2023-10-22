**Question 1**: Which three are advantages of the Java exception mechanism?

- a.Improves the program structure because the error handling code is separated from the normal program function
- b.Provides a set of standard exceptions that covers all the possible errors
- c.Improves the program structure because the programmer can choose where to handle exceptions
- d.Improves the program structure because exceptions must be handled in the method in which they occurred
- e. Allows the creation of new exceptions that are tailored to the particular program being created

<br>

**Question 2**: Given the following:

```
public static void main(String[] args){
     ArrayList lst=new ArrayList();
     String[] mr;
     try{
          while(true){
               lst.add(new String("cad"));
          }
     }
     catch(RuntimeException ex){
          System.out.println("Is a RuntimeException");
     }
     catch(Exception ex){
          System.out.println("Is a Exception");
     }
     System.out.println("End");
}
```

What is the result?

- a.Execution terminates in the first catch statement, and caught a RuntimeException is printed to the console.
- b.Execution terminates In the second catch statement, and caught an Exception is printed to the console.
- c.A runtime error is thrown in the thread "main".
- d.Execution completes normally, and "End" is printed to the console.
- e.The code fails to compile because a throws keyword is required.

<br>

**Question 3**: Given the following classes

```
public class TestException extends RuntimeException {}

public class Test{
     public static void main(String[] args){
          try{
               myMethod();
          } catch(TestException ex){
               System.out.print("A");
          }
     }
     public static void myMethod(){ //line 1
          try{
               throw (Math.random()>0.5)?new TestException():
               new RuntimeException();
          } catch(RuntimeException ex){
               System.out.print("B");
          }
     }
}
```

What is the result?

- a. A
- b. B
- c.Either A or B
- d. AB
- e. Compilation fails at line 1

<br>

**Question 4**: Which two are Java System Exception classes?

- a. SercurityException
- b. DuplicatePathException
- c. IllegalArgumentException
- d. TooManyArgumentsException

<br>

**Question 5**: Given:

```
public class Test {
     public static void main(String[] args) {
          int ax = 10, az = 30;
          int aw = 1, ay = 1;
          try {
               aw = ax % 2;
               ay = az / aw;
          } catch (ArithmeticException e1) {
               System.out.println("Invalid Divisor");
          } catch (Exception e2) {
               aw = 1;
               System.out.println("Divisor Changed");
          }
          ay = az /aw; // Line 14
          System.out.println("Succesful Division " + ay);
     }
}
```

What is the result?

```
a.
     Invalid Divisor
     Divisor Changed
     Successful Division 30
b.
     Invalid Divisor
     Successful Division 30
c.
     Invalid Divisor
     Exception in thread "main" java.lang.ArithmeticException: / by zero
     at test.Teagle.main(Teagle.java:14)
d.
     Invalid Divisor
     Exception in thread "main" java.lang.ArithmeticException: / by zero
     at test.Teagle.main(Teagle.java:14)
     Successful Division 1
```

<br>

**Question 6**: Given:

```
public class Test {
     public static void main(String[] args) {
          int arr[] = new int[4];
          arr[0] = 1;
          arr[1] = 2;
          arr[2] = 4;
          arr[3] = 5;
          int sum = 0;
          try {
               for (int pos = 0; pos <= 4; pos++) {
                    sum = sum + arr[pos];
               }
          } catch (Exception e) {
               System.out.println("Invalid index");
          }
          System.out.println(sum);
     }
}
```

What is the result?

- a. 12
- b. Invalid Index<br>
  12
- c. Invalid Index
- d. Compilation fails

<br>

**Results**:

- **Question 1**: a, c, e
- **Question 2**: c
- **Question 3**: b
- **Question 4**: a, c
- **Question 5**: c
- **Question 6**: b
