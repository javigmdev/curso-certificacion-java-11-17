# 3. Entrada-salida java.nio

# 3.1. Paquete java.nio.files

- Nuevo paquete de entrada/salida para lectura y escritura en ficheros
- Principales clases e interfaces de este paquete
  - _Path_: representa una ruta a un fichero o directorio
  - _Paths_: clase utilizada para crear instancias de _Path_
  - _Files_: dispone de diversos métodos estáticos para obperar contra un fichero o directorio

<br>

# 3.2. Interfaz Path

- Representa una ruta a un fichero o directorio
- Para crear una implementación
  - Método _of_ de _Path_
    ```
    Path path = Path.of("/users/mydata.txt");
    ```
  - Método _get_ de _Paths_
    ```
    Path path = Paths.get("/users/mydata.txt");
    ```

<br>

# 3.3. Métodos de Path

- Proporciona métodos para obtener información sobre la ruta
  - _Path getFileName()_: nombre del fichero o último elemento del _Path_
    ```
    Path path1 = Path.of("/user/mydata.txt");
    Path path2 = Path.of("/a/b";
    System.out.println(path1.getFileName()); // mydata.txt
    System.out.println(path2.getFileNime()); // b
    ```
  - _Path toAbsolutePath()_: ruta completa del fichero o directorio
    ```
    Path path1 = Path.of("c:\\user\\mydata.txt");
    Path path2 = Path.of("data.txt");
    System.out.println(path1.toAbsolutePath()); // c:\user\mydata.txt
    System.out.println(path2.getFtoAbsolutePathileNime()); // c:\practices\..\data.txt (ruta completa desde el directorio actual)
    ```
- _Path normalize()_: resuelve las rutas relativas y devuelve el path normalizado
  ```
  String url = "c:\\temp\\..\\data.txt";
  Path path1 = Paths.get(url);
  System.out.println(path1.normalize()); // c:\data.txt
  ```
- _Path relativize(Path other)_: devuelve la ruta relativa de _other_ respecto al path principal
  ```
  Path path1 = Path.of("c:\\temp\\mydata.txt");
  Path path2 = Path.of("c:\\temp\\..\\data.txt");
  System.out.println(path1.relativize(path2)); // ..\..\data.txt
  ```
  - Si uno es ruta absoluta y el otro no, se producirá una excepción
  - Al aplicar _relativize_, las dos rutas son internamente normalizadas primero
- _Path resolve(Path other)_: resuelve la ruta de _other_ frente a la principal
  ```
  Path path1 = Paths.get("c:\\temp\\..\\data.txt");
  Path path2 = Paths.get("new.txt");
  System.out.println(path1.resolve(path2)); // c:\temp\..\data.txt\new.txt
  ```
  - Si other es ruta absoluta, se devuelve esa misma ruta
- _int getNameCount()_: devuelve el número de elementos del path, sin incluir el raíz
  ```
  Path path1 = Path.of("c:\\temp\\..\\mydata.txt");
  System.out.println(path1.getNameCount()); //3
  ```
- _Path getName(int index)_: devuelve la parte del path que ocupa la posición indicada. El primer elemento (sin incluir la raíz) tiene índice 0
  ```
  Path path1 = Path.of("c:\\temp\\..\\mydata.txt");
  System.out.println(path1.getName(2)); // mydata.txt
  ```

<br>

# 3.4. Lectura de un fichero con Files

- La clase _Files_ proporciona los siguientes métodos estáticos para leer el contenido de un fichero

  - _Stream<String> lines(Path path)_: devuelve un _Stream_ con todas las líneas del fichero. A partir de ahí, se pueden aplicar los métodos de streams para realizar búsquedas, transformaciones, filtrados, etc
  - _List<String> readAllLines(Path path)_: devuelve una lista con las cadenas del fichero, donde cada elemento corresponde con una línea
    ```
    Path path1 = Path.of("c:\\user\\mydata.txt");
    List<String> data = Files.readAllLines(path1);
    data.forEach(line -> System.out.prinln(line));
    ```
  - _BufferedReader newBufferedReader(Path path)_: devuelve un objeto _BufferedReader_ para realizar la lectura de forma clásica

<br>

# 3.5. Escritura en ficheros con Files

- Para realizar la escritura en ficheros, la clase _Files_ proporciona los siguientes métodos
  - _writeString(Path path, CharSequence csq, CharSet cs, OpenOption... options)_: escribe en el fichero indicado como primer parámetro, la cadena especificada en el segundo, utilizando el juego de caracteres del tercero y las opciones de escritura del cuarto
    ```
    try {
         Path path = Path.of("c:\\user\\mydata.txt");
         Files.writeString(p1, "new text",
                             Charset.forName("UTF-8"),
                             StandardOpenOption.APPEND); // escritura en modo append
    } catch(IOException ex) {
         ex.printStackTrace();
    }
    ```
    - _write(Path path, Iterable<? extends CharSequence>, Charset cs, OpenOption... options)_: escribe en el fichero indicado como primer parámetro, la colección de cadenas especifica en el segundo, utilizando el juego de caracteres del tercero y las opciones de escritura del cuarto
    ```
    List<String> days = List.of("monday", "tuesday", "wednesday", "thursday", "friday", "saturday", "sunday");
    try {
         Path path = Path.of("c:\\user\\mydata.txt");
         Files.write(path, days,
                             Charset.forName("UTF-8"),
                             StandardOpenOption.APPEND);
    } catch(IOException ex) {
         ex.printStackTrace();
    }
    ```

<br>

# 3.6. Otros métodos de Files

- _static Path copy(Path source, Path target, CopyOption... options)_: copia el contenido de un fichero en otro
  - Si el fichero _target_ ya existe y no se indica opción, se produce una excepción. Aunque si ambas rutas son iguales, el método se ejecuta si cambios
  - Si _source_ es un directorio, se creará en _target_ un directorio vacío
  - Si _target_ es un directorio, _FileAlreadyExistsException_
  - Si el tercer parámetro es _StandardCopyOption.REPLACE_EXISTING_, el fichero _target_ será sustituido en caso de que exista
  - Si el tercer parámetro incluye _StandardCopyOption.COPY_ATTRIBUTES_, se copiarán también las propiedades del fichero origen en el destino
- _static void delete(Path path)_: elimina el fichero si existe, si no se produce una excepción. Si es un directorio, deberá estar vacío
- _static void deleteIfExists(Path path)_: elimina el fichero si existe, sino no hace nada. Si es un directorio, deberá estar vacío
- _static Path createFile(Path path, FileAttribute<?> ...attrs)_: crea el fichero indicado vacío. Si el fichero ya existe, se produce una excepción
