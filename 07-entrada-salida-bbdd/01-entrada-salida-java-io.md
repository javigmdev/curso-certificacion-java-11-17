# 1. Entrada-salida java.io

# 1.1. Salida

- Entre las principales clases para operaciones de salida de datos, están
  - _OutputStream_: clase abstracta que representa un flujo de salida
  - _PrintStream_: subclase de _OutputStream_ que proporciona métodos para enviar datos a cualquier flujo de salida
  - _FileOutputStream_: subclase de _OutputStream_ que representa un flujo de salida asociado a un fichero
  - _FileWriter_: clase específica para estructura de texto de un fichero

<br>

# 1.2. Escritura de consola

```
System.out.println(data)
---------- -------
objeto       Método
PrintStream
```

- Métodos de _PrintStream_
  - _print(type data)_: escritura de cualquier tipo de dato Java, sin incluir salto de línea final
  - _println(type data)_: escritura de cualquier tipo de dato Java, con salto de línea al final
  - _printf(String format, Object... args)_: escritura de datos con formato

<br>

# 1.3. Escritura en un fichero

- Utilizando _PrintStream_

  - Escritura con formato
  - Graba los datos en modo sobrescritura
  - Si el fichero no existe se crea

    ```
    String dir = "/user/mydata.txt";
    try(PrintStream out = new PrintStream(dir)) {
      out.println("data1");
    } catch(IOException ex) { ... }
    ```

    ```
    String dir = "/user/mydata.txt";
    try(FileOutputStream fos = new FileOutputStream(dir, true); PrintStream out = new PrintStream(fos)) {
        out.println("data1");

    } catch(IOException ex) { ... }
    ```

    - _FileOutputStream_: permite realizar la escritura en modo _append_ (_true_)

- Utilizando _FileWriter_

  - Graba los datos en modo sobrescritura
  - Si el fichero no existe, se crea
    ```
    String dir = "/user/mydata.txt";
    try(FileWriter out = new FileWriter(dir)) {
      out.write("data1");
    } catch(IOException ex) { ... }
    ```
  - Graba los datos en modo _append_
  - Si el fichero no existe se crea

    ```
    String dir = "/user/mydata.txt";
    try(FileWriter out = new FileWriter(dir, true)) {
      out.write("data1");
    } catch(IOException ex) { ... }
    ```

  - Escritura de datos a través de un _BufferedWriter_ que mejora el rendimiento

    ```
    String dir = "/user/mydata.txt";
    try(FileWriter out = new FileWriter(dir, true);
        BufferedWriter bw = new BufferedWriter(out)) {
          bw.write("data1");
          bw.newLine();
    } catch(IOException ex) { ... }
    ```

<br>

# 1.4. Entrada

- Entre las principales clases para operaciones de entrada de datos, están
  - _InputStream_: clase abstracta que representa un flujo de entrada de bytes
  - _FileInputStream_: subclase de InputStream que representa un flujo de entrada asociado a un
  - _FileReader_: clase específica para lectura de texto de un fichero
  - _BufferedReader_: proporciona un mecanismo eficiente para la lectura de cadenas de texto de una fuente externa

<br>

# 1.5. Lectura por teclado

- Lectura utilizando _BufferedReader_
  - se debe crear un _InputStreamReader_ asociado a la entrada estándar (_System.in_)
    ```
    try(InputStreamReader reader = new InputStreamReader(System.in); BufferedReader br = new BufferedReader(reader);) {
      System.out.println("Enter your name:");
      String name = br.readLine();
    } catch(IOException ex) { ... }
    ```
- Lectura mediante _Scanner_

  - se encuentra en _java.util_
  - dispone de otros métodos para leer datos como tipos primitivos (_nextInt_, _nextDouble_)

    ```
    Scanner sc = new Scanner(System.in);
    System.out.println("Enter your name:");
    String name = sc.nextLine();
    ```

<br>

# 1.6. Lectura de un fichero

- Lectura de texto utilizando _BufferedReader_
  - lectura de todas las líneas de un fichero
  - si el fichero no existe se produce una excepción
    ```
    String dir = "/user/mydata.txt";
    try(FileReader fr = new FileReader(dir);
        BufferedReader br = new BufferedReader(fr)) {
          String line;
          while((line = br.readLine()) != null) {
            System.out.prinln(line);
          }
    } catch(IOException ex) { ... }
    ```
- Lectura de bytes mediante _FileInputStream_:
  - utilizado para lectura de ficheros binarios
    ```
    String dir = "/user/mydata.txt";
    File file = new File(dir);
    try(FileInputStream fis = new FileInputStream(file)) {
      byte[] res = new byte[file.length()];
      fis.read(res):
    } catch(IOException ex) { ... }
    ```

<br>

# 1.7. La clase File

- Representa una ruta a un fichero o directorio
  ```
  File file = new File("/user/mydata.txt");
  ```
  - Proporciona métodos para obtener información sobre el elemento
  - _boolean exists()_: devuelve _true_ si existe
  - _boolean isFile()_: devuelve _true_ si es un fichero
  - _boolean isDirectory()_: devuelve _true_ si es un directorio
  - _boolean delete()_: elemina el elemento. Devuelve _true_ si ha conseguido eliminarlo
