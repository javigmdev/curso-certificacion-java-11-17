**Question 1**: What will the following code fragment print?

```
Path p1 = Paths.get("\\personal\\readme.txt");
Path p2 = Paths.get("\\index.html");
Path p3 = p1.relativize(p2);
System.out.println(p3);
```

- a. \index.html
- b. \personal \index.html
- c. personal \index.html
- d. ..\..\index.html

<br>

**Question 2**: Given

```
Path p1 = Paths.get("c:\\temp\\test1.txt");
Path p2 = Paths.get("c:\\temp\\test2.txt");
```

Which of the following code fragments moves the file test1.txt to test2.txt, even if test2.txt exists? (choose 2)

- a. Files.move(p1, p2);
- b. try(Files.move(p1,p2)){}
- c. Files.move(p1, p2, StandardCopyOption.REPLACE_EXISTING);
- d. try(Files.copy(p1, p2, StandardCopyOption.REPLACE_EXISTING)){ Files.delete(p1); }
- e. Files.copy(p1, p2, StandardCopyOption.REPLACE_EXISTING); Files.delete(p1);

<br>

**Question 3**: What will the following code fragment print?

```
Path p1 = Paths.get("temp\\..\\level\\.\\files\\a.txt");
Path p2 = p1.normalize();
Path p3 = p1.relativize(p2);
Path p4 = p2.relativize(p1);
System.out.println(
     p1.getNameCount()+" "+p2.getNameCount()+" "+
     p3.getNameCount()+" "+p4.getNameCount());
```

- a. 6 4 10 10
- b. 7 4 11 10
- c. 7 3 8 9
- d. 6 3 1 1

<br>

**Question 4**: Given:

```
String INPUT_FILE = "c:\\tempo\\src\\path.end\\screen.java";
```

Assuming the file exists, which of the following options will print the contents of the file? (2)

```
a. Files.lines(INPUT_FILE).forEach(System.out::println);
b. Stream<String> lines = Files.lines(Paths.get(INPUT_FILE));
   lines.forEach(System.out::println);
c. Stream<String> lines = Files.readAllLines(Paths.get(INPUT_FILE));
   lines.forEach(System.out::println);
d. List<String> lines = Files.readAllLines(Paths.get(INPUT_FILE));
   lines.forEach(System.out::println);
e. List<String> lines = Files.lines(Paths.get(INPUT_FILE));
   lines.forEach(System.out::println);
f. String[] stra = Files.readLines(Paths.get(INPUT_FILE));
   for(String s: stra) System.out.println(s);
```

<br>

**Question 5**: Given

```
Path current=Path.of("c:\\temp\\exam\\temp.txt");
Path output=Path.of("c:\\temp\\exam\\new.txt");
Path dir=Path.of("c:\\temp");
Files.copy(current, output);
Files.copy(output, dir);
Files.delete(output);
```

The c:\temp\exam\temp.txt file exists. The c:\temp\exam\new.txt and c:\temp\new.txt files do not exist.
What is the result?

- a. c:\temp\exam\new.txt and c:\temp\new.txt are deleted.
- b. The program throws a FileaAlreadyExistsException.
- c. The program throws a NoSuchFileException.
- d. A copy of new.txt exists in the c:\temp directory and c:\temp\exam\new.txt is deleted.

<br>

**Results**:

- **Question 1**: d
- **Question 2**: c, e
- **Question 3**: d
- **Question 4**: b, d
- **Question 5**: b
