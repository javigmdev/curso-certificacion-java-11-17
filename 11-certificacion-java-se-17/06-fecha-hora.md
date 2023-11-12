# 6. Clases de fecha y hora

# 6.1. Manipulación de fechas con java.time

- Desde Java 8, se incluyen las siguientes clases en _java.time_ para manipulación de fechas y horas
  - _LocalDate_: manipulación de fechas
  - _LocalTime_: manipulación de horas
  - _LocalDateTime_: manipulación de fecha más horas
  - _ZonedDateTime_: manipulación de fechas y horas en zona horaria
  - _Instant_: instante de tiempo concreto

<br>

# 6.2. Creación de objetos

- No disponen de constructores públicos
- Se crean a través de métodos estáticos (_of_)
  ```
  var date1 = LocalDate.of(2020, 11, 30); // yyyy,MM,dd
  var date2 = LocalDate.of(2010, Month.May, 15); // utiliza enumeración para el mes
  var hour1 = LocalTime.of(15, 20, 30); // HH, mm, ss
  var it1 = LocalDateTime.of(2022, 0, 30, 20, 11, 15);
  var it2 = LocalDateTime.of(date1, hour1); // a partir de objetos fecha y hora
  var zi = ZoneId.of("Europe/Amsterdam");
  var zdt1 = ZonedDateTime.of(date2, hour1, zi); // datos de fecha y hora más zona horaria
  ```
- Valores erróneos provocarían una excepción
  ```
  var e1 = LocalDate.of(2009, 13, 25); // DateTimeException, número més incorrecto
  ```

<br>

# 6.3. Parseado

- Se pueden crear objetos de fecha-hora, a partir de una cadena de caracteres con el formato estándar de fecha/hora
  ```
  var date1 = LocalDate.parse("2021-10-20");
  var hour1 = LocalTime.parse("15:23:45");
  var lt1 = LocalDateTime.parse("2019-06-03T16:15:30");
  var zdt1 = ZonedDateTime.parse("2019-06-03T16:15:30+01:00[Europe/Madrid]");
  ```
- Si la cadena tiene un formato incorrecto se produce una excepción
  ```
  var e1 = LocalDate.parse("11/10/2022"); // DateTimeParseException
  ```
- Aunque se puede indicar que la cadena tiene un formato específico
  ```
  var e1 = LocalDate.parse("11/10/2022", DateTimeFOrmatter.ofPattern("dd/MM/yyyy"));
  ```

<br>

# 6.4. Manipulación de fechas/horas

- Las clases anteriores disponen de métodos para obtener una nueva fecha resultante de la suma/extracción de una cantidad
- Estos métodos no modifican el valor original, dado que los objetos son inmutables
  ```
  var date1 = LocalDate.of(2020, 12, 1);
  var lt1 = LocalDateTime.of(2022, 9, 30, 20, 11, 15);
  var fn = date1.minusDays(1);
  var ltn = lt1.plusSeconds(50);
  System.out.println(date1); // se mantiene sin cambios 2020-12-01
  System.out.println(fn); // 2020-11-30
  System.out.println(ltn); // 2022-09-30T20:12:05
  ```
- Cuidado con llamadas a métodos no existentes en esa clase
  ```
  var date1 = LocalDate.of(2020, 11, 30);
  date1.minusHOurs(5); // error de compilación
  ```
