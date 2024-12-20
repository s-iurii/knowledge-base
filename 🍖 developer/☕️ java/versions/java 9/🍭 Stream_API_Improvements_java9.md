
В Java SE 9 корпорация Oracle добавила четыре новых полезных метода в интерфейс java.util.Stream. Поскольку Stream — это интерфейс, все эти новые реализованные методы являются методами по умолчанию. Он позволяет создавать декларативные конвейеры преобразований для коллекций. В интерфейс Stream добавлено четыре новых метода: dropWhile, takeWhile, ofNullable. Метод iterate получает новую перегрузку, что позволяет указать предикат, когда следует остановить итерацию.

### 1. `dropWhile`

Метод `dropWhile` был добавлен в Java 9 для работы с потоками (`Stream`). Этот метод возвращает оставшуюся часть потока после того, как был найден первый элемент, который не соответствует условию предиката. Другими словами, он "отбрасывает" элементы с начала потока, пока не встретится элемент, который не удовлетворяет предикату, и возвращает поток, начиная с этого элемента.

```java
List<Integer> numbers = List.of(1, 2, 3, 4, 5, 6, 7, 8, 9, 10); List<Integer> result = numbers.stream() .dropWhile(n -> n < 5) .collect(Collectors.toList()); System.out.println(result); // [5, 6, 7, 8, 9, 10]
```

### 2. `takeWhile`

Метод `takeWhile` также был добавлен в Java 9 и работает аналогично `dropWhile`, но с противоположным эффектом. Он берет элементы из потока, пока они удовлетворяют условию предиката, и прекращает, как только первый элемент не удовлетворяет условию.


```java
List<Integer> numbers = List.of(1, 2, 3, 4, 5, 6, 7, 8, 9, 10);
List<Integer> result = numbers.stream()
	.takeWhile(n -> n < 5)     
	.collect(Collectors.toList());  
System.out.println(result);  // [1, 2, 3, 4]
```

### 3. `ofNullable`

Метод `Stream.ofNullable` был добавлен в Java 9 и позволяет создать поток, содержащий один элемент, если он не является `null`, или пустой поток, если элемент равен `null`.

```java
String name = "Yuri";
Stream<String> stream = Stream.ofNullable(name); stream.forEach(System.out::println); // Выводит: Yuri 

name = null;
stream = Stream.ofNullable(name);
stream.forEach(System.out::println);// Не выводит ничего, поток пустой
```

### 4. `iterate`

Метод `Stream.iterate` в Java позволяет создавать бесконечные потоки, применяя функцию к начальному значению и затем к каждому последующему результату. В Java 9 была добавлена перегрузка метода `iterate`, которая принимает также условие окончания потока.

```java
Stream<Integer> evenNumbers = Stream.iterate(0, n -> n <= 20, n -> n + 2); List<Integer> result = evenNumbers.collect(Collectors.toList()); System.out.println(result); // [0, 2, 4, 6, 8, 10, 12, 14, 16, 18, 20]
```