[[🏸 Collections]]

Представляет собой неупорядоченную коллекцию, которая не может содержать дублирующиеся данные. Является программной моделью математического понятия «множество».

![[set_interface.png]]


# Methods of Set

The `Set` interface includes all the methods of the `Collection` interface. It's because `Collection` is a super interface of `Set`.

Some of the commonly used methods of the `Collection` interface that's also available in the `Set` interface are:

- **add()** - adds the specified element to the set
- **addAll()** - adds all the elements of the specified collection to the set
- **iterator()** - returns an iterator that can be used to access elements of the set sequentially
- **remove()** - removes the specified element from the set
- **removeAll()** - removes all the elements from the set that is present in another specified set
- **retainAll()** - retains all the elements in the set that are also present in another specified set
- **clear()** - removes all the elements from the set
- **size()** - returns the length (number of elements) of the set
- **toArray()** - returns an array containing all the elements of the set
- **contains()** - returns `true` if the set contains the specified element
- **containsAll()** - returns `true` if the set contains all the elements of the specified collection
- **hashCode()** - returns a hash code value (address of the element in the set)

**[HashSet](http://docs.oracle.com/javase/8/docs/api/java/util/HashSet.html)** — реализация интерфейса `Set`, базирующаяся на `HashMap`. Внутри использует объект HashMap для хранения данных. В качестве ключа используется добавляемый элемент, а в качестве значения — объект-пустышка (new Object()). Из-за особенностей реализации порядок элементов не гарантируется при добавлении.

**[LinkedHashSet](http://docs.oracle.com/javase/8/docs/api/java/util/LinkedHashSet.html)** — отличается от `HashSet` только тем, что в основе лежит `LinkedHashMap` вместо `HashMap`. Благодаря этому отличию порядок элементов при обходе коллекции является идентичным порядку добавления элементов.

**[TreeSet](http://docs.oracle.com/javase/8/docs/api/java/util/TreeSet.html)** — аналогично другим классам-реализациям интерфейса `Set` содержит в себе объект `NavigableMap`, что и обуславливает его поведение. Предоставляет возможность управлять порядком элементов в коллекции при помощи объекта `Comparator`, либо сохраняет элементы с использованием "[natural ordering](http://docs.oracle.com/javase/8/docs/api/java/lang/Comparable.html)".
# характеристики
#### **Производительность (Performance):**

- **Вставка (Insertion):** `O(1)` амортизированная, `O(log n)` в худшем случае (при большом количестве коллизий, когда элементы в бакете организованы в красно-чёрное дерево).
- **Получение (Access):** Неприменимо, так как `HashSet` не поддерживает прямой доступ по индексу.
- **Удаление (Deletion):** `O(1)` амортизированная, `O(log n)` в худшем случае.
- **Поиск (Search):** `O(1)` амортизированная, `O(log n)` в худшем случае.
- **Итерация (Iteration):** Итерация по элементам в порядке, зависящем от хеш-функции, не гарантирует определённого порядка.

#### 2. **Память (Memory):**

- **Потребление памяти (Memory Consumption):** Хэш-таблица требует дополнительной памяти для хранения бакетов.
- **Capacity:** Начальный размер `HashSet` — 16 бакетов. При превышении коэффициента загрузки `load factor` происходит увеличение в два раза.
- **Load Factor:** По умолчанию `0.75`, что означает, что при заполнении 75% ёмкости происходит увеличение.
- **Резервирование памяти (Overhead):** Дополнительная память на массив бакетов и ссылки на цепочки (для коллизий).

#### 3. **Функциональность (Functionality):**

- **Null допускается (Null allowed):** Допускает один `null` элемент.
- **Изменяемость (Mutability):** Изменяемая коллекция (можно добавлять, удалять элементы).
- **Поддержка индексации (Indexing support):** Индексация не поддерживается.
- **Порядок (Ordering):** Не гарантирует порядка элементов.

#### 4. **Параллелизм и потокобезопасность (Concurrency and Thread Safety):**

- **Параллелизм (Concurrency):** Не потокобезопасный, требуется внешняя синхронизация для многопоточного доступа. Для потокобезопасной альтернативы можно использовать `ConcurrentHashSet` (можно создать из `ConcurrentHashMap`).

#### 5. **Дополнительные характеристики (Additional Characteristics):**

- **Особенности использования (Use Case Specifics):** Подходит для случаев, когда важно исключить дублирование и требуется быстрый доступ для проверки наличия элемента.
- **Поддержка потоков (Stream Support):** Полностью поддерживается.

