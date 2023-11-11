**Question 1**: Given:

```
String cad1="This is text";
String cad2="""
     This is text""";
String cad3="""
     This is text
     """;
System.out.print(cad1.equals(cad2)+"-");
System.out.print(cad1.equals(cad3)+"-");
System.out.print(cad2.equals(cad3)+"-");
System.out.print(cad1.length()==cad2.length());
```

What is the result?

- a.false-false-false-false
- b.true-false-false-false
- c.true-true-false-false
- d.true-false-false-true
- e.false-true-true-true

<br>

**Question 2**: Given:

```
public static void main(String[] args){
     Integer data=10;
     int n=2;
     switch(data/n){
          case 1,3->System.out.print("low ");
          case 4,5-> System.out.print("medium ");
          case 6,7,9-> System.out.print("high");
     }
}
```

What is the result?

- a.medium
- b.medium high
- c.A runtime error is thrown.
- d.Compilation error.

<br>

**Question 3**: Given the following

```
class A{
     public void testA(){System.out.print("Is A ");}
}
class B extends A{
     public void testB(){System.out.print("Is B ");}
}
class C extends B{
     public void testC(){System.out.print("Is C ");}
}
```

And the following:

```
A ob=new C();
if(ob instanceof B b){
     b.testB(); //line 1
}
if(ob instanceof C a){//line 2
     a.testC();
} else{
     ob.testA();
}
```

What is the result?

- a. Is C
- b. Is A
- c. Is B Is C
- d. It prints nothing
- e. Compilation fails at line 1
- f. Compilation fails at line 2

<br>

**Question 4**: Given:

```
String cad="""
a""";
System.out.println(switch(cad.indent(1).length()){
     case 1->"simple";
     case 2,3->"normal";
     case 4->"optimal";
});
```

What is the result?

- a. simple
- b. normal
- c. optimal
- d. Compilation error

<br>

**Question 5**: Complete the following code (choose two):

```
enum Direction {
     NORTH, SOUTH, WEST, EAST
}
public class TestClass{
     public static String getColor(Direction c){
          INSERT CODE HERE
     }
     public static void main(String[] args) {
          System.out.println(getColor(Direction.NORTH));
     }
}
```

```
a. return switch(c){
     case NORTH, EAST -> "BLACK";
     break;
     case SOUTH, WEST -> "RED";
   };
b. return switch(c){
     case NORTH, EAST ->"BLACK";
     case SOUTH, WEST -> "RED";
     default -> "YELLOW";
   };
c. switch(c){
     case NORTH, EAST -> return "BLACK";
     case SOUTH, WEST -> return "RED";
   };
d. return switch(c){
     case NORTH, EAST -> "BLACK";
   };
e. return switch(c){
     case NORTH, EAST -> { yield "BLACK"; }
     case SOUTH, WEST -> { yield "RED"; }
   };
```

<br>

**Results**:

- **Question 1**: d
- **Question 2**: a
- **Question 3**: c
- **Question 4**: d
- **Question 5**: b, e
