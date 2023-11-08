# 2. Bloques de texto

# 2.1. Triples comillas

- Es posible representar un texto que contenga caracteres especiales, como saltos de línea y comillas, delimitándolo entre triples comillas: """ y """
- Muy útil, por ejemplo, para _JSON_
  ```
  String json = """
            {
                 "name": "John",
                 "phone": 666666666
            } """;
  ```
- El delimitador de inicio tiene que ir en una línea idependiente
- Se respetan todos los caracteres de la cadena, incluidos saltos de línea

<br>

# 2.2. Espacios

- En bloques de texto multilínea, los espacios antes del salto de línea son eliminados automáticamente, a no ser que se indiquen explícitamente (carácter _\s_)
- Ejemplo
  ```
  String text = """
                 a
                 b
                 c \s
                 """;
  System.out.println(text); // a
                               b
                               c
  System.out.println(text.length()); // 8
  ```
- Los espacios que hubiera después de a, b y _\s_ son eliminados automáticamente

<br>

# 2.3. Eliminación de saltos de línea

- Si no se quiere introducir un salto al final de cada línea, se utilizará el símbolo _(\\)_
- No se puede indicar ningún caracter después d edicho símbolo
  ```
  String text = """
              a \
              b\
              c
              """;
  System.out.println(text); // a bc
  System.out.println(text.length()); // 5
  ```

<br>

# 2.4. Indentación

- En Java 12, la clase _String_ incorpora el método _indent(int n)_ para añadir espacios en una cadena
- Añade tantos espacios al principio de cada línea como se indique en el número, si este es negativo los elimina
- Incluye un salto de línea final si no existe
  ```
  String mycad="""
            x
            y
            z""";
  System.out.println(mycad.length()); // 5
  System.out.println(mycad.indent(1).length()); // 9
  System.out.println(mycad.indent(-1).length()); // 6 hay que contar el salto de línea
  ```

<br>

# 2.5. Método stripIndent

- Método incorporado a la clase _String_ en Java 15 que, tras una concatenación, elimina los espacios existentes antes de un salto de línea
  ```
  String c1 = "x \n";
  String c2 = "y \n";
  System.out.println((c1 + c2).stripIndent().length()); // 5
  ```
