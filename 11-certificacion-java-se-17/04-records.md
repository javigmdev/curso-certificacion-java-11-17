# 4. Records

# 4.1. Características y definición

- Reduce la definición de clases de tipo _JavaBean_
- Se definen con la palabra record, indicando la firma del constructor

  ```
  public record User(String name, String email, int phone) {

  }

  User user = new User("Luke", "mail@mail.com", 666666666);
  ```

- Se genera de forma automática

  - los atributos de la clase
  - la implementación del constructor
  - métodos para recuperación de valores (_getters_)
  - implementaciones de _toString()_ y _equals()_

- Son implícitamente finales, por lo que no pueden ser heredados
- No pueden heredar ninguna clase
- Los atributos son inmutables, no pueden ser modificados
- Los atributos son finales. Si se define explícitamente un constructor, se deben dar valores a todos sus atributos

- _Constructor compacto_: constructor especial que permite realizar validaciones y transformaciones de datos

  ```
  public record Square(int side) {
       public Square { // Se ejecuta después del canónico
            if(side <= 0) {
                 side = 1;
            }
            if(side > 10) {
                 side = side / 2;
            }
       }
  }
  ```

  ```
  Square square1 = new Square(0);
  Square square2 = new Square(12);
  System.out.println(square1.side()); // 1
  System.out.println(square2.side()); // 6
  ```

- _Sobrecarga de constructores_: se peuden incluir constructores adicionales, pero siempre tendrán que llamar al canónico
  ```
  public record Test(int x, int y) {
       public Test(int x) {
            this(x, x);
       }
  }
  ```
