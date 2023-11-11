**Question 1**: Given the following interface:

```
public sealed interface Prints permits M1,M2{}
```

What of the following definitions are correct?

- a. sealed class M1 implements Prints{} <br>
  non-sealed interface M2 extends Prints{}
- b. non-sealed interface M1 extends Prints{} <br>
  final class M2 implements Prints{}
- c. final class M1 implements Prints{}<br>
  non-sealed interface M2 implements Prints{}
- d. final interface M1 extends Prints{} <br>
  non-sealed interface M2 extends Prints{}

<br>

**Question 2**: What is true about sealed class? (choose two)

- a. sealed class and permits classes must be in the same module
- b. sealed class and permits classes must be public
- c. sealed class must not have a constructor
- d. sealed class can extends another class
- e. sealed class can be final

<br>

**Question 3**: Given

```
interface Principal{
     int id();
}
sealed class Person implements Principal permits Student, Teacher {
     public int id(){
          return 0;
     }
}
record Student(int id, String subject) extends Person {}

sealed interface Teacher extends Person{}
```

Why doesn't compile the above code? (choose 2)

- a. Sealed class can't implement an interface
- b. Sealed class must be declared abstract
- c. A record can't extends a class
- d. Teacher interface must specific a list of permitted interfaces/classes

<br>

**Question 4**: Given:

```
sealed class C1 { //Line 1
     sealed class C2 extends C1 permits C3{ //Line 2
     }

     final class C3 extends C2{ //Line 3
     }

     class C4 extends C3{ //Line 4
     }

     void method() {
          C1 c=new C3(); //Line 5
     }
}
```

Where is the compilation fail?:

- a. Line 1
- b. Line 2
- c. Line 3
- d. Line 4
- e. Line 5

<br>

**Results**:

- **Question 1**:
- **Question 2**:
- **Question 3**:
- **Question 4**:
