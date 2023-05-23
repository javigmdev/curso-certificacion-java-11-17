**Question 1**: given the code fragment:

```
public static void main(String [] args){ // Line 3
    int ivar = 100; // Line 4
    float fvar = 23.4f; // Line 5
    double dvar = 20; // Line 6
    ivar = fvar; // Line 7
    fvar = ivar; // Line 8
    dvar = fvar; // Line 9
    fvar = dvar; // Line 10
    dvar = ivar; // Line 11
    ivar = dvar; // Line 12
} // Line 13
```

which three lines fails to compile?

- a. Line 7
- b. Line 8
- c. Line 9
- d. Line 10
- e. Line 11
- f. Line 12

<br>

**Question 2**: Which of the following compiles with no errors? (choose 4)

- a. int a = 2.7;
- b. byte n = (byte) 4546.9;
- c. int c = 0b110_100;
- e. double t = \_6.4;
- f. float g = 23;
- g. short k = (short)45L;
- h. boolean n = (boolean)1;
- i. char vv = 300000;

<br>

**Question 3**: Given:

```
public class User{
     int num;

     public static void save(User obj4){
          obj4.num+=10;
     }

     public static void main(String[] args){
          User obj1=new User();
          User obj2=obj1;
          User obj3=null
          obj2.num=60;
          save(obj2);
     }
}
```

How many User instances are created at runtime?

- a. 1
- b. 2
- c. 3
- d. 4

<br>

**Question 4**: Given:

```
public class Test { // Line 1
     public static void main(String[] args){ // Line 2
          Integer ten, twenty; // Line 3
          ten=new Integer (10); // Line 4
          twenty=new Integer(20); // Line 5
          ten=twenty; // Line 6
          ten=null; // Line 7
     } // Line 8
} // Line 9
```

When the objects created in lines 10 and 20 will be elegible for Garbage collection ?

- a. Both in line 8
- b. Both in line 9
- c. Both in line 7
- d. 10 in line 6 and 20 in line 7
- e. 10 in line 6 and 20 in line 8

<br>

**Question 5**: Given the following code:

```
Integer k = 5; // Line 1
int p = 10, s; // Line 2
k = k + p; // Line 3
s = k; // Line 4
System.out.println(s); // Line 5
```

What is the result?

- a. 15
- b. 5
- c. Compilation error in line 3
- d. Compilation error in line 4

<br>

**Results**:

- **Question 1**: a, d, f
- **Question 2**: b, c, f, g
- **Question 3**: a
- **Question 4**: e
- **Question 5**: a
