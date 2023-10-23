**Question 1**: Which statement about the following class is correct?

```
package mypg;
import java.util.*;

public class ThreadSafeList {
     private List<Integer> data = new ArrayList<>();

     public synchronized void addValue(int value) {
          data.add(value);
     }

     public int getValue(int index) {
          return data.get(index);
     }

     public int size() {
          synchronized(ThreadSafeList.class) {
               return data.size();
          }
     }
}
```

- a. The code compiles and is thread-safe.
- b. The code compiles and is not thread-safe.
- c. The code does not compile because of the size() method.
- d. The code does not compile because of the getValue() method.

<br>

**Question 2**: Given:

```
class Tarea implements Runnable{
     @Override
     public void run() {
          System.out.print("print ");
     }
}

public class Test {
     public static void main(String[] args) {
          Thread t1=new Thread(new Tarea());
          Thread t2=new Thread(new Tarea());
          t1.start();
          t1.run(); //line 1
          t2.start();
          t1.start(); //line 2
     }
}
```

Which one is correct?

- a. print print print
- b. print print
- c. Exception in line 1
- d. Exception in line 2
- e. Compilation fails

<br>

**Question 3**: Which of the following statements are true?

- a. A synchronized method cannot call another synchronized method in its body
- b. Making a synchronized method recursive will cause a deadlock
- c. Only non-static member variables are accessible in a synchronized method
- d. A synchronized method cannot be executed simultaneously by more than one thread on the same object.
- e. A synchronized method cannot call a non-synchronized method in its body.

<br>

**Results**:

- **Question 1**: b
- **Question 2**: d
- **Question 3**: d
