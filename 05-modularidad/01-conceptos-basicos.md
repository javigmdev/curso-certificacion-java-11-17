# 1. Conceptos básicos

# 1.1. ¿Qué es un módulo?

- Nivel de división superior al paquete
- Agrupa un conjunto de paquetes e incluye información de dependencia de los mismos
- El propio JDK está organizado de forma modular

  ```
   Módulo
             module-info.class

        paquete1          paquete2
        Class1.class      ClassA.class
        Class2.class      ClassB.class
  ```

<br>

# 1.2. Descriptor de módulo

- Se trata del archivo module-info.java
- Debe estar en el directorio raíz del módulo
- Indica los módulos requeridos por nuestro módulo y los paquetes a exportar para otros módulos
  ```
  moduleTest           module-info.java
    package1              module moduleTest {
    package2                  exports package1;
                              requires modulExt;
                          }
  ```

<br>

# 1.3. Ventajas

- Mejor control de acceso. Permite que ciertos paquetes sean utilizados sólo por otros paquetes
- Claridad en las dependencias. A través de _module-info_, se especifica claramente las dependencias entre módulos, que son evaluadas al compilar y al lanzar la aplicación
- Paquetes de distribución más pequeños. Facilita la distribución de aplicaciones y mejora el rendimiento
- Existencia de paquetes únicos. No puede haber dos módulos que expongan el mismo paquete
