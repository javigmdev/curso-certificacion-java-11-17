**Question 1**: Select the correct creation of Date/Time objects (choose 3):

- a. LocalDateTime ldt=LocalDateTime.now();
- b. LocalDate ld=LocalDate.of(2000,10,30);
- c. LocalTime lt=new LocalTime(10,30,45);
- d. LocalDate ld=LocalDate.of(2003,2,30);
- e. LocalDateTime ldt=LocalDateTime.of(LocalDate.now(), LocalTime.now());

<br>

**Question 2**: What will the following code print when compiled and run?

```
Instant init = Instant.parse("2022-06-25T16:13:30.00z");
init.plus(10, ChronoUnit.HOURS);
System.out.println(init);
Duration duration = Duration.ofHours(1);
Instant instant = init.plus(duration);
System.out.println(instant);
LocalDateTime ltd = LocalDateTime.ofInstant(instant, ZoneId.of("GMT+2"));
System.out.println(ltd);
```

- a. 2022-06-25T16:13:30Z <br>
  2022-06-25T17:13:30Z <br>
  2022-06-25T15:13:30
- b. T16:13:30Z <br>
  T17:13:30Z <br>
  2022-06-25T19:13:30
- c. 2022-06-25T16:13:30Z <br>
  2022-06-25T17:13:30Z <br>
  2022-06-25T19:13:30
- d. T16:13:30Z <br>
  T17:13:30Z <br>
  2022-06-25T15:13:30

<br>

**Question 3**: Given that Daylight Savings Time ends on Nov 1 at 2 AM in US/Eastern time zone, what will the following code print?

```
LocalDateTime ld = LocalDateTime.of(2022, Month.OCTOBER, 31, 10, 0);
ZonedDateTime date = ZonedDateTime.of(ld, ZoneId.of("US/Eastern"));
date = date.plus(Duration.ofDays(1));
System.out.println(date);
date = ZonedDateTime.of(ld, ZoneId.of("US/Eastern"));
date = date.plus(Period.ofDays(1));
System.out.println(date);
```

- a. 2022-11-01T09:00-05:00[US/Eastern] <br>
  2022-11-01T09:00-05:00[US/Eastern]
- b. 2022-11-01T09:00-05:00[US/Eastern] <br>
  2022-11-01T10:00-05:00[US/Eastern]
- c. 2022-11-01T10:00-05:00[US/Eastern] <br>
  2022-11-01T09:00-05:00[US/Eastern]
- d. 2022-11-01T10:00-05:00[US/Eastern] <br>
  2022-11-01T10:00-05:00[US/Eastern]

<br>

**Question 4**: Which of the following classes should you use to represent just a date without any time or zone information?

- a. java.sql.Date
- b. java.time.LocalDateTime
- c. java.time.format.DateTimeFormatter
- d. java.time.LocalDate
- e. java.time.Instant

<br>

**Question 5**: Given

```
var ldt1=LocalDateTime.of(2020,11,20,22,30,15);
var ldt2=ldt1.minusHours(3);
var zdt1=ZonedDateTime.of(ldt1,ZoneId.of("GMT"));
var zdt2=ZonedDateTime.of(ldt2,ZoneId.of("GMT-5"));
System.out.println(Duration.between(zdt1, zdt2));
```

What will this code print?

- a. PT2H
- b. PT3H
- c. PT8H
- d. The code throws an exception

<br>

**Results**:

- **Question 1**: a, b, e
- **Question 2**: c
- **Question 3**: b
- **Question 4**: d
- **Question 5**: a
