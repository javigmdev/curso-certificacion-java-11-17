**Question 1**: given the following:

```
public class Test {

     static int sum(Integer a, int b) {
          return a + b;
     }

     static long sum(long x, int y) {
          return x + y + 10;
     }

     static double sum(int n, double r) {
          return n + r;
     }

     public static void main (String []args) {
          System.out.println(sum(3,2));
     }

}
```

What is the result?

- a. The output is 5
- b. The output is 15
- c. The output is 5.0
- d. Compilation will fail
- e. It will throw an Exception

<br>

**Question 2**: Given the following:

```
class Number{
     private int n;

     public void setN(int a){
          n = a;
     }

     public int getN(){
          return n;
     }
}

public class Test {

     public static void main (String []args) {
          Number num = new Number();
          processing(num);
          System.out.print(num.getN());

     }

     static void processing(Number x){
          x.setN(x.getN() + 5);
          System.out.print(x.getN());
     }

}
```

What is the result?

- a. The output is 0
- b. The output is 5
- c. The output is 55
- d. Compilation fails

<br>

**Question 3**: Which of the following methods can't be in the same class with: public void mt(long r)? (choose 2)

- a. void mt(int s)
- b. int mt(long a)
- c. int mt()
- d. public void mt(Long a)
- e. void mt(long v)

<br>

**Question 4**: Given the following

```
class Test{
     int a;
     static int b;

     static{
          b++;
     }

     Test(){
          while(a < 5){
               b++;
               a++;
          }
     }

     public static void main(String[] args){
          Test t1=new Test();
          Test t2=new Test();
          System.out.println(t1.a + ":" + t2.b);
     }
}
```

Which is the result?

- a. 10:10
- b. 5:10
- c. 5:11
- d. 11:5
- e. Compilation fails

<br>

**Results**:

- **Question 1**: d (al no haber un método con dos parámetros int, lo siguiente que tiene preferencia, es la promoción de tipo. En estos ejemplos hay dos (long, int) y (int, double). Al no haber ninguna norma de preferencia entre promoción de tipos, el compilador no sabe cual de los dos debe usar y da error)
- **Question 2**: c
- **Question 3**: b, e
- **Question 4**: c
