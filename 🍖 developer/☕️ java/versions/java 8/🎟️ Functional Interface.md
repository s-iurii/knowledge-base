
[[🏆 Java8]]


Интерфейс, содержащий только один абстрактный метод, называется функциональным интерфейсом, но ограничений нет: внутри функционального интерфейса может быть **n** методов по умолчанию и статических методов.

В функциональных интерфейсах нет необходимости использовать ключевое слово abstract, поскольку это необязательно, поскольку по умолчанию метод, определенный внутри интерфейса, является только абстрактным. Мы также можем вызывать лямбда-выражения как экземпляр функционального интерфейса.

***Аннотация @FunctionalInterface***
Аннотация @FunctionalInterface используется для того, чтобы гарантировать, что функциональный интерфейс не может иметь более одного абстрактного метода. В случае наличия более одного абстрактного метода компилятор выдает сообщение «Неожиданная аннотация @FunctionalInterface». Однако использование этой аннотации не является обязательным.


- **Runnable –>** This interface only contains the run() method.
- **Comparable –>** This interface only contains the compareTo() method.
- **ActionListener –>** This interface only contains the actionPerformed() method.
- **Callable –>** This interface only contains the call() method.

1. **Consumer**
2. **Predicate**
3. **Function** 
4. **Supplier**

1. Consumer -> Bi-Consumer
2. Predicate -> Bi-Predicate
3. Function -> Bi-Function, Unary Operator, Binary Operator


### ***Consumer***
```java
Consumer<Integer> consumer = (value) -> System.out.println(value);

Consumer<Integer> display = a -> System.out.println(a);
display.accept(10);
```
Consumer — DoubleConsumer, IntConsumer, and LongConsumer

### ***Predicate***
```java
Predicate predicate = (value) -> value != null;

Predicate<Integer> lesserthan = i -> (i <` `18``); 
lesserthan.test(``10``);
```

### ***Function***
который получает только один аргумент и возвращает значение после необходимой обработки
1. apply()
2. andThen()
3. compose()
4. identity()
```java

Function<Integer, Double> half = a -> a / 2.0;
        half.apply(10);


Function<Integer, Double> half = a -> a / 2.0;
        half = half.andThen(a -> 3 * a);
        System.out.println(half.apply(10));

```

### ***Supplier***
Supplier также является типом функционального интерфейса, который не принимает никаких входных данных или аргументов и при этом возвращает один выходной сигнал. Этот тип функционального интерфейса обычно используется при ленивой генерации значений.
```java

T get()

```
### ***UnaryOperator***
это функциональный интерфейс, который представляет операцию над одним операндом одного и того же типа, возвращающую результат того же типа. Другими словами, он принимает один аргумент и возвращает результат того же типа.
```java
@FunctionalInterface
public interface UnaryOperator<T> extends Function<T, T> { 
	static <T> UnaryOperator<T> identity() { return t -> t; } 
}
```

## Not Predicate Method java11

A static [_not_ method](https://www.baeldung.com/java-negate-predicate-method-reference) has been added to the _Predicate_ interface. We can use it to negate an existing predicate, much like the _negate_ method:

```java
List<String> sampleList = Arrays.asList("Java", "\n \n", "Kotlin", " ");
List withoutBlanks = sampleList.stream()
  .filter(Predicate.not(String::isBlank))
  .collect(Collectors.toList());
assertThat(withoutBlanks).containsExactly("Java", "Kotlin");
```