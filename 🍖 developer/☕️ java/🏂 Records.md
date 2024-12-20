[[☕️ Java]] 
#### Preview Java 14
 There are now record classes, which help alleviate the pain of writing a lot of boilerplate with Java.

Have a look at this pre Java 14 class, which only contains data, (potentially) getters/setters, equals/hashcode, toString.

```
final class Point {
    public final int x;
    public final int y;

    public Point(int x, int y) {
        this.x = x;
        this.y = y;
    }
}
    // state-based implementations of equals, hashCode, toString
    // nothing else
```

With records, it can now be written like this:

```
record Point(int x, int y) { }
```

Again, this is a preview feature and subject to change in future releases.

Начиная с JDK 14, мы можем заменить наши повторяющиеся классы данных записями. **Записи — это неизменяемые классы данных, которым требуется только тип и имя полей.**

Методы equals _,_ _hashCode_ и _toString_ , а также поля _private,_  final  _и_ public _конструктор_ генерируются компилятором Java.
Используя записи, для нас генерируется открытый конструктор с аргументом для каждого поля.

В случае нашей  записи _Person_ эквивалентный конструктор выглядит так:
```java
public Person(String name, String address) {
	this.name = name; this.address = address; 
}
```
Мы также бесплатно получаем публичные методы-геттеры, имена которых совпадают с именем нашего поля
Хотя для нас генерируется открытый конструктор, мы все равно можем настроить реализацию нашего конструктора.

```java
public record Person(String name, String address) {
    public Person {
        Objects.requireNonNull(name);
        Objects.requireNonNull(address);
    }
}
```

Мы также можем создавать новые конструкторы с другими аргументами, предоставляя другой список аргументов:

```java
public record Person(String name, String address) {
    public Person(String name) {
        this(name, "Unknown");
    }
}
```

Мы объявляем статические переменные, используя тот же синтаксис, что и класс:

```java
public record Person(String name, String address) {
    public static String UNKNOWN_ADDRESS = "Unknown";
}
```

Аналогично мы объявляем статические методы, используя тот же синтаксис, что и класс:

```java
public record Person(String name, String address) {
    public static Person unnamed(String address) {
        return new Person("Unnamed", address);
    }
}
```

Затем мы можем ссылаться как на статические переменные, так и на статические методы, используя имя записи:

```java
Person.UNKNOWN_ADDRESS
Person.unnamed("100 Linda Ln.");
```

