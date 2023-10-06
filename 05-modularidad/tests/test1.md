**Question 1**: Given this requirement:
Module vehicle depends on module part and makes its com.vehicle package available for all other modules.

Which module-info.java declaration meets the requirement?

```
a.
module vehicle{
     requires part;
     exports com.vehicle;
}

b.
module vehicle{
     requires part;
     uses com.vehicle;
}

c.

module vehicle{
     requires part;
     exports com.vehicle to part;
}

d.
module vehicle{
     requires com.vehicle;
     exports part;
}
```

<br>

**Question 2**: A modularized application has been packaged in graphs.jar file with module name as com.xcomp.graphs. The entry point of the application is a class named Main in package com.xcomp.graphs.

Which two options can be used to execute this application?

- a. java --module-path graphs.jar --module com.xcomp.graphs.Main
- b. java --module-path graphs.jar --module com.xcomp.graphs/com.xcomp.graphs.Main
- c. java -classpath graphs.jar --module com.xcomp.graphs/com.xcomp.graphs.Main
- d. java --module-path graphs.jar com.xcomp.graphs.Main
- e. java -classpath graphs.jar com.xcomp.graphs.Main
- f. java --module-path graphs.jar --main-class com.xcomp.graphs.Main

<br>

**Question 3**: Which two statements are correct about modules in Java? (Choose two.)

- a. java.base exports all of the Java platforms core packages.
- b. module-info.java can be placed in any folder inside module-path.
- c. A module must be declared in module-info.java file.
- d. module-info.java cannot be empty.
- e. By default, modules can access each other as long as they run in the same folder.

<br>

**Question 4**: Given the follow two module definitions:

```
module author{
     requires serviceapi;
     uses api.BloggerService;
}

module abc.blogger{
     requires serviceapi;
     provides api.BloggerService with abc.SimpleBlogger;
}
```

Identify correct statements(choose two)

- a. api.BloggerService should be defined in author module
- b. api.BloggerService should be defined in abc.blogger module
- c. api.BloggerService should be defined in serviceapi module
- d. abc.blogger module should be on --module-path while executing author module but is not required while compiling
- e. author module should be on --module-path while executing abc.blogger module but is not required while compiling

<br>

**Question 5**: Identify correct statements about the modular JDK (choose three options)

- a. The base module does not depend on any module while every other module depends on the base module
- b. The set of modules of the modular JDK can be combined to create configurations corresponding to the full Java SE Platform, the full JRE, and the full JDK
- c. The standard modules of the modular JDK are governed by the Java Community Process while non-standard ones are not
- d. A standard module may contain a standard or non-standard API package but must not export any non-standard package

<br>

**Results**:

- **Question 1**: a
- **Question 2**: b, e
- **Question 3**: a, c
- **Question 4**: c, d
- **Question 5**: a, b, c
