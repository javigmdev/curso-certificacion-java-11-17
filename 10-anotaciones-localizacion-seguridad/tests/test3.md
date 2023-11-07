**Question 1**: Which two safely validate inputs? (Choose two.)

- a. Delegate numeric range checking of values to the database.
- b. Accept only valid characters and input values.
- c. Assume inputs have already been validated.
- d. Use trusted domain-specific libraries to validate inputs.
- e. Modify the input values, as needed, to pass validation.

<br>

**Question 2**: Given

```
1. public class Secret {
2.   String[] names;
3.   public Secret(String[] names) {
4.        this.names = names;
5.   }
6.   public String[] getNames() {
7.        return names;
8.   }
9. }
```

Which three actions implement Java SE security guidelines? (Choose three.)

- a. Change line 7 to return names.clone();
- b. Change line 4 to this.names = names.clone();
- c. Change the getNames() method name to get$Names()
- d. Change line 6 to public synchronized String[] getNames() {
- e. Change line 2 to private final String[] names;
- f. Change line 3 to private Secret(String[] names) {

<br>

**Question 3**: Consider the following method exposed by a utility class:

```
public static String getOptions(final String propName) {
     return AccessController.doPrivileged(
          new PrivilegedAction<String>() {
               public String run() {
                    return System.getProperty(propName);
               }
          }
     );
}
```

It has been decided to give appropriate permission in the security file for this code. Identify correct statements (choose two)

- a. It violates secure coding guidelines for invoking privileged actions.
- b. It violates secure coding guidelines for exposing static methods.
- c. It violates secure coding guidelines for validating inputs.
- d. It violates secure coding guidelines for protecting confidential information.

<br>

**Results**:

- **Question 1**: b, d
- **Question 2**: a, b, e
- **Question 3**: a, c
