# 9. Enumeraciones

# 9.1. Definición y estructura

- Una enumeración define un tipo de dato que consiste en una lista de valores posibles
  ```
  public enum Day {
       MONDAY, TUESDAY, WEDNESDAY, THURSDAY, FRIDAY, SATURDAY, SUNDAY;
  }
  ```
- Una variable de un tipo enumerado sólo puede tomar los valores definidos en dicho tipo
  ```
  Day day;
  day = Day.MONDAY;
  ```

<br>

# 9.2. Uso de instrucciones de control

- Las variables de tipo enumerado se pueden utilizar con el operador == para comprobar igualdad
  ```
  if(object == Day.TUESDAY) {}
  ```
- También puede utilizar un tipo enumerado en un switch
  ```
  switch(object) {
       case MONDAY:
            ...
       case TUESDAY:
            ...
  }
  ```

<br>

# 9.3. Constructores

- Una enumeración también puede tener constructores. Estos son privados.
- A cada valor de la enumeración se le asignan los posibles valores de los parámetros del constructor

  ```
  enum Day {
       MONDAY(1), TUESDAY(2), WEDNESDAY(3), THURSDAY(4), FRIDAY(5), SATURDAY(6), SUNDAY(7);

       int data;
       Day(int number) {
            data = number;
       }
  }
  ```

- Cada objeto enumerado tendrá asociado su correspondiente valor
  ```
  Day day = Day.WEDNESDAY;
  System.out.println(day.data); // 3
  ```

<br>

# 9.4. Métodos de una enumeración

- Toda enumeración es una subclase de java.lang.Enum, que proporcieona los siguientes métodos

  - _values_: método estático que devuelve un array con todos los valores de la enumeración
  - _name_: cadena de caracteres con el nombre del valor
  - _ordinal_: posición del valor dentro de la enumeración, siendo 0 la posición del primero
  - _toString_: devuelve el mismo resultado que name()

    ```
    for(var day: Day.values()) {
         System.out.println("Name:" + day.name + " Ordinal: " + day.ordinal() + " toString: " + day.toString());
    }

    // Name: MONDAY Ordinal: 0 toString: MONDAY
    // Name: TUESDAY Ordinal: 1 toString: TUESDAY
    // Name: WEDNESDAY Ordinal: 2 toString: WEDNESDAY
    //...
    ```
