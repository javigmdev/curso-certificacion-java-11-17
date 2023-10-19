**Question 1**: Which of the following are valid JDBC URLs? (choose 3)

- a. jdbc.derby.localhost/test
- b. jdbc://mysql.com/datas
- c. http://jdbc.mysql/mybase
- d. jdbc:oracle:thin:@localhost:6060:passdb
- e. jdbc:mysql://192.168.23.40:3306/mysql
- f. jdbc:xderby:1670:priters

<br>

**Question 2**: Assume ds is a DataSource and the EMP table is defined appropriately

```
try (Connection connection = ds.getConnection();
   PreparedStatement ps = connection.prepareStatement("INSERT INTO EMP VALUES (?,?,?)")) {
      ps.setObject(1, 101, JDBCType.INTEGER);
      ps.setObject(2, "SMITH", JDBCType.VARCHAR);
      ps.setObject(3, "HR", JDBCType.VARCHAR);
      ps.executeUpdate();
      ps.setInt(1, 102);
      ps.setString(2, "JONES");
      ps.executeUpdate();
}
```

What does executing this code fragment do?

- a. inserts two rows (101, 'SMITH', 'HR') and (102, 'JONES', NULL)
- b. inserts two rows (101, 'SMITH', 'HR') and (102, 'JONES', 'HR')
- c. inserts one row (101, 'SMITH', 'HR')
- d. throws a SQLException

<br>

**Question 3**: Consider the following code written to generate a report containing customer data where each line is a pipe separated list of values.

```
String qr = "select EMAILID, NAME, PHONE from CUSTOMER order by EMAILID";
PreparedStatement stmt = connection.prepareStatement(qr);
ResultSet rs = stmt.executeQuery(); //LINE 10
while(rs.next()){
   System.out.println(rs.getString(0)+"|"+rs.getString(1)+"|"+rs.getString(3));
}
connection.close();
```

Identify the correct statement about this code.
(Assume that items not specified such as import statements and try/catch block are all valid.)

- a. It will throw an exception when run if there is at least 1 record in the table.
- b. It will throw an exception when run if there are no records in the table.
- c. It will print the data as expected.
- d. It will not compile.

<br>

**Results**:

- **Question 1**: d, e, f
- **Question 2**: b
- **Question 3**: a
