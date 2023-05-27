# 6. Encapsulación

# 6.1. Definición

- Principio que se basa en mantener como privados los atributos que definen características de un objeto, proporcionando acceso a los mismos a través de métodos y constructores
- Evita que se pueda corromper el objeto

  ```
  public class User {
       String name;
       int age;
  }

  class Test {
       void method() {
            User user = new User();
            user.age = -2; // no tendría sentido
       }
  }
  ```

- EL acceso a los atributos se realiza de forma controlada a través de métodos _getter_ y _setter_
- El constructor permite inicializar los atributos durante la creación del objeto

  ```
  public class User {

       private String name;
       private int age;

       public User(String name, int age) {
            this.name = name;
            if(age > 0) this.age = age;
       }

       public String getName() {
            return name;
       }

       public void setName(String name) {
            this.name = name;
       }

       public int getAge() {
            return age;
       }

       public void setAge(int age) {
            if(age > 0) this.age = age;
       }
  }
  ```
