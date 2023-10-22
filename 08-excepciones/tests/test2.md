**Question 1**: Given:

```
public static void main(String[] args) {
     Device d1 = new Device(1);
     try(d1){
          //do some thing with d1
     }
}
```

Identify correct statement(s).

- a. Device should extend AutoCloseable and override close() method.
- b. Device should implement Closeable and override close() method.
- c. Device should implement Closeable and override autoClose() method.
- d. Device should implement AutoCloseable and override autoClose() method.
- e. Device should implement AutoCloseable and override close() method.
- f. Device should extend AutoCloseable and override autoClose() method.

<br>

**Question 2**: What will the following code print when compiled and run?

```
public class Device implements AutoCloseable{
     boolean open = false;
     int index;
     public Device(int index){
          this.index = index;
          open = true;
     }
     public void write() throws IOException{
          throw new RuntimeException("Can't write!");
     }
     public void close(){
          open = false;
          System.out.print("Device closed "+index);
     }
     public static void main(String[] args) {
          Device d1 = new Device(1);
          try(d1;
               Device d2 = new Device(2);
               Device d3 = new Device(3)){
               d2.write();
               d1.close();
          }catch(Exception e){
               System.out.print("Got Exception "+e.getMessage());
          }
     }
}
```

- a. Device closed 3Device closed 2Got Exception Can't write!
- b. Device closed 2 Device closed 3 Got Exception Can't write!
- c. Device closed 1 Device closed 2 Device closed 3 Got Exception Can't write!
- d. Device closed 1 Device closed 3 Device closed 2 Got Exception Can't write!
- e. Device closed 3 Device closed 2 Device closed 1 Got Exception Can't write!

<br>

**Question 3**: Given the following exception classes:

```
class MyException extends Exception{}
class MyException1 extends MyException{}
class MyException2 extends MyException{}
class MyException3 extends MyException2{}
and the following code:
try{
//code that could potentially throw any of the above mentioned exceptions
}
INSERT CODE HERE
```

What is the result?

Which of the following options can be inserted in the above code?

- a. catch(MyException|MyException3 e){ }
- b. catch(MyException3 me3){ } <br>
  catch(Exception e){ }
- c. catch(MyException2 me2){ } <br>
  catch(MyException3 me3){ }
- d. catch(Throwable t){ } <br>
  catch(MyException3 me3){ }
- e. catch(MyException|MyException1|MyException2|MyException3 e){ }

<br>

**Question 4**: Given:

```
public static void main(String[] args) {
     try (Reader reader1 = new FileReader("File1.txt");
          Reader reader2 = new FileReader("File2.txt");
          Reader reader3 = new FileReader("File3.txt")) {

     } catch(IOException ex) {
          Logger.getLogger(Main.class.getName()).log(Level.SEVERE, null, ex);
     }
     // Line 1
     System.out.println("Done");
}
```

When run and all three files exist, what is the state of each reader on Line 1?

- a. All three readers are still open.
- b. All three readers have been closed.
- c. The compilation fails.
- d. Only reader1 has been closed.

<br>

**Results**:

- **Question 1**: e
- **Question 2**: e
- **Question 3**: b
- **Question 4**: b
