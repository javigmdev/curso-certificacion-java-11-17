# 1. Creación de métodos y sobrecarga

# 1.1. Definición y estructura

- Un método es una función que realiza una tarea. Puede recibir parámetros y devolver un resultado
- Estructura:
  ```
  modificador tipo_devolucion nombre_metodo(parametros){}
  ```
- Ejemplos

  ```
  public int sum(int number1, int number2) {
       return number1 + number2; // devolución
  }

  public void print(int number){
       System.out.println(number);
  }
  // los métodos que no devuelven resultado (void) no necesitan return
  ```

  <br>

# 1.2. Llamada a método

- Los métodos se definen dentro de clases y para llamarlos se debe crear un objeto de la clase y utilizar la sintaxis:
  ```
  objeto.metodo(argumentos);
  ```
- Ejemplo:

  ```
     class Calculator {

          public int sum(int number1, int number2){
               return number1 + number2;
          }

     }

     class Test {

          public static void main(String[] args){
               Calculator calculator = new Calculator();
               int result = calculator.sum(8,3);
          }
     }
  ```

  <br>

# 1.3. Sobrecarga de métodos

- Una clase puede contener varios métodos con el mismo nombre, pero deben diferenciarse en el número o tipo de parámetros

  ```
  public int sum(int number1, int number2){}
  public int sum(int number1){}
  public int sum(long number1){}

  sum(3,9);
  sum(10);
  sum(7L);
  ```

- El tipo de devolución no afecta en la sobrecarga, puede ser el mismo o diferente

- Cuando hay varios posible métodos que se puedan ejecutar en una llamada, primero se intenta coincidencia exacta, después promoción de tipos y en último lugar autoboxing

  ```
  En los siguentes ejemplos cual se ejecutaría primero:

  calculate(4);       void calculate(int number); // 1º coincidencia exacta
                      void calculate(Integer number);

  calculate(4);       void calculate(long number); // 1º promoción tipo
                      void calculate(Integer number);

  calculate(4);       void calculate(Long number);
                      void calculate(Integer number); // 1º autoboxing
  ```
