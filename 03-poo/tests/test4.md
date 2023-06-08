**Question 1**: Given

```
Class A {}
Class B {}
Interface X {}
Interface Y {}
```

Which two definitions of class C are valid?

- a. class C extends A implements X { }
- b. class C implements Y extends B { }
- c. class C extends A, B { }
- d. class C implements X, Y extends B { }
- e. class C extends B implements X, Y { }

<br>

**Question 2**: Given the following:

```
abstract class Car{
     protected void run(){} //line 1
     abstract Object stop(); //line 2
}
class MyCar extends Car{
     void run(){} //line 3
     protected void stop(){} //line 4
}
```

Which two modifications are necessary to enable the code to compile?

- a. Make the method at line 1 public.
- b. Make the method at line 2 public.
- c. Make the method at line 3 public.
- d. Change the return type of method in line 4 to String.
- e. Make the method at line 4 public.

<br>

**Question 3**: Given the code:

```
public static void main(String[] args){
     Short a = 100;
     Integer b = 300;
     Long c = (long)a + b; //line 1
     String d = (String)(c * b); //line 2
     System.out.println("Result: " +d)
}
```

What is the result?

- a. Sum is 400
- b. Compilation fails at line 1.
- c. Compilation fails at line 2.
- d. A ClassCastException is thrown at line 1.
- e. A ClassCastException is thrown at line 2.

<br>

**Question 4**: Which two are benefits of polymorphism?

- a. Faster code at runtime
- b. More efficient code at runtime
- c. More dynamic code at runtime
- d. More flexible and reusable code
- e. Code that is protected from extension by other classes

<br>

**Question 5**: Given the following class declarations:

```
public abstract class Animal
public interface Hunter
public class Cat extends Animal implements Hunter
public class Tiger extends Cat
```

Which answer fails to compile?

- a. ArrayList<Animal> ml=new ArrayList<>()
  - ml.add(new Tiger());
- b. ArrayList<Hunter> ml=new ArrayList<>()
  - ml.add(new Cat());
- c. ArrayList<Hunter> ml=new ArrayList<>()
  - ml.add(new Tiger());
- d. ArrayList<Tiger> ml=new ArrayList<>()
  - ml.add(new Cat());
- e. ArrayList<Animal> ml=new ArrayList<>()
  - ml.add(new Cat());

<br>

**Question 6**: Which two statements correctly describe capabilities of interfaces and abstract classes?
(Choose two.)

- a. Interfaces cannot have protected methods but abstract classes can.
- b. Both interfaces and abstract classes can have final methods.
- c. Interfaces cannot have instance fields but abstract classes can.
- d. Interfaces cannot have static methods but abstract classes can.
- e. Interfaces cannot have methods with bodies but abstract classes can.

<br>

- **Question 1**: a, e
- **Question 2**: c, d
- **Question 3**: c
- **Question 4**: c, d
- **Question 5**: d
- **Question 6**: a, c
