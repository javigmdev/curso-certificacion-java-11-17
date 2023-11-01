# 3. Clases Atomic

# 3.1. Fundamentos

- Conjunto de clases de _java.util.concurrent.atomic_ para operar sobre variables simples en un entorno multitarea en modo _thread-safe_
- A diferencia de las clases de envoltorio, garantizan la integridad de los datos en entorno multitarea
- Utilizan internamente variables _volatile_ (acceso directo a memoria) para garantizar la integridad de los datos
- Las principales clases son _AtomicBoolean_, _AtomicInteger_ y _AtomicLong_

<br>

# 3.2. AtomicInteger

- Adecuada para aplicaciones de tipo contador global
- Entre sus principales métodos
  - _int incrementAndGet()_: incrementa el contador interno y devuelve su valor
  - _int decrementAndGet()_: decrementa el contador interno y devuelve su valor
  - _int addAndGet(int delta)_: añade el valor especificado a la variable interna y devuelve el valor de la misma
  - _int get()_: devuelve el valor actual del contador

<br>

# 3.3. AtomicBoolean

- Adecuada para ser utilizado como flag o indicador global
- Entre sus principales métodos
  - _void set(boolean newValue)_: establece el nuevo valor al indicador
  - _boolean get()_: devuelve el valor actual del indicador
  - _boolean compareAndSet(boolean expected, boolean newValue)_: si el valor actual es igual al _expected_, se asigna _newValue_ como valor actual
