# 4. BBDD

# 4.1. Fundamentos JDBC

- Conjunto de clases e interfaces que permiten a una aplicación Java acceder a cualquier base de datos a través de un driver

  ```
                                   -> Driver MySQL  -> MySQL
  Aplicación -> Instrucciones JDBC -> Driver Oracle -> Oracle
                                   -> Driver DB2    -> DB2
  ```

<br>

# 4.2. API JDBC

- Se encuentra en el paquete _java.sql_
- Entre las principales clases e interfaces están
  - _DriverManager_: proporciona un método estático para poder obtener conexiones contra la base de datos
  - _Connection_: representa una conexión contra la base de datos. La obtención de una conexión es un paso previo para poder operar contra la misma
  - _Statement_: a través de este objeto podemos enviar consultas SQL a la base de datos
  - _PreparedStatement_: es una versión alternativa de _Statement_, con la que se puede precompilar consultas SQL antes de enviarlas a la BD
  - _ResultSet_: cuando una consulta devuelve resultados (caso de las instrucciones _Select_), la manipulación de los mismos se realiza a través de un objeto _Resulset_

<br>

# 4.3. Pasos para operar contra una BD

1. Carga del driver
2. Establecimiento de la conexión con la BD
3. Ejecución de la consulta SQL
4. Manipulación de resultados, si procede
5. Cierre de la conexión

<br>

# 4.4. Carga del driver

- El driver es una librería _.jar_ que se incluye dentro del classpath de la aplicación
- Deberá ser cargado en memoria mediante
  ```
  Class.forName("com.mysql.jdbc.Driver");
  ```
- Desde JDBC 4 no es necesario realizar esta operación

<br>

# 4.5. Establecimiento de la conexión

- La conexión con la base de datos se establece a través del método _getConnection()_ de _DriverManager_, que devuelve un objeto _Connection_

  ```
  Connection connection = DriverManager.getConnection(String cadena, String user, String password);

  Connection connection = DriverManager.getConnection(String cadena, Properties properties);
  ```

- La cadena de conexión tiene el siguiente formato
  ```
  jdbc:<subprotocolo>: subname
  ```
- Donde _subprotocolo_ es el tipo de base de datos y _subname_ depende de la base de datos. Ejemplos
  ```
  jdbc:mysql://localhost:3306/mydata
  jdbc:oracle:thin:@localhost:1521/servicedata
  jdbc:db2://localhost:50000/datasets
  ```

<br>

# 4.6. Ejecución de consulta SQL

- Para ejecutar una consulta SQL se utilizan los objetos _Statement_ o _PreparedStatement_
  ```
  String sql = "insert into table(col1, col2) values(40, 'wwww');
  Statement st = connection.createStatement();
  st.execute(sql);
  ```
  ```
  String sql = "insert ito table(col1, col2) values(?,?)";
  PreparedStatement st = connection.prepareStatement(sql);
  st.setInt(1, 40);
  st.setString(2, "wwww");
  st.execute();
  ```
- En el caso de una consulta de selección, se debe obtener el objeto _ResultSet_ para acceder a los registros
  ```
  String sql = "select * from data";
  Statement st = connetion.createStatement();
  st.execute(sql);
  ResultSet rs = st.getResultSet();
  ```
  ```
  String sql = "select ? from data";
  Statement st = connection.createStatement();
  ResultSet rs = st.executeQuery(sql):
  ```

<br>

# 4.7. Manipulación de resultados

- Para acceder a los registros empleamos los siguientes métodos de _ResultSet_
  - _boolean next()_: se desplaza al siguiente registro, si no hay ninguno devolverá _false_
    ```
    // recorre todas las filas
    while(rs.next()) {}
    ```
  - _xxx getXxx(int col)_: métodos para obtener el valor de la columna indicada. La posición de la primera columna es el 1. _xxx_ es el nombre del tipo Java (_getInt_, _getString_,...)
  - _xxxgetXxx(String col)_: igual que el anterior, utilizando el nombre de la columna

<br>

# 4.8. Cierre de la conexión

- Las conexiones deben cerrarse cuando no van a ser utilizadas
  - utilizando el méotodo _close()_ de _Connection_
    ```
    try {
         Connection connection = ...
    }
    finally {
         connection.close();
    }
    ```
  - mediante un _try_ con recursos
    ```
    try(Connection con = ...) {
         ...
    } // se cierra automáticamente al abandonar el try
    ```
