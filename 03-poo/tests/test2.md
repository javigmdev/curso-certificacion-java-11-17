**Question 1**: given the following:

```
public class Test {

     public Test(){
         System.out.println("No params");
     }

     public void Test(int j){
          System.out.println("Param " + j);
     }

     public static void main(String[] args) {
          Test t = new Test(3);
     }
}
```

Which is the result?

- a. Param 3
- b. No params
- c. Compilation fails
- d. Exception

<br>

**Question 2**: Given the following:

```
class Vehicle {
     String name;

     void setName (String name) {
          this.name = name;
     }

     String getName() {
          return name;
     }
}
```

Which action would apply encapsulation in this class?

- a. Define name variable as public
- b. Define name variable as private
- c. Define Vehicle class as public
- d. Define setter and getter methods as public
- e. Define setter and getter methods as private

<br>

**Question 3**: Given:

```
C1.java
package p1;
class C1 {
     int p;
     private int k;
     public int s;
}

C2.java
package p2;
import p1.C1;
public class C2{
     public static void main(String[] args){
          C1 obj = new C1();
     }
}
```

Which statement is true?

- a. Both p and s are accesible by obj
- b. Only s is accesible by obj
- c. None of the variables are accesible by obj
- d. Compilation fails

<br>

**Question 4**: Which are true? (choose 2)

- a. Default constructor should be always there for any class.
- b. Default constructor must have parameters
- c. When defining our own constructor we can’t use any access modifier.
- d. A constructor should not have a return type.
- e. We can have more than one constructor in a class

<br>

**Results**:

- **Question 1**: c
- **Question 2**: b
- **Question 3**: d
- **Question 4**: d, e
