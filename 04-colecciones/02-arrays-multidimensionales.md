# 2. Arrays multidimensionales

# 2.1. Fundamentos

- Se pueden crear en java arrays de varias dimensiones
  ```
  int[][] ar; // 2 dimensiones
  int[]ar[];  // 2 dimensiones
  int [][][] ar2; // 3 dimensiones
  ```
- Para crear el array se asigna tamaño a las dos dimensiones
  ```
  ar = new int[3][4]; // array de 12 elementos
  ar2 = new int[2][5][10]; // array de 100 elementos
  ```
- El acceso a los elementos se realiza con un índice por dimensión
  ```
  ar[1][2] = 23;
  ar2[0][3][8] = 8;
  ```

<br>

# 2.2. Recorrido

- Con _for_ estándar
  ```
  int[][] nums = new int[5][7];
  for(int i = 0; i < nums.length; i++) {
       for(int k = 0; k < nums[i].length; k++) {
            System.out.println(nums[i][j]);
       }
  }
  ```
- Con _for each_
  ```
  int[][] nums = new int[5][7];
  for(int[] i : nums) {
    for(int k : i) {
         System.out.println(k);
    }
  }
  ```

<br>

# 2.3. Arrays irregulares

- A la hora de crear un array multidimensional, se pueden dejar las últimas dimensiones sin asignar tamaño
  ```
  int[][] d = new int[5][];
  int[][][] n = new int[4][][];
  int[][][] v = new int[2][10][];
  int[][][] h = new int[6][][4]; // error de compilación, no se pueden dejar dimensiones intermedias sin asignar
  ```
- A cada posición definida se le puede asignar un array con tantas dimensiones como queden sin tamaño
  ```
  d[0] = new int[4];
  d[2] = new int[7];
  n[1] = new int[4][2];
  v[0][0] = new int[6];
  ```
- Dados los siguientes arrays
  ```
  int[] a = new int[10];
  long[][] b = new long[2][3];
  int[][] c = new int[3][];
  long[][][] d = new long[5][][];
  ```
  - Las siguientes instrucciones son correctas:
    - b[0][0] = a[1];
    - c[1] = a;
    - d[0] = b;
  - Las siguientes son incorrectas (error de compilación):
    - c[0][0] = a[1]; // no se ha dado tamaño a la segunda dimensión
    - c[2] = a[3]; // en la primera dimensión de c se debe asignar un array
    - d[1] = a; // tiene que ser array de dos dimensiones
    - d[0] = c; // misma dimensión, pero un array de int no se puede asignar a una variable array de long

<br>

# 2.4. Creación abreviada

- Igual que ocurre con los arrays de una dimensión, un array multidimensional puede declararse, crearse e inicializarse en una única instrucción
  ```
  int[][] data = {{3,5,8,3},{8,2,1}};
  ```
- Se pueden dejar las últimas dimensiones sin asignar tamaño e inicializarlas después
  ```
  int[][] data = new int[2][];
  data[0] = new int[]{2,7,1};
  data[1] = {5,9}; // error, no se admite forma simplificada
  ```
