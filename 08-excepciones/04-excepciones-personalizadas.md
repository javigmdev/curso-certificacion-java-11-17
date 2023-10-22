# 4. Excepciones personalizadas

# 4.1. Introducción

- Se puede crear una excepción personalizada definiendo una clase que herede _Exception_

  ```
  class TestException extends Exception {...}
  ```

  ```
  class MyClass {
       // propaga la excepción que lanza
       public void method() throws TestException {
            ...
            throw new TestException();
       }
  }
  ```

  ```
  MyClass myClass = new MyClass();
  try {
       // al utilizar method() se debe capturar la excepción
       myClass.method();
  } catch(TestException ex) {
       ...
  }
  ```
