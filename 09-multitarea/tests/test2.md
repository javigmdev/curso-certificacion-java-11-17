**Question 1**: Given the code fragment:

```
var pool = Executors.newFixedThreadPool(5);
Future outcome = pool.submit(() −> 1);
```

Which type of lambda expression is passed into submit()?

- a. java.lang.Runnable
- b. java.util.function.Predicate
- c. java.util.function.Function
- d. java.util.concurrent.Callable

<br>

**Question 2**: Consider the following code:

```
class Account{
     private String id;
     private double balance;

     ReentrantLock lock = new ReentrantLock();

     public void withdraw(double amt){
          try{
               lock.lock();
               if(balance > amt) balance = balance - amt;
          } finally {
               lock.unlock();
          }
     }
}
```

What can be done to make the above code thread safe?

- a. Change new ReentrantLock() to new ReentrantLock(true)
- b. Move the call to lock.lock(); to before the try block
- c. Declare lock variable as private and final
- d. Make the lock variable private, final, and static
- e. No change is required

<br>

**Question 3**: Consider the following code:

```
import java.util.List;
import java.util.concurrent.CopyOnWriteArrayList;

public class MyCache {
     private CopyOnWriteArrayList<String> cal = new CopyOnWriteArrayList<>();

     public void addData(List<String> list){
          cal.addAll(list);
     }
     public Iterator getIterator(){
          return cal.iterator();
     }
}
```

Given that one thread calls the addData method on an instance of the above class and another thread calls the getIterator method on the same instance at the same time and starts iterating through its values, which of the following options are correct?
<br>

(Assume that no other calls have been made on the MyCache instance.)

- a. The call to addAll may be blocked while the other thread is iterating through the iterator
- b. Both the threads will complete their operations successfully without getting any exception
- c. The thread iterating through the Iterator will get a ConcurrentModificationException
- d. Elements added by the addAll method will automatically be visible through the iterator in the other thread

<br>

**Question 4**: What will the following code print?

```
var rlock = new ReentrantLock();
var f1 = rlock.lock();
System.out.print(f1);
var f2 = rlock.lock();
System.out.println(f2);
```

- a. true true
- b. true false
- c. true
- d. It will not compile

<br>

**Question 5**: You want to execute your tasks after a given delay. Which ExecutorService would you use?

- a. FixedDelayExecutorService
- b. TimedExecutorService
- c. DelayedExecutorService
- d. ScheduledExecutorService

<br>

**Question 6**: Which of the following code fragments will you use to create an ExecutorService? (choose 2)

- a. ExecutorService
- b. Executor
- c. Executors
- d. .newSingleThreadExecutor();
- e. .createSingleThreadExecutor();
- f. .getSingleThreadExecutor();

<br>

**Results**:

- **Question 1**: d
- **Question 2**: c
- **Question 3**: b
- **Question 4**: d
- **Question 5**: d
- **Question 6**: c, d
