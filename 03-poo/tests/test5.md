**Question 1**: Which of the following statements are true?

- a. A nested class may be declared static
- b. Local method class may be declared public.
- c. Anonymous inner class may be declared public.
- d. Anonymous inner class may extend an abstract class.

<br>

**Question 2**: Given:

```
public class Main {
     class Student{ //1
          String name;

          Student(String name){ //2
           this.name = name;
          }
     }

     public static void main(String[] args) {
          var student = new Student("Peter"); //3
     }
}
```

Which two independent changes will make the Main class compile? (Choose two.)

- a. Move the entire Student class declaration to a separate Java file, Student.java.
- b. Change line 2 to public Student(String classname)
- c. Change line 1 to public class Student {
- d. Change line 3 to Student student = new Student(“Biology”);
- e. Change line 1 to static class Student {

<br>

**Question 3**: Given:

```
enum Color implements Serializable{
     R(1), G(2), B(3);

     int n;

     public Color(int n){
          this.n = n;
     }
}
```

What action ensures successful compilation?

- a. Replace public Color(int c) with private Color(int c)
- b. Replace int c; with private int c;
- c. Replace int c; with private final int c;
- d. Replace enum Color implements Serializable with public enum Color
- e. Replace enum Color with public enum Color

<br>

**Execution 4**: Given the following:

```
public class Test2 {
     enum Posicion{
          NORTE(2), SUR(1), ESTE(5), OESTE(3);

          int s;

          Posicion(int s){
               this.s = s;
          }
     }

     public static void main(String[] args) {
          Posicion[] pos= { Posicion.NORTE, Posicion.ESTE, Posicion.SUR };
          pos[1].s = 3; //1

          for(Posicion p : pos) {
               System.out.print(p.name() + " ");
          }
     }
}
```

Which is the result?

- a. it prints NORTE OESTE SUR
- b. it prints NORTE ESTE SUR
- c. ir prints nothing
- d. compilation error in line 1

<br>

**Question 5**: Given the code fragment:

```
int m[]={1,2,3,4,5};

for(---){
     System.out.print(m[i]);
}
```

Which option can replace --- to enable the code to print 135?

- a. int i = 0; i <= 4; i ++
- b. int i =0; i <5; i += 2
- c. int i = 1; i <= 5; i += 1
- d. int i = 1; i <5; i +=2

<br>

**Question 6**: Given the following:

```
public static void main(String[] args){
     int a = 5;
     while(isPresent(a)){
          System.out.println(a); //line 1
          //line 2
     }

}
public static boolean isPresent(int a){ //line 3
     return a-->0 ? true : false;
}
```

Which modification enables the code to print 54321?

- a. Replace line 1 with System. out. print (--a) ;
- b. At line 2, insert a --;
- c. Replace line 1 with --a; and, at line 2, insert system. out. print (a);
- d.Replace line 3 With return (a > 0) ?false: true;

<br>

- **Question 1**: a, d
- **Question 2**: a, e
- **Question 3**: a
- **Question 4**: b (sólo se cambia el número)
- **Question 5**: b
- **Question 6**: b
