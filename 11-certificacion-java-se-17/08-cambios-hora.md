# 8. Cambios de hora

- Java tiene en cuenta los cambios de hora en la manipulación de objetos _ZonedDateTime_
  ```
  LocalDateTime ld1 = LocalDateTime.of(2022, 10, 30, 2, 30, 30);
  ZonedDateTime zd1 = ZonedDateTime.of(ld1, ZoneId.of("Europe/Madrid")); // media hora antes del atraso de otoño
  ZonedDateTime zd2 = zd1.plusHours(1);
  System.out.println(zd1); // 2022-10-30T02:30:30+02:00[Europe/Madrid]
  System.out.println(zd2); // 2022-10-30T02:30:30+01:00[Europe/Madrid]
  System.out.println(Duration.between(zd1, zd2)); // PT1H
  System.out.println(zd1.getOffset()); // +02:00
  System.out.println(zd2.getOffset()); // +01:00
  ```
