# 1. Anotaciones

# 1.1. Fundamentos

- Permiten suministrar información al entorno de ejecución (metadatos) desde el propio código
- Su sintaxis es
  ```
  @AnnotationName(attribute1 = "value", attribute2 = "value"..)
  ```
- Se puede indicar delante de clases, métodos o atributos
- Siempre deben ir delante del nombre del tipo
  ```
  @Annotation var data; // OK
  @Annotation public void method() { ... } // OK
  String @Annotation car; // KO
  var n = @Annotation "text"; // KO
  ```
- Java proporciona varias anotaciones predefinidas

<br>

# 1.2. Anotaciones personalizadas

- Se puede crear nuestras propias anotaciones personalizadas definiéndolas como una interfaz especial
  ```
  public @interface MyAnnotation {}
  ```
- La interfaz anterior debe estar anotada a su vez con dos anotaciones especiales, conocidas como metaanotaciones (_@Target_ y _@Retention_)
- En cuanto al interior de la interfaz, ésta está formada por una serie de métodos que determinan los atributos expuestos por la anotación

<br>

# 1.3. Metaanotaciones

- _Target_: indica a qué tipo de elemento se aplicará la anotación
  - _ElementType.TYPE_: se aplica a un tipo (clase, interface, enumeración)
  - _ElementType.FIELD_: se aplica a un miembro de la clase
  - _ElementType.METHOD_: se aplica a un método
  - _ElementType.PARAMETER_: se aplica a parámetros de un método
  - _ElementType.CONSTRUCTOR_: se aplica a constructores
  - _ElementType.LOCAL_VARIABLE_: se aplica a variables locales
  - _ElementType.ANNOTATION_TYPE_: indica que el tipo declarado en sí es un tipo de anotación
- _Retention_: indica el nivel de retención de la anotación, es decir, su ámbito de acceso
  - _RetentionPolicy.SOURCE_: retenida sólo a nivel de código, por lo que es ignorada por el compilador
  - _RetentionPolicy.CLASS_: retenida en tiempo de compilación, pero ignorada en tiempo de ejecución
  - _RetentionPolicy.RUNTIME_: retenida en tiempo de ejecución y sólo se puede acceder a ella en este tiempo

<br>

# 1.4. Ejemplo

- Anotación que, a través de su atributo _level_, define el nivel de detalle de un método encargado de un registro de sucesos

  ```
  @Retention(RUNTIME) // interpretada en tiempo de ejecución
  @Target(METHOD) // se puede utilizar sobre métodos
  public @interface Log {
       Values level() default Values.ONE;
  }
  ```

  _default_: si indica valores por defecto, el atributo es opcional

  Enumeración que define los posibles valores del atributo

  ```
  public enum Values {
       ONE, TWO, THREE
  }
  ```

- Los valores de un atributo de anotación solo pueden ser primitivos, envoltorio, _String_ o enumeraciones. También _array_ de éstos

<br>

# 1.5. Metaanotación @Repetable

- Permite que una anotación pueda aplicarse más de una vez sobre el elemento
- Además de la anotación principal, se debe crear otra que incluya un _array_ de objetos anotación
  ```
  @Repatable(Authors.class)
  public @interface Author {
       int id() default 0;
       String value();
  }
  ```
  ```
  public @interface Authors {
       Author[] value();
  }
  ```
- Para utilizarla

  ```
  @Author(...)
  @Author(...)
  class MyClass {}
  ```

  o

  ```
  @Authors({@Author(...), @Author(...)})
  class MyClass {}
  ```

<br>

# 1.6. Anotación @SuppressWarnings

- Anotación especial para eliminar avisos en código fuente
- Su definición es
  ```
  @Target(value={TYPE,FIELD,METHOD,PARAMETER,CONSTRUCTOR,LOCAL_VARIABLE})
  @Retention(value=SOURCE)
  public @interface SuppressWarnings {
       String[] value;
  }
  ```
- Entre los posibles valores de _value_
  - _unchecked_: se suprimen avisos de código inseguro
  - _deprecation_: se suprimen avisos de código deprecado
  - _unused_: se suprimen avisos de elementos no utilizados

<br>

# 1.7. Otras anotaciones especiales

- _@Override_: se utiliza delante de un método de instancia para indicar que dicho método está siendo sobreescrito. Es utilizada por el compilador
- _@Deprecated_: se utiliza para indicar que una clase, atributo o método está _deprecated_ y no se recomienda su uso. Es utilizada en tiempo de ejecución
- _@SafeVarargs_: utilizada sobre métodos y constructores para afirmar que el parámetro _varargs_ no realiza operaciones potencialmente inseguras
