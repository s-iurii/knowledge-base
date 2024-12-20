[[🏸 Collections]]

![[Java-list-interface.png]]


# Methods


- `add(E e)` - inserts the specified element at the end of the list.
- `add(int index, E element)` - inserts the specified element at the specified position in the list.
- `addAll(Collection<? extends E> c)` - adds all elements from the specified collection to the end of the list.
- `addAll(int index, Collection<? extends E> c)` - inserts all elements from the specified collection into the list at the specified position.
- `size()` - returns the number of elements in the list.
- `remove(int index)` - removes the element at the specified position in the list.
- `remove(Object o)` - removes the first occurrence of the specified element from the list, if it is present.
- `removeAll(Collection<?> c)` - removes from the list all elements that are also contained in the specified collection.
- `retainAll(Collection<?> c)` - retains only the elements in the list that are contained in the specified collection.
- `clear()` - removes all elements from the list.
- `get(int index)` - returns the element at the specified position in the list.
- `set(int index, E element)` - replaces the element at the specified position in the list with the specified element.
- `indexOf(Object o)` - returns the index of the first occurrence of the specified element in the list, or -1 if the list does not contain the element.
- `lastIndexOf(Object o)` - returns the index of the last occurrence of the specified element in the list, or -1 if the list does not contain the element.
- `isEmpty()` - returns `true` if the list contains no elements.
- `contains(Object o)` - returns `true` if the list contains the specified element.
- `containsAll(Collection<?> c)` - returns `true` if the list contains all elements in the specified collection.
- `iterator()` - returns an iterator over the elements in the list in proper sequence.
- `listIterator()` - returns a list iterator over the elements in the list (starting at the beginning).
- `listIterator(int index)` - returns a list iterator over the elements in the list, starting at the specified position in the list.
- `subList(int fromIndex, int toIndex)` - returns a view of the portion of this list between the specified `fromIndex`, inclusive, and `toIndex`, exclusive.
- `toArray()` - returns an array containing all the elements in the list in proper sequence.
- `toArray(T[] a)` - returns an array containing all the elements in the list in proper sequence; the runtime type of the returned array is that of the specified array.
- `equals(Object o)` - compares the specified object with this list for equality.
- `hashCode()` - returns the hash code value for this list.
- `spliterator()` - creates a `Spliterator` over the elements in the list.


# Classes that Implement List

- [[🥐 ArrayList]]
- [[🍠 LinkedList]]

**[Vector](http://docs.oracle.com/javase/8/docs/api/java/util/Vector.html)** — реализация динамического массива объектов. Позволяет хранить любые данные, включая null в качестве элемента. `Vector` появился в JDK версии Java 1.0, но как и `Hashtable`, эту коллекцию не рекомендуется использовать, если не требуется достижения потокобезопасности. Потому как в `Vector`, в отличии от других реализаций `List`, все операции с данными являются синхронизированными. В качестве альтернативы часто применяется аналог — `ArrayList`.  
  
**[Stack](http://docs.oracle.com/javase/8/docs/api/java/util/Stack.html)** — данная коллекция является расширением коллекции `Vector`. Была добавлена в Java 1.0 как реализация стека LIFO (last-in-first-out). Является частично синхронизированной коллекцией (кроме метода добавления `push()`). После добавления в Java 1.6 интерфейса `Deque`, рекомендуется использовать именно реализации этого интерфейса, например `ArrayDeque`.