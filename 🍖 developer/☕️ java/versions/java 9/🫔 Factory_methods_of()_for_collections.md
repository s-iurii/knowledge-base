
[[🧁 Java9]], [[🏸 Collections]]

### links
[java-9-features](https://www.geeksforgeeks.org/java-9-features-with-examples/)


### методы of()

Часто вы хотите создать коллекцию (например, List или Set) в своей программе Java и заполнить ее некоторыми элементами. Это приводит к повторяющемуся кодированию, когда вы создаете экземпляр коллекции, а затем выполняете несколько вызовов «add». В Java 9 было добавлено несколько так называемых методов фабрики коллекций. Интерфейсы List и Set имеют методы «of()» для создания пустых или непустых неизменяемых объектов List или Set, как показано ниже:

```java

List immutableList = List.of();
List immutableList = List.of("one", "two", "three");

jshell> Map emptyImmutableMap = Map.of()  
emptyImmutableMap ==> {}

jshell> Map nonemptyImmutableMap = Map.of(1, "one", 2, "two", 3, "three")  
nonemptyImmutableMap ==> {2=two, 3=three, 1=one}
```
