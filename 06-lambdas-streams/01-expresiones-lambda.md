# 1. Expresiones lambda e interfaces funcionales

# 1.1. Interfaz funcional

- Interfaz que proporciona un único método abstracto
  ```
  public interface Runnable {
       void run();
  }
  ```
  ```
  public interface Interface1 {
       void met(int data);
       default int res() {
            return 1;
       }
  }
  ```
  ```
  public interface Interface2 {
       boolean process(int n, String pt);
       static void print();
  }
  ```

<br>

# 1.2. ¿Qué es una expresión lambda?

- Implementación de una interfaz funcional
- Proporciona el código del único método abstracto de la interfaz, a la vez qeu genera un objeto que implementa la misma
  ```
  Interface1 interface1 = (a)->System.out.println(a); // expresión lambda
  interface1.met(100); // llamada al método sobre el objeto
  ```
- Una expresión lambda tiene dos partes, la lista de parámetros del método y la implementación
  ```
  parametros->implementación
  ```
- Los parámetros pueden indicar o no el tipo
- La lista de parámetros se puede indicar o no entre paréntesis (obligatorio si hay dos o más) y también si se indica el tipo
- En caso de devolver un resultado, la implementación puede omitir la palabra _return_ si consta de una sola instrucción
- Ejemplos

  ```
  () -> 3

  (int a) -> System.out.println("hellow");

  x -> x*x

  (n1, n2) -> {
       n1+=20;
       System.out.println(n1 + n2);
  }
  ```

<br>

# 1.3. Inferencia de tipos

- Es posible inferir el tipo en los parámetros de las expresiones lambda
  ```
  (var a) -> System.out.prinlnt(a);
  ```
- Aunque no se puede combinar inferencia de tipos y tipos específicos en una misma expresión
  ```
  (var a, int c) -> a+c // error de compilación
  ```
- ¿Qué utilidad tiene si ya es posible no indicar el tipo en los parámetros?
  ```
  (@NotNull var c) -> ... // ok
  (@NotNull c) -> ... // error de compilación
  ```

<br>

# 1.4. Comparator con lambdas

- Interfaz utilizada para la ordenación de colecciones y arrays
- Al ser funcional, se puede implementar con lambdas

  ```
  List<String> texts = new ArrayList<>();
  texts.add("my text");
  texts.add("hello");
  texts.add("long text");

  // ordenación de la lista de textos por longitud
  texts.sort((text1,text2) -> text1.length() - text2.length());

  // recorrido y presentación de datos
  for(String text : text) {
       System.out.println(s);
  }

  // hello
  // my text
  // long text
  ```
