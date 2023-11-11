**Question 1**: What is true about the records? (choose three):

- a. Can extends a class
- b. Can implements an interface
- c. Can define specific instance variables
- d. Can extends another Record
- e. Can define specific constructors
- f. Are implicitly final

<br>

**Question 2**: Given:

```
record MyClass(int id, String name){
     int rate;
     public int getRate(){
          return rate;
     }
}

public class TestClass{
     public static void main(String[] args) {
     MyClass mc = new MyClass(1000, "Java");
       System.out.println(mc);
     }
}
```

Which change will enable the code to compile?

- a. Replace record with void.
- b. Replace record with class.
- c. Make the rate variable private.
- d. Make the rate variable static.
- e. Intinialize rate variable with 0.

<br>

**Question 3**: Given

```
record Course(String name, int duration){
     //line 1
}
```

What can be valid in line 1? (choose 2)

- a. Course{duration\*10;}
- b. int task=duration+1;
- c. this.duration++;
- d. Course(int plus){this.duration+=plus;}
- e. Course(){this("Java",100);}

<br>

**Question 4**: Given:

```
enum Option{
     ONE(1), TWO(2), THREE(3);
     int r;
     Option(int r){
      this.r=r;
     }
}
record Process(Option... ops){}
```

And the following code:

```
Process p1=new Process(Option.ONE);
Process p2=new Process(Option.TWO);
System.out.print(p1==p2);
System.out.print(p1.ops()[0]);
System.out.print(p2.ops()[0]);
```

What is the result?

- a. true12
- b. falseONETWO
- c. false12
- d. trueONETWO
- e. Compilation error

<br>

**Results**:

- **Question 1**: b, e, f
- **Question 2**: d
- **Question 3**: a, e
- **Question 4**: b
