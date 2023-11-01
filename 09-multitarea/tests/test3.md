**Question 1**: Given the code fragment:

```
public static void main(String[] args) {
     List<Integer> list=new CopyOnWriteArrayList<>();
     ExecutorService service=Executors.newFixedThreadPool(5);
     CyclicBarrier barrier=new CyclicBarrier(2, ()->System.out.println(list));
     IntStream.range(0, 5).forEach(n->service.execute(()->
     {
          try {
               list.add(n);
               barrier.await();
          }catch(InterruptedException|BrokenBarrierException e) {
               System.out.println("exception");
          }
     }));
     service.shutdown();
}
```

Which statement is true?

- a. It never finishes.
- b. The action of CyclicBarrier is called five times.
- c. It finishes without any exception.
- d. Threads in executorService execute for each of the two threads.

<br>

**Results**:

- **Question 1**: a
