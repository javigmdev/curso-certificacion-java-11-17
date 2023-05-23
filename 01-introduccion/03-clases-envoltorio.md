# 3. Clases de envoltorio

# 3.1. Uso

- Encapsulan tipos primitivos como objetos

  ```
  Integer integerNumber = new Integer(200);
  Double decimalNumber = new Double(30.4);

  int integerValue = integerNumber.intValue();
  double decimalValue = decimalNumber.doubleValue();
  ```

- Métodos estáticos para convertir un _String_ en tipo primitivo u objeto

  ```
  int number = Integer.parseInt("300");
  int number2 = Integer.parseInt("100011",2); //35 binario
  Integer number3 = Integer.valueOf("100011",2);
  ```

<br>

# 3.2. Autoboxing/unboxing

- **autoboxing**: se puede asignar directamente el tipo primitivo a la variable objeto
- **unboxing**: se puede recuperar el tipo primitivo asignando directamente la variable primitiva
  ```
  Integer integerNumber = 200; // autoboxing
  Double decimalNumber = 45.7; // autoboxing
  int integerValue = integerNumber; // unboxing
  integerNumber++; // unboxing + autoboxing
  ```

<br>

# 3.3. Inmutabilidad de objetos

- Los objetos de las clases de envoltorio son inmutables, no se pueden modificar
  ```
  Integer integerNumber = 200; // autoboxing
  integerNumber = integerNumber + 100; // genera un nuevo objeto (unboxing + autoboxing)
  ```
