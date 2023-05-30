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
