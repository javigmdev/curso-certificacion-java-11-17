# 2. Ciclo de vida de los objetos

# 2.1. Creación de un objeto

- Un objeto se crea a partir del operador _new_, seguido del nombre de la case
- Se devuelve una referencia al objeto que se guarda en una variable de la clase

```
User user = new User();
String name = new String("Bob");
Object object = new Object();
```

<br>

# 2.2. Constructores

- Se ejecutan durante la creación del objeto

  ```
  User user = new User();

  class User {
       public User(){
            // código constructor
       }
  }
  ```

- Pueden sobrecargarse (varios constructores)

  ```
  public User() {}

  public User(String name){}
  ```

<br>

# 2.3. Destrucción de un objeto

- Los objetos son eliminados de la memoria por el _Garbage Collector_
- Un objeto es elegido para recolección, cuando no hay referencias del mismo
- Cuando un objeto es elegido para recolección, la _JVM_ llama al método _finalize()_ del objeto. Dicho método solo puede ser llamado una o ninguna vez durante la vida de un objeto

  ```
  public void method(){
       User user1 = new User();
       User user2 = new User();
       user2 = user1; // user1 a recolección
       user2 = null;
  } // user2 a recolección
  ```
