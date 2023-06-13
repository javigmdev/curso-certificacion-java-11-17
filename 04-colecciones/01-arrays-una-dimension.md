# 1. Arrays de una dimensión

# 1.1. Definición

- Conjunto de datos de un mismo tipo a los que se accede mediante una única variable
- Cada dato tiene asociado un índice dentro del array, empezando por la posición 0
- Un array es una estructura de datos estática, una vez definido su tamaño no se puede modificar

<br>

# 1.2. Declaración e instanciación

- Declaración
  - si es variable atributo se inicializa a null
  - si es variable local no se inicializa por defecto
  - no se puede indicar el tamaño en la declaración
    ```
    int []data;
    int data[];
    int data[3];
    ```
- Instanciación
  - Un array se crea como cualquier objeto a través del operador _new_, indicando entre los corchetes el tamaño
  - Cada posición del array se inicializa con el valor por defecto
    ```
    data = new int[10]; // array de 10 enteros
    System.out.println(data[0]); // muestra el valor 0
    ```

<br>

# 1.3. Acceso a elementos y creación abreviada

- Se accede con el nombre de la variable y se indica entre corchetes el índice del elemento
- Si se intenta acceder fuera de los límites del array, se produce una _ArrayIndexOutOfBoundsException_
  ```
  data[] int = new int[10];
  data[0] = 15;
  data[10] = 2; // ArrayIndexOutOfBoundsException<>
  ```
- Se puede declarar, instanciar e inicializar un array en una misma instrucción
  ```
  int[] values = new int[] {3,5,20,11};
  ```
- O de forma más abreviada
  ```
  int[] values = {3,5,20,11};
  ```

<br>

# 1.4. Arrays son objetos

- Un array es un objeto

  ```
  void method() {
       int[] data = new int[5];
       save(data);
       System.out.println(data[0]); // 10
  }

  void save(int[] data) {
       data[0] = 10;
  }
  ```

<br>

# 1.5. Tamaño de un array

- Un array dispone de la propiedad _length_ que permite conocer en cada momento el tamaño del mismo
- La posición del último elemento siempre será _length_-1
  ```
  int[] data = new int[10];
  System.out.println(data.length); // 10
  ```

<br>

# 1.6. Recorrido de un array

- Se puede utilizar un bucle _for_ estándar:
  ```
  int[] data = new int[10];
  for(int i = 0; i < data.length; i++) {
       data[i] = i*2;
  }
  ```
- O un _for each_ si el acceso es para lectura
  ```
  for(int n: data) {
       System.out.println(n);
  }
  ```
