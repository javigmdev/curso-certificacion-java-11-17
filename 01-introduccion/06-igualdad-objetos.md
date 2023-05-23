# 6. Igualdad de objetos

# 6.1. Operador ==

- Se utiliza para comprobar la igualdad con tipos primitivos
- En variables de tipo objeto compara referencias, no los objetos:

  ```
  String name1 = new String("Jack");
  String name2 = new String("Jack");

  if(name1 == name2){ }  // el resultado es false
  ```

- Al apuntar a objetos diferentes, las referencias también lo son

<br>

# 6.2. Igualdad de cadenas

- Para comparar dos cadenas de caracteres utilizamos el método _equals_

  ```
   String name1 = new String("Jack");
  String name2 = new String("Jack");

  if(name1.equals(name2)){ }  // el resultado es true
  ```

- El método _equals_ distingue mayúsculas y minúsculas. Para ignorar la diferencia, usar _equalsIgnoreCase_

<br>

# 6.3. Pool de cadenas

- Java utiliza un pool de literales de cadenas para optimizar memoria
  ```
  String name1 = "Jack";
  String name2 = "Jack";
  if(name1 == name2) {} // true: apuntan al mismo objeto
  ```
- Al asignar un literal de cadena, no se crea un nuevo objeto, se comprueba si existe en el pool y si es así, se devuelve una referencia del objeto existente. Si no existe, se crea y se graba en el pool

<br>

# 6.4. Igualdad de objetos de envoltorio

- Se aplica lo mismo que para cadenas
  - Diferentes objetos
  ```
  Integer number1 = new Integer(20);
  Integer number2 = new Integer(20);
  if(number1 == number2){} // false
  ```
  - Mismo objeto
  ```
  Integer number1 = 20;
  Integer number2 = 20;
  if(number1 == number2){} // true
  ```
- Se puede utilizar el método _equals_ para comparar los valores envueltos por el objeto

<br>

# 6.5. Igualdad de StringBuilder

- Representa cadenas mutables (modificables)
- No sobrescribe el método _equals_, por lo que _==_ y _equals_ producen el mismo efecto

  ```
  StringBuilder name1 = new StringBuilder("Jack");
  StringBuilder name2 = new StringBuilder("Jack");
  StringBuilder name3 = name2;

  if(name1 == name2) {} // false
  if(name1.equals(name2)) {} // false
  if(name2 == name3) {} // true
  ```

<br>

# 6.6. Inmutabilidad de objetos String

- Un objeto _String_ representa una cadena de caracteres inmutable (no modificable)
- En la concatenación, no se modifica ningún objeto existente, se crea uno nuevo
  ```
  String name = "Tom";
  String surname = "Hardy";
  name = name + surname; // se crea nuevo objeto
  ```
