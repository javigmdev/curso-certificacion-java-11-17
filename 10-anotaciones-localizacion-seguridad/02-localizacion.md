# 2. Localización

# 2.1. Fundamentos

- COnsiste en desarrollar aplicaciones para múltiples idiomas y adaptadas a determinadas localizaciones geográficas
- Los textos se incluyen en archivos de recursos que no son cargados dinámicamente en tiempo de ejecución
- La clase _Locale_ permite establecer la localización geográfica e idioma con el que se va a trabajar

<br>

# 2.2. Archivos de recursos

- Para cada idioma, se creará un archivo de texto _.properties_ con parejas _clave=valor_ que incluyan los diferentes textos a mostrar
- Los archivos se nombrarán
  ```
  filename_prefix.properties
  ```
- Ejemplos

  ```
  // messages_es.properties
  data.name = Introduce tu nombre
  data.age = Introduce tu edad
  ```

  ```
  // messages_en.properties
  data.name = Type your name
  data.age = Type your age
  ```

<br>

# 2.3. Objeto Locale

- La clase _java.util.Locale_ representa una localización e idioma
- Se puede crear un objeto _Locale_ con los constructores
  ```
  Locale(String language)
  Locale(String language, String country)
  ```
- También se puede usar las constantes _Locale.US_, _Locale.CANADA_, _Locale.FRENCH_, etc
  ```
  Locale localeFR = new Locale("fr","FR");
  Locale localeUS = new Locale("en","US");
  ```
- Localización por defecto
  ```
  static void setDefault(Locale newLocale)
  static void setDefault(Locale.Category category, Locale new Locale)
  ```

<br>

# 2.4. Carga del archivo de recursos

- Para obtener el archivo de recursos asociado a una determinada localización, se debe crear un objeto _ResourceBundle_
  ```
  ResourceBundle rb = ResourceBundle.getBundle(String fileName, Locale locale);
  ```
- Ejemplos
  ```
  ResourceBundle rbUS = ResourceBundle.getBundle("messages", Locale.US);
  ResourceBundle rbDefault = ResourceBundle.getBundle("messages", Locale.getDefault());
  ```
- Para obtener los textos, se emplea el método _getString(String key)_ de _ResourceBundle_
  ```
  System.out.println("US:" + rbUS.getString("data1"));
  System.out.println("Default:" + rbDefault.getString("data2"));
  ```

<br>

# 2.5. Formateado de datos

- El paquete _java.text_ incluye las siguientes clases para el formateado de números y fechas según una determinada localización
  - _NumberFormat_: establece un formato para número
    ```
    double salary = 1256.678;
    NumberFormat numberFormat = NumberFormat.getCurrencyInstance(Locale.GERMANY);
    System.out.println(numberFormat.format(salary));
    ```
  - _DateFormat_: permite formatear fechas
    ```
    DateFormat dateFormat = DateFormat.getDateInstance(DateFormat.FULL, Locale.US);
    System.out.println(dateFormat.format(new Date())); // Tuesday, May 4, 2021
    ```
  - _DateTimeFormatter_: formateado de nuevas clases de fecha
    ```
    LocalDate localDate = LocalDate.now();
    DateTimeFormatter dateTimeFormatter = DateTimeFormatter.ofPattern("dd/MM/yyyy");
    System.out.println(dateTimeFormatter.format(localDate)); // 07/05/2021
    ```
