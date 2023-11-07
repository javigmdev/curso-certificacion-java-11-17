# 3. Codificación segura de aplicaciones

# 3.1. Fundamentos

- Conjunto de buenas prácticas a la hora de conseguir generar código seguro, que evite efectos indeseados ante posibles ataques externos
- Se organizan en nueve secciones
  - Denegación de servicio
  - Confidencialidad
  - Inyección e inclusión
  - Accesibilidad
  - Validación de datos
  - Mutabilidad
  - Construcción de objetos
  - Serialización
  - Control de acceso

<br>

# 3.2. Denegación de servicio

- Se debe comprobar la entrada de datos en un sistema para evitar que cause un consumo excesivo de recursos y que pueda afectar a la CPU o la memoria
- Liberar recursos en todas las situaciones
- Definir un sistema robusto de gestión de errores y excepciones

  ```
  try(resource1 ; resource2) {

  } catch...
  ```

<br>

# 3.3. Confidencialidad

- Los datos confidenciales solo deberían ser visibles dentro de un contexto limitado
- Eliminar información sensible de volcados de error
- No realizar registros de log de información sensible
- Considerar eliminar información sensible de la memoria después de su uso

<br>

# 3.4. Inyección

- Evitar la inyección de SQL mediante el uso de _PreparedStatement_. Utilizar parámetros en la instrucción SQL, en lugar de concatenar valores
  ```
  // incorrecto
  String sql = "select * from people where name = `" + name + "´";
  Statement st = connection.createStatement();
  st.execute(sql);
  ```
  ```
  String sql = "select * from people where name = ?";
  PreparedStatement ps = connection.prepareStatement(sql);
  ps.setParameter(1, name);
  st.execute();
  ```
- Evitar inyección de valores excepcionales en punto flotante

  ```
  if(Double.isNaN(untrusted_double_value)) {
       // specific action for non-number case
  }

  if(Double.isInfinite(unstrusted_double_value)) {
       // specific action for infinite case
  }

  // normal processing starts here
  ```

<br>

# 3.5. Accesibilidad

- Limitar la accesibilidad de clases, métodos y atributos al mínimo requerido por nuestro código
- Limitar la extensibilidad de clases y métodos. Para evitar herencias y sobrescrituras maliciosas, se deben definir como _final_. Si una clase debe usar otra, preferible composición a herencia
- Evitar cambios en una superclase para que las subclases no se vean afectadas

<br>

# 3.6. Validación de datos

- Validar siempre datos de entrada, a fin de evitar que puedan alterar el flujo de nuestro código o corromper el estado de objetos

  ```
  public void process(String name, int value) {
       if(name.equals("")) { ... }

       if(value < 0 && value > 100) { ... }
  }
  ```

- No se debe confiar solo en la validación del lado cliente
- Definir envoltorios alrededor de métodos nativos

<br>

# 3.7. Mutabilidad

- Crear copias de valores de salida mutables. Cuando un método devuelve un dato que es mutable, preferible devolver una copia

  ```
  public class CopyOutput {
       private final java.util.Date date;

       public java.util.Date getDate() {
            return (java.util.Date) date.clone();
       }
  }
  ```

- No exponer colecciones modificables
- Definir atributos públicos estáticos como finales

<br>

# 3.8. Construcción de objetos

- Evitar constructores públicos de clases sensibles
- No establecer valores de atributos en el constructor, hasta que todas las comprobaciones se hayan realizado
- Evitar desde los constructores llamadas a métodos que pueden ser sobrescritos
  ```
  public class Test {
       private int data;
       public Test(int x) {
            if(x < 10) { ... } // validación de parámetros antes de asignación
            method(); // llamada no segura
       }
       public void method() { ... }
  }
  ```

<br>

# 3.9. Serialización

- Evitar la serialización de clases sensibles
- Proteger datos sensibles durante la serialización
- Evitar serializar determinados datos durante el proceso de serialización, definiéndolos como _transient_
  ```
  public class Profile implements Serializable {
       private transient String password;
  }
  ```
- Ser consciente de que durante el proceso de deserialización, se crea un objeto de la clase sin invocar a constructor alguno

<br>

# 3.10. Control de acceso

- Invocaciones seguras mediante _doPrivileged_

  ```
  public class LibClass {
     private static final String OPTIONS = "xx.lib.options";

     public static String getOptions() {
          return AccessController.doPrivileged(
               new PrivilegedAction<String>() {
                    public String run() {
                         // this is checked by SecurityManager
                         return System.getProperty(OPTIONS); // OPTIONS: el valor debe estar "controlado", no permitir cualquier entrada
                    }
               }
          );
     }
  }
  ```

- Las llamadas a propiedades de sistema se realizan desde _doPrivileged_ para que, quien utilice la clase, acceda con los permisos de la misma
