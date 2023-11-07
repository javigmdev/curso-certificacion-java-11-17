**Question 1**: Given:

```
@interface Resource {
     String name;
     int level default 0;
}
```

Examine this code fragment:

```
/* here */ class ProcessOrders { ... }
```

Which two annotations may be applied at here in the code fragment? (Choose two.)

- a. @Resource(level=100)
- b. @Resource(level=0)
- c. @Resource(name="Customer1", level=100)
- d. @Resource(name="Customer1")
- e. @Resource

<br>

**Question 2**: Given:

```
@Target(value={TYPE_USE,TYPE_PARAMETER})
public @interface Interned{ }

public class Account{ }
```

Identify correct usages (2 options)

- a. var str = "Hello"+ (@Interned) "World";
- b. var str = "Hello"+ (@Interned "World");
- c. @Interned Account acct = new Account();
- d. Account acct = new @Interned Account();
- e. Account acct = @Interned new Account()

<br>

**Question 3**: Which of the following are meta-annotations? (choose 2)

- a. @Override
- b. @FunctionalInterface
- c. @Retention
- d. @Repetable
- e. @SuppressWarnings

<br>

**Results**:

- **Question 1**: c, d
- **Question 2**: c, d
- **Question 3**: c, d
