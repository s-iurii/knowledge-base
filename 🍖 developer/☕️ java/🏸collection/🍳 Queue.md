[[🏸 Collections]]


Этот интерфейс описывает коллекции с предопределённым способом вставки и извлечения элементов, а именно — очереди FIFO (first-in-first-out). Помимо методов, определённых в интерфейсе Collection, определяет дополнительные методы для извлечения и добавления элементов в очередь. Большинство реализаций данного интерфейса находится в пакете `java.util.concurrent` и подробно рассматриваются в [данном](http://habrahabr.ru/company/luxoft/blog/157273/) обзоре.
## Methods of Queue

The `Queue` interface includes all the methods of the `Collection` interface. It is because `Collection` is the super interface of `Queue`.

Some of the commonly used methods of the `Queue` interface are:

- **add()** - Inserts the specified element into the queue. If the task is successful, `add()` returns `true`, if not it throws an [exception](https://www.programiz.com/java-programming/exceptions).
- **offer()** - Inserts the specified element into the queue. If the task is successful, `offer()` returns `true`, if not it returns `false`.
- **element()** - Returns the head of the queue. Throws an exception if the queue is empty.
- **peek()** - Returns the head of the queue. Returns `null` if the queue is empty.
- **remove()** - Returns and removes the head of the queue. Throws an exception if the queue is empty.
- **poll()** - Returns and removes the head of the queue. Returns `null` if the queue is empty.

**[PriorityQueue](http://docs.oracle.com/javase/8/docs/api/java/util/PriorityQueue.html)** — является единственной прямой реализацией интерфейса `Queue` (была добавлена, как и интерфейс Queue, в Java 1.5), не считая класса `LinkedList`, который так же реализует этот интерфейс, но был реализован намного раньше. Особенностью данной очереди является возможность управления порядком элементов. По-умолчанию, элементы сортируются с использованием «natural ordering», но это поведение может быть переопределено при помощи объекта `Comparator`, который задаётся при создании очереди. Данная коллекция не поддерживает `null` в качестве элементов.

**[ArrayDeque](http://docs.oracle.com/javase/8/docs/api/java/util/ArrayDeque.html)** — реализация интерфейса [Deque](http://docs.oracle.com/javase/8/docs/api/java/util/Deque.html), который расширяет интерфейс `Queue` методами, позволяющими реализовать конструкцию вида LIFO (last-in-first-out). Интерфейс `Deque` и реализация `ArrayDeque` были добавлены в Java 1.6. Эта коллекция представляет собой реализацию с использованием массивов, подобно `ArrayList`, но не позволяет обращаться к элементам по индексу и хранение `null`. Как заявлено в документации, коллекция работает быстрее чем `Stack`, если используется как LIFO коллекция, а также быстрее чем LinkedList, если используется как FIFO.