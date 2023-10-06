# 3. Empaquetado de módulos

# 3.1. Empaquetado en archivos .jar

- Para empaquetar un módulo en un _.jar_

  ```
  jar -c -file=dir_destino/nombre_archivo.jar -C path_modulo

  dir_destino: directorio de destino del módulo
  path_modulo: directorio raíz del módulo

  jar -c --file=ejecutables/module2.jar -C module2 .
  jar -c --file=ejecutables/module1.jar -C module1 .

  .: indica que se incluya todo el contenido del directorio
  ```

  - Para ejecutar com.module1 desde _ejecutables_

  ```
  java -p . -m com.module1/com.client.Test
  ```

<br>

# 3.2. Empaquetado en archivos .jmod

- Similar a _.jar_. Debe ser utilizado para librerías nativas en lugar de módulos en general
  ```
  jmod create --class-path dir_modulo fichero.jmod
  ```
- Ejemplo
  ```
  jmod create --class-path module2 ejecutables/module2.jmod
  jmod create --class-path module1 ejecutables/module1.jmod
  ```
- No se puede utilizar el formato _.jmod_ en la ejecución de módulos

<br>

# 3.3. Comando jdeps

- Se emplea para obtener información sobre la dependencia de módulos
  ```
  jdeps -s dir_modulo
          o
  jdeps -s dir_modulo/archivo.jar
  ```
- Si depende de algún módulo extra
  ```
  jdeps --module-path dir_mod_dependiente -s dir_modulo
  ```
- Ejemplo:

  ```
  jdeps --module-path ejecutables/module2.jar -s ejecutables/module1.jar

  // module2 -> java.base
  // module1 -> module2
  ```
