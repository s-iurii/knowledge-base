[[☕️ Java]]

#### New methods added Java 11 : 

**isBlank():** Это логический метод. Он просто возвращает true, когда строка пуста, и наоборот. 
**lines():** этот метод возвращает коллекцию строк, разделенных символами конца строки.
**strip():** используется для удаления пробелов в начале и конце строки.
**stripTrailing():** используется для удаления пробелов в конце строки.
**stripLeading():** используется для удаления пробелов перед строкой.
**repeat(n):** Результатом является объединенная строка исходной строки, повторенная указанное в аргументе количество раз.

**asMatchPredicate():** Этот метод похож на метод asPredicate() из Java 8. Этот метод, представленный в JDK 11, создаст предикат, если шаблон совпадает с входной строкой.
```shell
jshell>var str = Pattern.compile("aba").asMatchPredicate();
jshell>str.test(aabb);
**Вывод:** ложь
jshell>str.test(aba);
**Вывод:** истина
```

#### Multiline Strings
##### Multiline java 13
You can _finally_ do this in Java:

```
String htmlBeforeJava13 = "<html>\n" +
              "    <body>\n" +
              "        <p>Hello, world</p>\n" +
              "    </body>\n" +
              "</html>\n";

String htmlWithJava13 = """
              <html>
                  <body>
                      <p>Hello, world</p>
                  </body>
              </html>
              """;
```

##### Text-Blocks / Multiline Strings java 15

Introduced as an experimental feature in Java 13 (see above), multiline strings are now production-ready.

```
String text = """
                Lorem ipsum dolor sit amet, consectetur adipiscing \
                elit, sed do eiusmod tempor incididunt ut labore \
                et dolore magna aliqua.\
                """;
```

##### String Literal

Java offers several mechanisms for composing strings with string literals and expressions. Some of these are String concatenation, _StringBuilder_ class, _String_ class _format()_ method, and the _MessageFormat_ class.

**Java 21 introduces string templates.** These complement Java’s existing string literals and text blocks by coupling literal text with template expressions and template processors to produce the desired results.

Let’s see an example:

```java
String name = "Baeldung";
String welcomeText = STR."Welcome to \{name}";
System.out.println(welcomeText);
```

The above code snippet prints the text “_Welcome to Baeldung_“.

[![String Templates](https://www.baeldung.com/wp-content/uploads/2024/04/StringTemplates.png)](https://www.baeldung.com/wp-content/uploads/2024/04/StringTemplates.png)

In the above text, we have a template processor (STR), a dot character, and a template that contains an embedded expression (_\{name}_). At runtime, when the template processor evaluates the template expression, it combines the literal text in the template with the values of the embedded expression to produce the result.