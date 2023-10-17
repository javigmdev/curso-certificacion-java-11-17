**Question 1**: Given

```
public class Main {
     public static void main(String[] args) {
          try(BufferedReader in = new BufferedReader(new InputStreamReader(System.in))) {
               System.out.print("Input: ");
               String input = in.readLine();
               System.out.print("Echo: " + input);
          } catch(IOException e) {
               e.printStackTrace();
          }
     }
}
```

And the command:

```
java Main Helloworld
```

What is the result ?

```
a. Input:
   Echo:
b. Input: Helloworld
   Echo: Helloworld
c. Input:
   Then block until any input comes from System.in
d. Input:
   Echo: Helloworld
e. A NullPointerException is thrown at run time
```

<br>

**Question 2**: Given

```
public static void reader(String fileName1) throws Exception{
     try (var fr = new FileReader(fileName1);) {
          int charRead = 0;
          while ((charRead = fr.read()) != -1) {
               System.out.println("Read char " + charRead);
          }
     }
}
```

What can be done to the above code to make it read Strings instead of chars?

- a. Chain fr to a StringReader and use its readString method.
- b. Use fr.readString instead of fr.read.
- c. Chain fr to a BufferedReader use its readLine method
- d. Chain fr to a DataReader and use its readLine method.

<br>

**Question 3**: Given

```
public class SerializedMessage implements Serializable {
     String message;
     LocalDateTime createdTime;
     transient LocalDateTime updatedDateTime;

     SerializedMessage(String message) {
          this.message = message;
          this.createdTime = LocalDateTime.now();
     }

     private void readObject(ObjectInputStream in) {
          try {
               in.defaultReadObject();
               this.updateDateTime = LocalDateTime.now();
          } catch(IOException | ClassNotFoundException e) {
               e.printStackTrace();
          }
     }
}
```

When is the readObject method called?

- a. before this object is deserialized
- b. after this object is deserialized
- c. before this object Is serialized
- d. The method is never called.
- e. after this object is serialized

<br>

**Question 4**: Given that the file test.txt contains:

```
12345678
```

What will the following code print when compiled and run?

```
public static void main(String[] args) throws Exception{
     try(var fis = new FileInputStream("c:\\temp\\test.txt");
          var isr = new InputStreamReader(fis)){
          while(isr.ready()){
               isr.skip(1);
               int i = isr.read();
               char c = (char) i;
               System.out.print(c);
          }
     }
}
```

When run and all three files exist, what is the state of each reader on Line 1?

- a. It will not compile.
- b. It will throw an exception when run.
- c. It will print just 2.
- d. It will run without any exception but will not print anything.
- e. It will print 2468

<br>

**Question 5**: What is the output of the following program? Assume the file paths referenced in the class
exist and are able to be written to and read from.

```
import java.io.*;

public class Vegetable implements Serializable {
     private Integer size = 1;
     private transient String name = "Red";

     { size = 3; name = "Purple"; }

     public Vegetable() {
          this.size = 2;
          name = "Green";
     }

     public static void main(String[] love) throws Throwable {
          try (var o = new ObjectOutputStream(
                    new FileOutputStream("healthy.txt"))) {
               final var v = new Vegetable();
               v.size = 4;
               o.writeObject(v);
          }
          try (var o = new ObjectInputStream(
               new FileInputStream("healthy.txt"))) {
               var v = (Vegetable) o.readObject();
               System.out.print(v.size + "," + v.name);
          }
     }

}
```

- a. 1,Red
- b. 2,Green
- c. 2,null
- d. 3,Purple
- e. 4,null
- f. null,null

<br>

**Results**:

- **Question 1**: c
- **Question 2**: c
- **Question 3**: b
- **Question 4**: e
- **Question 5**: e
