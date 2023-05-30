**Question 1**: Which statement is/are true?

1. Default constructor only contains "super();" call.
2. Only constructor with no parameters in the superclass can be called from subclass.
3. super o this call must be the first statement in all constructors.

- a. Only 1
- b. Only 2
- c. Only 1 and 2.
- d. Only 1 and 3.
- e. All

<br>

**Question 2**: Given the following:

```
class ClaseOne {
     public ClaseOne (int n){
          System.out.println(“Second constructor”);
     }
}

public class ClaseTwo extends ClaseOne {
     public ClaseTwo(){
          System.out.println(“constructor one from object”);
     }

     public ClaseTwo (int p){
          System.out.println(“constructor one from object”);
     }
}

// And the following main method:
ClaseTwo cd = new ClaseTwo(10);
```

Which is the result?

- a. constructor one from object
  - Second constructor
- b. Second constructor
  - constructor two from object
- c. constructor two from object
- d. Compilations fails

<br>

**Question 3**: Given the following:

```
class Data1 {
     int x;

     Data1(){
          this(100); //line 1
     }

     Data1(int n){
          this.x=n;
     }
}

class Data2 extends Data1{
     int y;

     Data2(){
          super();
          this(5); //line 2
     }

     Data2(int n){
          Data1(); //line 3
          this.y = n;
     }

     public String toString(){
          return super.x + ":" + this.y;
     }
}

// And given the following fragment:
Data2 dt = new Data2();
System.out.println(dt);
```

What is the result?

- a. 100:5
- b. 0:5
- c. Compilation fails at line 1
- d. Compilation fails at line 2
- e. Compilation fails at line 2 and line 3

<br>

**Question 4**: Given the following:

```
class Data1 {
     private int x;

     Data1(int x) {
          this.x = x;
     }
}

class Data2 extends Data1 ∫{
     int y;

     Data2(int x, int y) {
          //line 1
     }
}

// And given the following fragment:
Data2 dt = new Data2(2,7);
```

Which code fragment should you use at line 1 to instantiate the dt object successfully?

- a. super.x = x
  - this.y = y;
- b. super(x);
  - this(y);
- c. super(x);
  - this.y = y;
- d. this.x = x;
  - super(y);

<br>

**Question 5**: Given:

```
public class Test {
     void myMethod(){}
}

class Exam extends Test {
     ____ void myMethod(){}
}
```

Which two of the following can fill in the blank in this code to make it compile?

- a. abstract
- b. int
- c. private
- d. protected
- e. public

<br>

- **Question 1**: b
- **Question 2**: d (la clase padre no tiene constructor sin parámetros y al no poner el super para el constructor con un parámetro que tiene la clase padre da error)
- **Question 3**: e (tanto this como super deben estar en la primera línea del constructor y no pueden usarse en el mismo. Dentro de un constructor para llamar a otro no se puede usar el nombre de la clase, hay que usar super)
- **Question 4**: c
- **Question 5**: d, e
