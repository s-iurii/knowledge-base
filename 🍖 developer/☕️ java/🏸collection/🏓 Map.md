https://habr.com/ru/articles/237043/
 [[🏸 Collections]]

**[Map](http://docs.oracle.com/javase/8/docs/api/java/util/Map.html)**. Данный интерфейс также находится в составе JDK c версии 1.2 и предоставляет разработчику базовые методы для работы с данными вида «ключ — значение».Также как и `Collection`, он был дополнен дженериками в версии Java 1.5 и в версии Java 8 появились дополнительные методы для работы с лямбдами, а также методы, которые зачастую реализовались в логике приложения (`getOrDefault(Object key, V defaultValue)`, `putIfAbsent(K key, V value)`).  


#### Интерфейс Map [[doc](http://docs.oracle.com/javase/8/docs/api/java/util/Map.html)]

![[map_interface.png]]


## Methods

- `put(K, V)` - Inserts the association of a key K and a value V into the map. If the key is already present, the new value replaces the old value.
- `putAll()` - Inserts all the entries from the specified map to this map.
- `putIfAbsent(K, V)` - Inserts the association if the key K is not already associated with the value V.
- `get(K)` - Returns the value associated with the specified key K. If the key is not found, it returns `null`.
- `getOrDefault(K, defaultValue)` - Returns the value associated with the specified key K. If the key is not found, it returns the defaultValue.
- `containsKey(K)` - Checks if the specified key K is present in the map or not.
- `containsValue(V)` - Checks if the specified value V is present in the map or not.
- `replace(K, V)` - Replace the value of the key K with the new specified value V.
- `replace(K, oldValue, newValue)` - Replaces the value of the key K with the new value newValue only if the key K is associated with the value oldValue.
- `remove(K)` - Removes the entry from the map represented by the key K.
- `remove(K, V)` - Removes the entry from the map that has key K associated with value V.
- `keySet()` - Returns a set of all the keys present in a map.
- `values()` - Returns a set of all the values present in a map.
- `entrySet()` - Returns a set of all the key/value mapping present in a map.

**[Hashtable](http://docs.oracle.com/javase/8/docs/api/java/util/Hashtable.html)** — реализация такой структуры данных, как хэш-таблица. Она не позволяет использовать `null` в качестве значения или ключа. Эта коллекция была реализована раньше, чем Java Collection Framework, но в последствии была включена в его состав. Как и другие коллекции из Java 1.0, `Hashtable` является синхронизированной (почти все методы помечены как `synchronized`). Из-за этой особенности у неё имеются существенные проблемы с производительностью и, начиная с Java 1.2, в большинстве случаев рекомендуется использовать другие реализации интерфейса `Map` ввиду отсутствия у них синхронизации.

[[🧀 HashMap]]
[[🏓 Map#Methods]]

**[LinkedHashMap](http://docs.oracle.com/javase/8/docs/api/java/util/LinkedHashMap.html)** — это упорядоченная реализация хэш-таблицы. Здесь, в отличии от `HashMap`, порядок итерирования равен порядку добавления элементов. Данная особенность достигается благодаря двунаправленным связям между элементами (аналогично `LinkedList`). Но это преимущество имеет также и недостаток — увеличение памяти, которое занимет коллекция. Более подробная информация изложена в этой [статье](http://habrahabr.ru/post/129037/).

**[TreeMap](http://docs.oracle.com/javase/8/docs/api/java/util/TreeMap.html)** — реализация `Map` основанная на красно-чёрных деревьях. Как и `LinkedHashMap` является упорядоченной. По-умолчанию, коллекция сортируется по ключам с использованием принципа "[natural ordering](http://docs.oracle.com/javase/8/docs/api/java/lang/Comparable.html)", но это поведение может быть настроено под конкретную задачу при помощи объекта `Comparator`, который указывается в качестве параметра при создании объекта `TreeMap`.

**[WeakHashMap](http://docs.oracle.com/javase/8/docs/api/java/util/WeakHashMap.html)** — реализация хэш-таблицы, которая организована с использованием [weak references](http://docs.oracle.com/javase/8/docs/api/java/lang/ref/WeakReference.html). Другими словами, Garbage Collector автоматически удалит элемент из коллекции при следующей сборке мусора, если на ключ этого элеметна нет жёстких ссылок.
# интересные методы:
##  compute()
https://ru.hexlet.io/courses/java-functions/lessons/compute-in-maps/theory_unit

Метод `compute()` обновляет значение ключа в `Map`, на основе логики, заданной внутри лямбда-функции. Эта лямбда-функция получает на вход текущее значение ключа, выполняет с ним необходимые операции и возвращает новое значение.

```
import java.util.List;
import java.util.HashMap;

public class WordCountExample {
    public static void main(String[] args) {
        var words = List.of("apple", "banana", "apple", "orange", "banana", "apple");
        var wordCount = new HashMap<String, Integer>();

        words.forEach((word) -> {
            // Для данной задачи key не используется
            wordCount.compute(word, (key, count) -> count == null ? 1 : count + 1);
        });

        System.out.println(wordCount); // => {orange=1, banana=2, apple=3}
    }
}
```

В примере выше, метод `compute()` вызывается для каждого слова из списка. Лямбда-функция принимает на вход ключ и значение, которое является количеством повторений слова в списке. Дальше в зависимости от того, первый ли раз встречается это слово или нет, изменяется количество повторений. Без `compute()` нам бы пришлось написать код похожий на этот:

## computeIfPresent()

Метод `computeIfPresent()` отличается от `compute()` тем, что лямбда вызывается только в том случае, если ключ уже был добавлен в коллекцию. Ниже пример кода, который применяет скидку к товарам, находящимся внутри коллекции без проверки того, есть ли они там на самом деле:

```
import java.util.HashMap;

public class DiscountExample {
    public static void main(String[] args) {
        var prices = new HashMap<String, Double>();
        prices.put("T-shirt", 20.0);
        prices.put("Jeans", 40.0);

        // Применяет 10% скидку только если такой товар существует
        prices.computeIfPresent("Jeans", (key, value) -> value * 0.9);

        // Ничего не происходит, так как такого товара нет
        prices.computeIfPresent("Socks", (key, value) -> value * 0.9);

        System.out.println(prices); // => {T-shirt=20.0, Jeans=36.0}
```

- ***computeIfAbsent***

Как работает `computeIfAbsent`:

- Если по данному ключу в мапе уже существует значение (т.е. `map.containsKey(key)` возвращает `true`), метод возвращает это значение и ничего не меняет.
- Если ключ отсутствует в мапе (т.е. `map.containsKey(key)` возвращает `false`), метод вызывает функцию `mappingFunction` для вычисления нового значения, добавляет это значение в мапу под данным ключом и возвращает его.

```
Map<String, List<String>> studentGroups = new HashMap<>(); // Добавление 
студента в группу 
	studentGroups.computeIfAbsent("Group1", k -> new ArrayList<>()).add("John Doe");
```



- ***getOrDefault***

 Как работает `getOrDefault`:
 
- Если по указанному ключу в мапе уже существует значение (т.е. `map.containsKey(key)` возвращает `true`), метод возвращает это значение.
- Если ключ отсутствует в мапе (т.е. `map.containsKey(key)` возвращает `false`), метод возвращает переданное значение `defaultValue`.


```
Map<String, Integer> scores = new HashMap<>();
scores.put("Alice", 10);
scores.put("Bob", 15);

// Получение очков для существующего игрока int aliceScore = scores.getOrDefault("Alice", 0); // вернет 10 
// Попытка получить очки для игрока, которого нет в мапе int charlieScore = scores.getOrDefault("Charlie", 0); // вернет 0
```

