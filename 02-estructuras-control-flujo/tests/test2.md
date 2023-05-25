**Question 1**: given the code fragment:

```
public class Test {

     public static void main(String[] args) {
          int a = 0, s = 0, i = 1;
          principal: for(;i < 10; i++) {
               while(a < 5) {
                    a = i++;
                    s = a+i;
                    if(s >= 10) {
                         break principal;
                    }
               }
          }
          System.out.println(i + ":" + a + ":" + s);
     }

}
```

What is the result?

<br>

**Question 2**: Given the following:

```
public class Runner {
     static int a = 1;

     public static void main (String []args) {
          int b = 6;
          while (a++) {
               b--;
          }
          System.out.println("a=" + a + " b =" + b);
     }

}
```

What is the result?

- a. The output is a = 6 b = 0
- b. The output is a = 7 b = -1
- c. The output is a = 6 b = -1
- d. The output is a = 7 b = 0
- e. Compilation will fail.

<br>

**Question 3**: Given the code fragment:

```
public static void main(String[] args){
     int x = 0;
     int y = 7;
     for(x = 0; x < y - 1; x = x + 2){
          System.out.println(x + " ");
     }
}
```

What is the result?

- a. 2 4
- b. 0 2 4 6
- c. 0 2 4
- d. Compilation fails

<br>

**Question 4**: Given the code fragment:

```
public static void main(String[] args){
     String[] cars = {"A","B","C","D"};
     for(int i = 0; i < cars.length; i++){
          System.out.print(cars[i] + " ");
          if(cars[i].equals("C")){
               continue;
          }
          System.out.println("End");
          break;
     }
}
```

What is the result?

- a. A B C End
- b. A B C D End
- c. A End
- d. Compilation fails

<br>

**Question 5**: Given the code fragment:

```
public static void main(String[] args){
     String[][] cars = {{"A","B","C"},{"D","E"}};
     ex: for(int i=0; i < cars.length; i++){
          for(int k=0; k < cars[i].length; k++){
               System.out.print(cars[i][k] + " ");
               if(cars[i][k].equals("B")){
                    break;
               }
               continue ex;
          }
     }
}
```

What is the result?

- a. A B C
- b. A D
- c. A B D E
- d. Compilation fails.

<br>

**Question 6**: Given the code fragment:

```
int m[] = {1,2,3,4,5};
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

**Question 7**: Given the following:

```
public static void main(String[] args){
     int a = 5;
     while(isPresent(a)){
          System.out.print(a); //line 1
          //line 2
     }
}

public static boolean isPresent(int a){ //line 3
     return a-- > 0 ? true : false;
}
```

Which modification enables the code to print 54321?

- a. Replace line 1 with System. out. print (--a) ;
- b. At line 2, insert a --;
- c. Replace line 1 with --a; and, at line 2, insert system. out. print (a);
- d. Replace line 3 With return (a > 0) ?false: true;

<br>

**Results**:

- **Question 1**: 6:5:11
- **Question 2**: e
- **Question 3**: c
- **Question 4**: c
- **Question 5**: b
- **Question 6**: b
- **Question 7**: b
