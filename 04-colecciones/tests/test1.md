**Question 1**: given the following:

```
public class Test {
     static int[] n;

     public static void main (String []args) {
          System.out.println(n[0]);
     }

}
```

What is the result?

- a. The output is 0
- b. The output is null
- c. Compilation will fail
- d. NullPointerException

<br>

**Question 2**: Given the following:

```
public class Test {

     public static void main (String []args) {
          int [] n;
          System.out.println(n[0]);
     }

}
```

What is the result?

- a. The output is 0
- b. The output is null
- c. Compilation will fail
- d. NullPointerException

<br>

**Question 3**: Given the following

```
10. float f1 = 4.3f;
11. float [] f2 = new float[5];
12. float [][] f3 = new float [2][];
13. ?
```

Which of the following expresions could be placed in the line 13? (choose two)

- a. f2[2] = f1;
- b. f3[0][0] = f1;
- c. f3[1] = f2[0];
- d. f3[0] = f2;

<br>

**Question 4**: Which of these array instantations are not legal? (choose 3)

- a. String[] str = String[3];
- b. int[]k[] d = new int[3][];
- c. int[][][] s = new int[2][][];
- d. long[][] k = new int[3][4];
- e. String[][] c = new String[][5];
- f. int[][] n = {{4,5,7},{8,9}};

<br>

**Question 5**: Given the following:

```
public class Test {
     public static void main(String[] args) {
          int sum = 0;
          int [][] s = new int[2][];
          s[0] = new int[]{1,1,2};
          //line x
          for(int c[]:s){
               for(int n:c){
                    sum += n;
               }
          }
          System.out.println(sum);
     }
}
```

Which of the following statements must be placed in line x to programas prints 5? (choose 2)

- a. s[1] = 1
- b. s[1] = new int[]{0,1};
- c. s[1] = new int[]{0,0};
- d. s[1] = new int[]{1};

<br>

**Question 6**: Given the following array:

```
int[] mAr = {5,9,12,4,7}
```

Which two code fragments, independently, print each element in this array?

- a.

```
for(int i : mAr){
     System.out.println(mAr[i] + " ");
}
```

- b.

```
for(int i : mAr){
     System.out.println(i+ " ");
}
```

- c.

```
for(int i=0:mAr){
     System.out.println(mAr[i] + " ");
     i++;
}
```

- d.

```
for(int i = 0; i < mAr.length; i++){
     System.out.println(i + " ");
}
```

- e.

```
for(int i = 0;i < mAr.length; i++){
     System.out.println(mAr[i] + " ");
}
```

- f.

```
for(int i; i < mAr.length; i++){
     System.out.println(mAr[i] + " ");
}
```

<br>

**Results**:

- **Question 1**: d
- **Question 2**: b (no se puede usar una variable sin inicializar)
- **Question 3**: a, d
- **Question 4**: a, d, e
- **Question 5**: b, d
- **Question 6**: b, e
