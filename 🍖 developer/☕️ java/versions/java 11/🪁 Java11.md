
[[☕️ Java]]


### Running Java Files

A major change in this version is that **we don’t need to compile the Java source files with _javac_ explicitly anymore_:_**

```bash
$ javac HelloWorld.java
$ java HelloWorld 
Hello Java 8!
```

Instead, we can [directly run the file](https://www.baeldung.com/java-single-file-source-code) using the _java_ command:

```bash
$ java HelloWorld.java
Hello Java 11!
```