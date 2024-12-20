[[☕️ Java]]

The Java collections framework provides various interfaces. These interfaces include several methods to perform different operations on collections.

![[Java-Collections.webp]]

# Collection Interface

The `Collection` interface is the root interface of the collections framework hierarchy.
Java does not provide direct implementations of the `Collection` interface but provides implementations of its subinterfaces like `List`, `Set`, and `Queue`. To learn more, visit: [Java Collection Interface](https://www.programiz.com/java-programming/collection-interface "Java Collection Interface")

### Collections Framework Vs. Collection Interface

People often get confused between the collections framework and `Collection` Interface.

The `Collection` interface is the root interface of the collections framework. The framework includes other interfaces as well: `Map` and `Iterator`. These interfaces may also have subinterfaces.

![[Java-collection-interface.png]]

## Methods of Collection

The `Collection` interface includes various methods that can be used to perform different operations on objects. These methods are available in all its subinterfaces.

- `add()` - inserts the specified element to the collection
- `size()` - returns the size of the collection
- `remove()` - removes the specified element from the collection
- `iterator()` - returns an iterator to access elements of the collection
- `addAll()` - adds all the elements of a specified collection to the collection
- `removeAll()` - removes all the elements of the specified collection from the collection
- `clear()` - removes all the elements of the collection
- `isEmpty()`
- `contains`
- `containsAll`
# Lterator Interface
In Java, the `Iterator` interface provides methods that can be used to access elements of collections.
All the Java collections include an `iterator()` method. This method returns an instance of iterator used to iterate over elements of collections.
### Methods of Iterator

The `Iterator` interface provides 4 methods that can be used to perform various operations on elements of collections.

- `hasNext()` - returns `true` if there exists an element in the collection
- `next()` - returns the next element of the collection
- `remove()` - removes the last element returned by the `next()`
- `forEachRemaining()` - performs the specified action for each remaining element of the collection

```java
import java.util.ArrayList;
import java.util.Iterator;

class Main {
    public static void main(String[] args) {
        // Creating an ArrayList
        ArrayList<Integer> numbers = new ArrayList<>();
        numbers.add(1);
        numbers.add(3);
        numbers.add(2);
        System.out.println("ArrayList: " + numbers);

        // Creating an instance of Iterator
        Iterator<Integer> iterate = numbers.iterator();

        // Using the next() method
        int number = iterate.next();
        System.out.println("Accessed Element: " + number);

        // Using the remove() method
        iterate.remove();
        System.out.println("Removed Element: " + number);

        System.out.print("Updated ArrayList: ");

        // Using the hasNext() method
        while(iterate.hasNext()) {
            // Using the forEachRemaining() method
            iterate.forEachRemaining((value) -> System.out.print(value + ", "));
        }
    }
}
```


# ListIterator Interface

специальный интерфейс в Java, который является расширенной версией `Iterator` и предназначен для итерации по элементам списков (`List`). В отличие от обычного `Iterator`, `ListIterator` предоставляет дополнительные возможности для навигации по списку и изменения его элементов во время итерации.

- `boolean hasNext()` - Проверяет, есть ли следующий элемент в списке. 
- `E next()` - Возвращает следующий элемент или  `NoSuchElementException`.
- `boolean hasPrevious()` - Проверяет, есть ли предыдущий элемент.
- `E previous()` - Возвращает предыдущий элемент или  `NoSuchElementException`.
- `int nextIndex()`- Возвращает индекс следующего элемента.
- `int previousIndex()` - Возвращает индекс предыдущего элемента.
- `void remove()`- Удаляет последний элемент.
- `void set(E e)`- Заменяет последний элемент.
- `void add(E e)` - Вставляет элемент `e` перед элементом, который будет возвращен методом `next()`

```java
ListIterator<String> iterator = fruits.listIterator();

System.out.println("Итерация вперед:"); 
while (iterator.hasNext()) { 
	int index = iterator.nextIndex(); 
	String fruit = iterator.next(); 
	System.out.println("Индекс: " + index + ", Элемент: " + fruit); 
} 
System.out.println("\nИтерация назад:"); 
while (iterator.hasPrevious()) { 
	int index = iterator.previousIndex(); 
	String fruit = iterator.previous(); 
	System.out.println("Индекс: " + index + ", Элемент: " + fruit); 
}
```

Только коллекции, реализующие интерфейс **`List`** (такие как `ArrayList`, `LinkedList`), предоставляют метод `listIterator()`

 `ListIterator` **не является потокобезопасным**. Если список модифицируется из нескольких потоков одновременно, необходимо обеспечить внешнюю синхронизацию.

# **примитивные типы ы коллекциях**

это сочетание двух фактов:

- примитивные типы Java не являются ссылочными типами (например,`int` - Это не `Object`)
- Java делает дженерики, используя стирание типа ссылочных типов (например, a `List<?>` действительно `List<Object>` во время выполнения)

поскольку оба они истинны, общие коллекции Java не могут хранить примитивные типы напрямую. Для удобства, **autoboxing** введен для того чтобы позволить примитивным типам автоматически быть упакованным как ссылочный тип. Не ошибитесь в этом, хотя коллекции по-прежнему сохраняют ссылки на объекты независимо.
# [[🧅 List]]
# [[🏓 Map]] , [[SortedMap]], [[NavigableMap]]
# [[🫒 Set]]
# [[🍳 Queue]]

![[collection_compare.png]]
## интересные методы

### ***nCopies***

### ***removeIf***

Метод проходит по коллекции и применяет заданный предикат к каждому элементу. Если предикат возвращает `true` для какого-то элемента, этот элемент удаляется из коллекции.

```
List<Integer> numbers = new ArrayList<>(Arrays.asList(1, 2, 3, 4, 5, 6, 7, 8, 9, 10)); 
// Удаляем все четные числа numbers.removeIf(n -> n % 2 == 0); System.out.println(numbers); // Выведет: [1, 3, 5, 7, 9]
```

### _toArray_


The _java.util.Collection_ interface contains a new default _toArray_ method which takes an _IntFunction_ argument.
This makes it easier to create an array of the right type from a collection:

```java
List sampleList = Arrays.asList("Java", "Kotlin");
String[] sampleArray = sampleList.toArray(String[]::new);
assertThat(sampleArray).containsExactly("Java", "Kotlin");
```

###  Sequenced Collections
В фреймворке коллекций Java ни один тип коллекции не представляет последовательность элементов с определенным порядком встреч. Например, интерфейсы _List_ и _Deque_ определяют порядок встреч, но их общий супертип _Collection_ не определяет. Точно так же _Set_ не определяет порядок встреч, но подтипы, такие как _LinkedHashSet_ или _SortedSet_ , определяют.

**В Java 21 появились три новых интерфейса для представления упорядоченных коллекций, упорядоченных наборов и упорядоченных карт.**

Упорядоченная [коллекция](https://www.baeldung.com/java-21-sequenced-collections) — это коллекция, элементы которой имеют определенный порядок встреч. Она имеет первый и последний элементы, а элементы между ними имеют последователей и предшественников. Упорядоченный набор — это набор, который является упорядоченной коллекцией без повторяющихся элементов. Упорядоченная карта — это карта, записи которой имеют определенный порядок встреч.

На следующей диаграмме показана модернизация новых интерфейсов в иерархии фреймворка коллекции:

[![Последовательные коллекции](https://www.baeldung.com/wp-content/uploads/2024/04/SequencedCollections.png)](https://www.baeldung.com/wp-content/uploads/2024/04/SequencedCollections.png)
