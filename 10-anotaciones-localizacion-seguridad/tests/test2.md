**Question 1**: Consider the following piece of code, which is run in an environment where the default locale is English - US:

```
Locale.setDefault(new Locale("fr", "CA")); //Set default to French Canada
Locale l = new Locale("jp", "JP");
ResourceBundle rb = ResourceBundle.getBundle("appmessages", l);
String msg = rb.getString("greetings");
System.out.println(msg);
```

You have created two resource bundles for appmessages, with the following contents:

```
#In English US resource bundle file
greetings=Hello
#In French CA resource bundle file
greetings=bonjour
```

What will be the output?

- a. Hello
- b. bonjour
- c. An exception at run time.
- d. No message will be printed.

<br>

**Question 2**: Which two statements set the default locale used for formatting numbers, currency, and percentages?(Choose two.)

- a. Locale.setDefault(Locale.Category.FORMAT, "zh-CN");
- b. Locale.setDefault(Locale.Category.FORMAT, Locale.CANADA_FRENCH);
- c. Locale.setDefault(Locale.SIMPLIFIED_CHINESE);
- d. Locale.setDefault("en_CA");
- e. Locale.setDefault("es", Locale.US);

<br>

**Question 3**: Identify valid statements (choose 3)

- a. Locale myLocale = System.getDefaultLocale();
- b. Locale myLocale = Locale.getDefaultLocale();
- c. Locale myLocale = Locale.getDefault();
- d. Locale myLocale = Locale.US;
- e. Locale myLocale = Locale.getInstance();
- f. Locale myLocale = new Locale("ru", "RU");

<br>

**Results**:

- **Question 1**: b
- **Question 2**: b, c
- **Question 3**: d
