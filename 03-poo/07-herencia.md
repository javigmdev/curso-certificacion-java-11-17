# 7. Herencia

# 7.1. Definición

- Herencia es una característica que permite crear nuevas clases a partir de clases ya existentes, de forma que la nueva clase adquiera (herede) los miembros de la ya existente
- A la clase _padre_ se le conoce como _superclase_, mientras que a la clase _hija_ es la _subclase_
  -Se usa la palabra _extends_

  ```
  class ClassA {
  public void method() {}
       }

  class ClassB extends ClassA {
       // automáticamente adquiere el método
  }
  ```

- El principal beneficio de la herencia es la reutilización de código
- Una clase sólo puede heredar otra clase, aunque la superclase puede heredar a su vez otra y así hasta n nivel
- Varias clases pueden heredar la misma clase
- Los miembros privados de la superclase no son accesibles directamente desde la subclase
- Para impedir que una clase se pueda heredar, se define con _final_

  ```
  final class ClassA {
       public void method();
  }

  class ClassB extends ClassA {} // error de compilación
  ```

<br>

# 7.2. Herencia de Object

- Todas las clases java heredan de _Object_
- Si una clase no hereda explícitamente otra clase, implícitamente heredará _Object_
  ```
  class Test {}     equivale a      class Test extends Object {}
  ```
- Todas las clases disponen de los métodos de _Object_, entre ellos _toString_, _equals_ y _hashCode_

<br>

# 7.3. Constructores

- Toda clase incluye de forma implícita en sus constructores como primera línea de código la instrucción _super();_, que es una llamada al constructor sin parámetros de la superclase

  ```
  class ClassA {
     public ClassA(int a) {
          System.out.println(a);
     }
  }

  // equivale a

  class ClassA {
     public ClassA(int a) {
          super();
          System.out.println(a);
     }
  }
  ```

- Si la superclase no dispone de constructor sin parámetros, se produce un error de compilación en la subclase

- Es posible llaar a otro constructor de la superclase que no sea el contructor sin parámetros. Para ello, se usa la instrucción _super_

  ```
  class ClassA {
       ClassA(int a) {}
  }

  class ClassB extends ClassA {
       ClassB(int x){
            super(x); // debe ser la primera instrucción
            System.out.println("Class B");
       }
  }
  ```

  ```
  class ClassA {
      ClassA(int a) {}
  }

  class ClassB extends ClassA {
      ClassB(int x){
           super(x); // debe ser la primera instrucción
           System.out.println("Class B");
      }

      ClassB() {
         this(10); // Llamada a otro constructor
      }
  }
  ```

<br>

# 7.4. Sobrescritura de métodos

- Cuando una clase hereda un método de otra puede sobrescribirlo, lo que significa que vuelve a definirlo en la nueva clase

  ```
  class ClassA {
       public void test() {
            System.out.println("Class A");
       }
  }

  class ClassB extends ClassA {
       // se vuelve a definir el método
       @Override
       public void test() {
            System.out.prinln("Class B");
       }
  }

  ClassB classB = new ClassB();
  classB.test(); // impreme Class B
  ```

- La anotación _@Override_ indica al compilador que se está intentando sobrescribir un método. Su uso no es obligatorio, pero si conveniente

- A la hora de sobrescribir un método se deben seguir las siguientes reglas:
  - El nombre y la lista de parámetros debe ser idéntico
  - El ámbito debe ser igual o menos restrictivo
  - El tipo de devolución debe ser igual o un subtipo del original
  - La nueva versión del método no debe propagar excepciones que no estén definidas en el original (esta restricción NO afecta a las excepciones _Runtime_)
- Ejemplos

  ```
  class ClassA {
       public Object test(){}
  }

  class ClassB extends ClassA {
       @Override
       public String test() {} // tipo de devolución subclase de object
  }
  ```

  ```
  class ClassA {
       void test(){}
  }

  class ClassB extends ClassA {
       @Override
       public void test() {} // ámbito superior a (default)
  }
  ```

  ```
  class ClassA {
       void test() throws IOException {}
  }

  class ClassB extends ClassA {
       @Override
       public void test() throws FileNotFoundException {} // subtipo de IOException
  }
  ```

<br>

# 7.5. Tipo de objeto y tipo de referencia

- En java se puede asignar una referencia a un objeto de un tipo en una variable del tipo de su superclase
  ```
  Object object = new String("hello");
  ```
- El tipo de la referencia (_Object_) es superclase del tipo del objeto (_String_)
- Se aplica a varios niveles

  ```
  class ClassB extends ClassA {}
  class ClassC extends ClassB {}

  ClassA classA = new ClassC();
  ```

- Con esta referencia se puede llamar a métodos del objeto, pero sólo a aquellos que han sido heredados o sobrescritos

  ```
  Object object = new String("hello");
  System.out.println(object.toString()); // correcto, llamada a método toString() de String

  if(object.equals("hello")) {} // correcto, llamada a equals() de String

  System.out.println(object.length()); // error de compilación, length() es un método propio de String, no existe en object
  ```

## Casting entre tipos objeto

- Para obtener una referencia al tipo original del objeto se puede efectuar un casting
  ```
  String s = (String)object;
  ```
- El compilador permite hacer casting de una referencia de un tipo a cualqiuer tipo de sus subclases, pero si el objeto no es de ese tipo se producirá una _ClassCastException_
  ```
  Integer number = (Integer)object;
  // Esta instrucción compila correctamente, pero al ejecutarla se producirá una excepción ClassCastException,
  // ya que el tipo de objeto referenciado por object es String, no Integer
  ```

<br>

# 7.6. Clases abstractas y polimorfimso

## Clases abstractas

- Clases que cuentan, al menos, con un método abstracto, que es aquel que está declarado en la clase pero no implementado
- Tanto la clase como los métodos abstractos se definen con la palabra _abstract_
  ```
  abstract class ClassA {
       public abstract int calculate();
  }
  ```
- No es posible crear objetos de una clase abstracta
- Además de métodos abstractos, las clases abstractas pueden incluir atributos, constructores y métodos estándares
- Una clase que herede una clase abstracta está obligada a sobrescribir los métodos abstractos heredados (o declararse también como abstract)
- El objetivo de los métodos abstractos es forzar a que todas las subclases tengan el mismo formato de método

  ```
  abstract class Figure {
       private String color;

       public Figure(String color) {
            this.color = color;
       }

       public abstract double area();
  }
  ```

  ```
  class Circle extends Figure {
       private int radio;

       public Circle(String color, int radio) {
            super(color);
            this.radio = radio;
       }

       public double area() {
            return Math.PI*radio*radio;
       }
  }
  ```

  ```
  class Triangle extends Figure {
       private int base, altura;

       public Circle(String color, int base, int altura) {
            super(color);
            this.base = base;
       }

       public double area() {
            return base * altura / 2;
       }
  }
  ```

<br>

## Polimorfismo

- Se basa en la asignación de referencias a objetos de subclases en variables de su superclase (abstractas o no)
- Consiste en utilizar una misma instrucción para llamar a diferentes versiones de un mismo método
  ```
  Figure figure = new Triangle(...);
  figure.area(); // método área de Triangle
  figure = new Circle(...);
  figure.area(); // método área de Circle
  ```
- Principales ventajas:
  - reutilización de código
  - flexibilidad
  - dinamismo

<br>

## Métodos abstractos vs finales

- Lo contrario a un método abstracto es un método final
- Un método final es aquel que no puede ser sobrescrito. El modificador _final_ se utiliza delante del tipo

  ```
  class ClassA {
       public final int calculate();
  }

  class ClassB extends ClassA {
       public int calculate(); // error de compilación
  }
  ```

<br>

# 7.7. Interfaces

- Una interfaz es un conjunto de métodos abstractos
- Su objetivo es definir el formato de ciertos métodos, que posteriormenete las clases se encargarán de implementar
- También puede incluir constantes, que serán públicas y estáticas
- Se define con la palabra reservada _interface_

  ```
  public interface InterfaceA {
       int number = 10;

       int sum(int total);
  }
  ```

- En el caso de las constantes, se omiten las palabras _public_, _final_ y _static_
- Como los método solo pueden ser públicos y abstractos, se pueden omitir las palabras _abstract_ y _public_

<br>

## Implementación de una interfaz

- Una clase que implementa una interfaz está obligada a sobrescribir (implementar) todos los métodos de la misma

  ```
  public class Test implements InterfaceA {

       public int sum(int total) {}

  }
  ```

<br>

## Flexibilidad de las interfaces

- Una clase puede implementar varias interfaces
  ```
  public class Test implements InterfaceA, InterfaceB {
       // implementación de todos los métodos de ambas interfaces
  }
  ```
- Una clase puede heredar otra clase y, a su vez, implementar una o varias interfaces
  ```
  public class Test extends Figure implements InterfaceA, InterfaceB {
       // implementación de todos los métodos de ambas interfaces
  }
  ```

<br>

## Herencia múltiple en interfaces

- Una interfaz puede heredar una o varias interfaces

  ```
  public interface InterfaceA {
     void method1(int number);
     int method2();
  }
  ```

  ```
  public interface InterfaceB {
     void method3();
  }
  ```

  ```
  public interface InterfaceC extends InterfaceA, InterfaceB {
     void method4();
  }
  ```

  ```
  public class Test implements InterfaceC {
     public void method1(int number) {}
     public int method2() {}
     public void method3() {}
     public void method4() {}
  }
  ```

  <br>

## Polimorfismo con interfaces

- Mediante una interfaz, se puede hacer referencia a un objeto que la implementa
- Con esta referencia se podría llamar a las implementaciones de los métodos declarados en la de la interfaz, pudiendo llevar a cabo el polimorfismo a través de las interfaces

  ```
  interface TestInterface {
       int CONV = 8.75;

       void method1(int x);
       int method2(String s);
  }
  ```

  ```
  class Test implements TestInterface {
       public void method1(int x) {}
       public int method2(String s) {}
       public void ownMethod() {}
  }
  ```

  ```
  Test test = new TestInterface();
  test.method1(10);
  test.method2("hello");
  test.ownMethod(); // Error de compilación
  ```

- Se puede llamar a las constantes con la interfaz o con las clases que la implementan
  ```
  TestInterface.CONV;
  Test.CONV;
  ```

<br>

## Novedades en Java 8 y 9

- Proporciona una implementación por defecto, que puede ser utilizada por las clases que implementan la interfaz
- Se definen con la palabra reservada _default_

  ```
  public interface Operations {
       default void printNumber(int number) {
            System.out.println("Number:" + number);
       }

       int calculate(int number);
  }
  ```

  ```
  public class ClassA implements Operations {
       public int calculate(int number) {}

       // Es obligatorio implementar el método abstracto, aunque se podría sobrescribir también el default
  }
  ```

  ```
  public class Test {
       public static void main(String[] args) {
            ClassA classA = new ClassA();
            classA.print(30); // utiliza la implementación por defecto
       }
  }
  ```

- Desde Java 8, las interfaces pueden incluir métodos estáticos al igual que las clases
- El método está asociado a la interfaz, no es heredado por las clases que la implementan

  ```
  interface InterfaceA {
       static void method() {
            System.out.println("static method");
       }
  }
  ```

  ```
  public class ClassA implements InterfaceA {}
  ```

  ```
  public class Test {

       public static void main(String[] args) {
            ClassA classA = new ClassA();
            classA.method(); // error de compilación
            classA.method(); // error de compilación
            InterfaceA.method(); // static method
       }

  }
  ```

- Desde Java 9, se pueden incluir métodos privados en las interfaces. Son utilizados desde métodos _default_

  ```
  interface InterfaceA {

       private int calculateLargest(int number1, int number2) {
            return (a > b) ? a : b;
       }

       private int calculateSmallest(int number1, inte number2) {
            return (a < b) ? a: b;
       }

       default sum(int number1, int number2) {
            int s = 0;

            for(int i = calculateSmallest(number1, number2); i < calculateLargest(number1, number2); i++) {
                 s += i;
            }
            return s;
       }
  }
  ```

  ```
  public class Test {

       public static void main(String[] args) {
            InterfaceA interfaceA = new Interface();
            System.out.println("Sum" + interfaceA.sum(10, 5));
       }

  }
  ```

- Los métodos privados también pueden ser estáticos, pudiendo ser llamados desde otros métodos estáticos o _default_ de la interfaz

<br>

## Problema de herencia múltiple

- Si una clase implementa dos interfaces con el mismo método _default_, está obligada a sobrescribirlo

  ```
  interface InterfaceA {
       dafult void method() {
            System.out.println("default interfaceA");
       }
  }
  ```

  ```
  interface InterfaceB {
       dafult void method() {
            System.out.println("default interfaceB");
       }
  }
  ```

  ```
  class Test implements InterfaceA, InterfaceB {

       // error de compilación si no se sobrescribiese
       public void method() {
            System.out.print("Implementation test");
       }
  }
  ```

## Interfaces funcionales

- Concepto introducido en java 8 para denominar a las interfaces que disponen de un único método abstracto
- Se pueden crear implementaciones de estas interfaces a través de expresiones lambda
- Pueden, opcionalmente, estar definidas con la anotación _@FunctionalInterface_
- Ejemplos interfaces funcionales

  ```
  interface InterfaceA {
       default void defaultMethod() {
            System.out.println("default InterfaceA");
       }

       int method();
  }
  ```

  ```
  interface InterfaceB extends InterfaceA {
       static void print() {
            System.out.println("static Interface B");
       }
  }
  ```

  ```
  @FunctionalInterface
  interface InterfaceC {
       void method();
       String toString();
       // los métodos abstractos que coincidan con algún método de Object NO se tiene en cuenta de cara a la característica de ser funcional
  }
  ```

- Ejemplos no funcionales

  ```
  interface InterfaceD extends InterfaceA {
       int method(int p); // no puede haber dos abstractos, aunque sea sobrecarga
  }
  ```

  ```
  interface InterfaceE extends InterfaceA {
       // implementa método, por lo que ya no tiene métodos abstractos
       default int method() {
            return 10;
       }
  }
  ```
