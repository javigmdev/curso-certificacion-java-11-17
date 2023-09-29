# 3. Genéricos

# 3.1. Definición

- Permiten que una clase pueda operar con cualquier tipo de objeto Java (no pueden ser primitivos)
- En la definición de la clase se emplea una letra para hacer referencia de forma genérica al tipo
  ```
  class MyClass<T>{}
  ```
- Al crear un objeto de la misma, se debe especificar el tipo concreto con el que se va a trabajar

  ```
  MyClass<String> myClass = new MyClass<>();
  ```

- Clase para encapsulación de cualquier tipo Java

  ```
  public class Bean<T> {
       private T data;

       public Bean(T data) {
            this.data = data;
       }

       public T getData() {
            return data;
       }

       public void setData(T data) {
            this.data = data;
       }
  }
  ```

  ```
     Bean<String> dataString = new Bean<>("hello");
     System.out.println(dataString.getData());
     Bean<Integer> dataNumeric = new Bean<>(30);
     System.out.println(dataNumeric.getData());
  ```

<br>

# 3.2. Tipo genérico como dato

- A la hora de definir un parámetro de tipo genérico, se debe emplear el operador comodín (?)
  ```
  public void print(Bean<?> bean) {
       System.out.println(bean.getData());
  }
  ```
- El método podrá ser llamado con un objeto _Bean_ de cualquier tipo
  ```
  Bean<String> dataString = new Bean<>("hello");
  Bean<Integer> dataNumeric = new Bean<>(30);
  print(dataString);
  print(dataNumeric);
  ```

<br>

# 3.3. Restricciones de tipo

- Se puede definir una clase que solo admita objetos de un determinado subtipo
  ```
  // Cualquier subclase de Number
  class MyClass<T extends Number>{
       ...
  }
  ```
- También al definir parámetros de tipo genérico, se puede utilizar tanto _extends_ como _super_ para establecer restricciones

  ```
  public void print(Bean<? extends Number> bean) {
       System.out.println(bean.getData());
  }

  print(new Bean<String>("hello")); // error de compilación
  print(new Bean<Integer>(30)); // ok
  ```

  ```
  public void print(Bean<? super JButton> bean) {
       System.out.println(bean.getData());
  }

  print(new Bean<String>("hello")); // error de compilación
  print(new Bean<Container>(new Container())); // ok
  ```

<br>

# 3.4. Métodos genéricos

- Una clase no genérica puede incluir métodos que utilicen un tipo genéricos (en parámetros o como resultado)
- Se incluirá la expresión <T> en la definición del método
  ```
  public <T> void m1(T data){}
  public <T extends Number> void m2(T data){}
  public <T> T m3() {}
  ```
- Ejemplo

  ```
  public class GenericMethods {
       public <T> String getType(T data) {
            return data.getClass().getName();
       }
  }
  ```

  ```
  GenericMethods genericMethods = new GenericMethods();
  System.out.println(genericMethod.getType("hello")); // String
  System.out.println(genericMethod.getType(50)); // Integer
  ```
