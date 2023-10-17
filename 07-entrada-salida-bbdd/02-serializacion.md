# 2. Serialización

# 2.1. Características

- Proceso mediante el cual un objeto es transformado en un conjunto de unos y ceros para poder ser almacenado en un fichero o enviado por una red
- Todo objeto serializado debe ser posteriormente convertido a su estado original en un proceso de deserialización
- Para que un objeto pueda ser serializado, su clase debe implementar _Serializable_

<br>

# 2.2. Interfaz Serializable

- Interfaz del paquete _java.io_
- No contiene ningún método, pero debe ser implementada por una clase para que sus objetos puedan ser serializados
  ```
  class Person implements Serializable {
       ...
  }
  ```
- Las clases de envoltorio, _String_ y las clases de colección ya implementan esta interfaz

<br>

# 2.3. Escritura de objeto en un fichero

- Un objeto serializable puede ser almacenado en un fichero utilizando la clase _ObjectOutputStream_
- El objeto es serializado durante el proceso de escritura
  ```
  class Person implements Serializable { ...}
  ```
  ```
  String dir = "/user/data.obj";
  try(FileOutputStream fos = new FileOutputStream(dir);
       ObjectOutputStream out = new ObjectOutputStream(fos)) {
            out.writeObject(new Person(..));
  } catch(IOException ex) { ... }
  ```

<br>

# 2.4. Lectura de objeto de un fichero

- Para recuperar un objeto almacenado en un fichero utilizamos _readObject()_ de la clase _ObjectInputStream_
- Se debe reawlizar un casting al tipo específico
  ```
  class Person implements Serializable { ...}
  ```
  ```
  String dir = "/user/data.obj";
  try(FileInputputStream fis = new FileInputStream(dir);
       ObjectInputStream in = new ObjectInputStream(fis)) {
            in.readObject(new Person(..));
  } catch(IOException ex) { ... }
  ```

<br>

# 2.5. Atributos transient

- Si a la hora de serializar un objeto, se necesita que alguno de sus atributos no sea serializado, deberá estar declarado como _transient_
- Se utiliza con campos sensibles que por seguridad, no queremos serializar
- Al recuperar un objeto serializado, el valor del atributo con _transient_ es _null_
  ```
  class Perfil implements Serializable {
       private transient String password;
       ...
  }
  ```
