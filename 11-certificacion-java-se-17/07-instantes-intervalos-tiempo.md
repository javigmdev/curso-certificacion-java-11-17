# 7. Instantes e intervalos de tiempo

# 7.1 Instante de tiempo

- Un objeto _Instant_ representa un momento de tiempo concreto en la zona _GMT_
  ```
  var instant1 = Instant.now(); // instante de tiempo actual
  var instant2 = Instant.ofEpochSecond(2_000_000); // momento de tiempo dos millones de segundos después de 1970-01-01T00:00:00
  System.out.println(instant2); 1970-01-24T03:33:20Z
  ```
- Se puede crear a partir de un _ZonedDateTime_
  ```
  var zi = ZoneId.of("America/New York");
  var date1 = LocalDate.of(2020, 11, 30);
  var h1 = LocalTime.of(15, 20, 30);
  var zdt1 = ZonedDateTime.of(date1, h1, zi);
  var i3 = zdt1.toInstant();
  System.out.println(zdt1); // 2020-11-30T15:20:30-05:00[America/New York]
  System.out.println(i3); // 2020-11-30T20:20:30Z
  ```

<br>

# 7.2. Periodos de tiempo

- La clase _Period_ representa un periodo de tiempo, medido en años, meses y días
  ```
  Period p1 = Period.of(2,5,11); // P2Y5M11D
  Period p2 = Period.ofYear(3); // P3Y
  Period p3 = Period.ofDays(200); // P200D
  Period d4 = p2.plus(p3); // P3Y200D
  ```
- Se pueden sumar/restar periodos de tiempo a objetos de fecha, pero no a _LocalTime_
  ```
  var d1 = LocalDate.of(2020, 11, 30);
  Period p1 = Period.ofWeeks(3);
  System.out.println(d1.plus(p1)); // 2020-12-21
  var h1 = LocalTime.of(15, 20, 30);
  System.out.println(h1.minus(p1)); // exception UnsupportedTemporalTypeException
  ```

<br>

# 7.3. Intervalo entre fechas

- Mediante el método estático _between()_ de _Period_ se puede obtener el intervalo de tiempo entre dos fechas en formato _Period_
- Únicamente puede utilizarse con objetos _LocalDate_
  ```
  static Period between(LocalDate startDateInclusive, LocalDate endDateExclusive)
  ```
  ```
  var date1 = LocalDate.of(2020, 11, 11);
  var date2 = LocalDate.of(2020, 11, 30);
  var ldt1 = LocalDateTime.of(2020, 11, 20, 22, 30, 15);
  var ldt2 = LocalDateTiem.of(2020, 11, 21, 01, 30, 15);
  System.out.println(Period.between(date1, date2)); // P19D
  System.out.println(Period.between(ldt1.toLocalDate(), ldt2.toLocalDate())); // P1D
  ```

<br>

# 7.4. Duraciones

- Una duración, representada por el objeto _Duration_, representa un intervalo de tiempo medido en horas, minutos y segundos
  ```
  Duration d1 = Duration.ofDays(2); // se almacena el número de horas: PT48H
  Duration d2 = Duration.ofSeconds(150); // PT150S
  Duration d3 = Duration.ofHours(4); // PT4H
  Duration d4 = d3.plus(d2); // PT4H2M30S
  ```
- Se pueden sumar/restar duraciones a objetos de hora, pero no a objetos _LocalDate_
  ```
  Duration d1 = Duration.ofHours(4);
  var ldt1 = LocalDateTime.of(2003, 8, 11, 15, 20, 30);
  var ldt2 = ldt1.minus(d1);
  System.out.println(ldt2); // 2003-08-11T11:20:30
  ```

<br>

# 7.5. Intervalo entre horas

- Mediante el método estático _between_ de _Duration_, se puede obtener el intervalo de tiempo entre dos fechas en formato _Duration_
- Puede utilizarse con objetos que contengan datos de hora

  ```
  static Duration between(Temporal startInclusive, Temporal endExclusive)
  ```

  ```
  var t1 = LocalTime.of(2, 11, 30);
  var t2 = LocalTime.of(15, 11, 40);
  var ldt1 = LocalDateTime.of(2020, 11, 20, 22, 30, 15);
  var ldt2 = LocalDateTime.of(2020, 11, 21, 1, 30, 15);
  System.out.println(Duration.between(t1, t2)); // PT13H10S
  System.out.println(Duration.between(ldt1, ldt2)); // PT3H
  var zdt1 = ZonedDateTime.of(ldt1, ZoneId.of("Europe/Amsterdam")); // GMT+1
  var zdt2 = ZonedDateTime.of(ldt2, ZoneId.of("America/New_York")); // GMT-5
  System.out.println(Duration.between(zdt1, zdt2)); // PT9H se tiene en cuenta la diferencia horaria entre ambas zonas
  ```
