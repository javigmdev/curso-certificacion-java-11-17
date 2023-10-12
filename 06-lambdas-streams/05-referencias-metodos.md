# 5. Referencias a métodos

# 5.1. Concepto y uso

- Sustituyen a expresiones lambda cuya única instrucción consiste en una llamada a un método
- Indica qué método debe ser llamado en circunstancias donde los parámetros y objeto al que aplicarlo pueden ser deducidos por el contexto
- Sintaxis
  ```
  class/object::method_name
  ```

<br>

# 5.2. Tipos y casos

| Tipo                                     | Expresión lambda equivalente | Referencia a método |
| ---------------------------------------- | ---------------------------- | ------------------- |
| Referencia a método estático             | s -> String.valueOf(s)       | String::valueOf     |
| Referencia a método de objeto específico | s -> System.out.prinln(s)    | System.out::println |
| Referencia a método de objeto arbitrario | (a,b) -> a.equal(b)          | String::equals      |
| Referencia a constructor                 | a -> new MyClass(a)          | MyClass::new        |
