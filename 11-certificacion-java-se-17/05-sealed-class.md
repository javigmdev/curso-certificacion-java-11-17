# 5. Sealed class (clases selladas)

# 5.1. Introducción

- Clases que pueden ser heredadas solo por ciertas clases
- Más permisivo que _final_, menos que el comportamiento por defecto
  ```
  public sealed class ClaseX permits Class1, Class2 {...}
  ```
- Las subclases deben ser declaradas como _non-sealed_, _sealed_ o final

  ```
  public non-sealed Class1 extends ClassX {...}

  public final Class2 extends ClassX { ... }

  // error de compilación
  public Class3 extends ClassX { ... }

  // error de compilación
  public class Class2 extends ClassX { ... }
  ```

- Las clases implicadas deben formar parte del mismo módulo o, en caso de ser módulos anónimos, deben estar en el mismo paquete
- Si una subclase permitida se define como _non-sealed_, todas las subclases de esta tendrían acceso a la clase base

  ```
  sealed class Parent permits Child {
    public void method() {
      System.out.println("method parent");
    }
  }

  non-sealed class Child extends Parent {}

  class GrandChild extends Child {
    public void test() {
      super.method();
    }
  }
  ```

<br>

# 5.2. Sealed interface

- Las interfaces también pueden ser _sealed_, permitiendo la herencia e implementación solo a ciertas interfaces y clases

  ```
  public sealed interface IParent permits IChild1, Child1 {}

  non-sealed interface IChild1 extends IParent {}

  non-sealed class Child1 implements IParent {}
  ```

- En el caso de una interfaz permitida, esta sólo podrá ser declarada como _non-sealed_ o _sealed_, nunca _final_

<br>

# 5.3. Cláusula permits opcional

- Si la clase o interfaz _sealed_ está en el mismo fichero que las permitidas, puede omitirse la cláusula _permits_

  ```
  // MyClass.java
  public sealed MyClass {}

  final class Other extends MyClass {}
  ```

- También si se trata de una clase o interfaz anidada
  ```
  public sealed interface MyInter {
    non-sealed class C1 implements MyInter {}
  }
  ```
