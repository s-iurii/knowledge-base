
# **groupingBy**

https://www.baeldung.com/java-groupingby-collector
https://www.baeldung.com/java-collectors

### **Простая группировка по одному столбцу**

```java
Map<BlogPostType, List<BlogPost>> postsPerType = posts.stream() .collect(groupingBy(BlogPost::getType));
```

### **_groupingBy_ с типом сложного ключа _карты_**

```java
Map<Pair<BlogPostType, String>, List<BlogPost>> postsPerTypeAndAuthor = posts.stream() .collect(groupingBy(post -> new ImmutablePair<>(post.getType(), post.getAuthor())));


Map<Tuple, List<BlogPost>> postsPerTypeAndAuthor = posts.stream() .collect(groupingBy(post -> new Tuple(post.getType(), post.getAuthor())));
```

### **Изменение типа возвращаемого значения _карты_**

```java
Map<BlogPostType, Set<BlogPost>> postsPerType = posts.stream() .collect(groupingBy(BlogPost::getType, toSet()));
```

### **Группировка по нескольким полям**

```java
Map<String, Map<BlogPostType, List>> map = posts.stream() .collect(groupingBy(BlogPost::getAuthor, groupingBy(BlogPost::getType)));
```

### **Получение среднего значения из сгруппированных результатов**

```java
Map<BlogPostType, Double> averageLikesPerType = posts.stream() .collect(groupingBy(BlogPost::getType, averagingInt(BlogPost::getLikes)));
```

### **Получение суммы из сгруппированных результатов**


```java
Map<BlogPostType, Integer> likesPerType = posts.stream() .collect(groupingBy(BlogPost::getType, summingInt(BlogPost::getLikes)));
```


## **Класс рабочего, над которым будем ставить эксперименты**

```
public class Worker{    private String name;    private int age;    private int salary;    private String position;    public Worker(String name, int age, int salary, String position) {        this.name = name;        this.age = age;        this.salary = salary;        this.position = position;    }    public String getName() {        return name;    }    public int getAge() {        return age;    }    public int getSalary() {        return salary;    }    public String getPosition() {        return position;    }}
```

  

#### 1. Группировка списка рабочих по их должности (деление на списки)

```
 Map<String, List<Worker>> map1 = workers.stream()       .collect(Collectors.groupingBy(Worker::getPosition));
```


#### 2. Группировка списка рабочих по их должности (деление на множества)

  

```
Map<String, Set<Worker>> map2 = workers.stream()       .collect(Collectors.groupingBy(Worker::getPosition, Collectors.toSet()));
```

  

#### 3. Подсчет количества рабочих, занимаемых конкретную должность

  

```
Map<String, Long> map3 = workers.stream()       .collect(Collectors.groupingBy(Worker::getPosition, Collectors.counting()));
```

  

#### 4. Группировка списка рабочих по их должности, при этом нас интересуют только имена

  

```
Map<String, Set<String>> map4 = workers.stream()       .collect(Collectors.groupingBy(Worker::getPosition,               Collectors.mapping(Worker::getName, Collectors.toSet())));
```

  

#### 5. Расчет средней зарплаты для данной должности

  

```
Map<String, Double> map5 = workers.stream()       .collect(Collectors.groupingBy(Worker::getPosition,              Collectors.averagingInt(Worker::getSalary)));
```

  

#### 6. Группировка списка рабочих по их должности, рабочие представлены только именами единой строкой

  

```
Map<String, String> map6 = workers.stream()       .collect(Collectors.groupingBy(Worker::getPosition,              Collectors.mapping(Worker::getName,                      Collectors.joining(", ", "{","}")))       );
```

  

#### 7. Группировка списка рабочих по их должности и по возрасту.

  

_Подсказал пользователь j2ck_

  

```
Map<String, Map<Integer, List<Worker>>> collect = workers.stream()       .collect(Collectors.groupingBy(Worker::getPosition,               Collectors.groupingBy(Worker::getAge)));
```


# **comparing**

```java
list.stream()  
        .sorted(Comparator.comparing(Worker::getName))  
        .map(Worker::getName)  
        .collect(Collectors.toList());


list.stream()  
    .sorted(Comparator.comparing(Worker::getName).reversed()) 
        .map(Worker::getName)  
        .collect(Collectors.toList());
```

# Convert from

**from char**
```java

char[] charArray = {'a', 'b', 'c'};
Stream<Character> charStream = IntStream
.range(0, charArray.length) 
.mapToObj(i -> charArray[i]);



```
**from Arrey**
```java

int[] arr = {1, 2, 3, 4, 5, 6, 7, 8, 90, 100, 1001};  
Arrays.stream(arr)  
        .boxed()  
        .collect(Collectors.toList());



Integer[] numbers = new Integer[] { 1, 2, 3 };  
List<Integer> list = Arrays.asList(numbers);
list.stream()

```


# IntStream в Java

## 1. Создание IntStream

Существует несколько способов создания `IntStream`.

### [](https://howtodoinjava.com/java8/intstream-examples/#1-1-with-specified-values)1.1 С указанными значениями

Эта функция возвращает последовательный упорядоченный поток, элементами которого являются указанные значения.

Он поставляется в двух версиях: поток с одним элементом и поток с несколькими значениями.

- `IntStream of(int t)`– Возвращает поток, содержащий один указанный элемент.
- `IntStream of(int... values)`– Возвращает поток, содержащий все указанные элементы.
### 1.2 Генерация целых чисел в диапазоне

Созданный `IntStream`методами `range()`последовательный упорядоченный поток значений int, который является эквивалентной последовательностью увеличивающихся значений int в цикле for и значения, увеличенного на 1. Этот класс поддерживает два метода.

- range(int start, int end) – возвращает последовательный упорядоченный поток целых чисел от startInclusive ( _включительно_ ) до endExclusive ( _исключительно_ ) с шагом 1.
- rangeClosed(int start, int end) — возвращает последовательный упорядоченный поток целых чисел от startInclusive ( _включительно_ ) до endInclusive ( _включительно_ ) с шагом 1.

```java
IntStream.range(1, 5);  	//1,2,3,4

IntStream.rangeClosed(1, 5);  	//1,2,3,4,5
```

### [](https://howtodoinjava.com/java8/intstream-examples/#1-3-infinite-streams-with-iteration)1.3 Бесконечные потоки с итерацией

Функция `iterator()`полезна для создания [бесконечных потоков](https://howtodoinjava.com/java8/java-infinite-stream/) . Также мы можем использовать этот метод для создругое значение, кроме 1.

В данном примере выводятся первые 10 четных чисел, начиная с 0.

```java
IntStream.iterate(0, i -> i + 2).limit(10);	

//0,2,4,6,8,10,12,14,16,18
```

### 1.4 Бесконечные потоки с IntSupplier

Метод `generate()`очень похож на iterator(), но отличается тем, что не вычисляет значения int путем увеличения предыдущего значения. Вместо этого предоставляется [IntSupplier , который является](https://docs.oracle.com/javase/8/docs/api/java/util/function/IntSupplier.html) [функциональным интерфейсом](https://howtodoinjava.com/java/stream/functional-interface-tutorial/) , используемым для генерации бесконечного последовательного **неупорядоченного** потока значений int.

В следующем примере создается поток из 10 случайных чисел, а затем выводится их в консоли.

```java
IntStream stream = IntStream
    .generate(() -> { return (int)(Math.random() * 10000); }); 

stream.limit(10).forEach(System.out::println);
```

## [](https://howtodoinjava.com/java8/intstream-examples/#2-iterating-over-values)2. Итерация значений

Для циклического перебора элементов поток поддерживает операцию [forEach()](https://howtodoinjava.com/java8/java-stream-foreach/) . Чтобы заменить простой [цикл for](https://howtodoinjava.com/java/flow-control/for-loop-in-java/) с помощью `IntStream`, следуйте тому же подходу.

```java
IntStream.rangeClosed(0, 4)
			.forEach( System.out::println );
```

## [](https://howtodoinjava.com/java8/intstream-examples/#3-filtering-the-values)3. Фильтрация значений

Мы можем применить фильтрацию к значениям _int,_ созданным потоком, и использовать их в другой функции или собрать для дальнейшей обработки.

Например, мы можем перебирать значения типа int и фильтровать/собирать все простые числа до определенного предела.
```java
IntStream stream = IntStream.range(1, 100); 

List<Integer> primes = stream.filter(ThisClass::isPrime)
			.boxed()
			.collect(Collectors.toList());

public static boolean isPrime(int i)
{
    IntPredicate isDivisible = index -> i % index == 0;
    return i > 1 && IntStream.range(2, i).noneMatch(isDivisible);
}
```

## [](https://howtodoinjava.com/java8/intstream-examples/#4-converting-intstream-to-array)4. Преобразование IntStream в массив

Используйте метод **IntStream.toArray()** для преобразования потока в массив _int ._

```java
int[] intArray = IntStream.of(1, 2, 3, 4, 5).toArray();
```

## [](https://howtodoinjava.com/java8/intstream-examples/#5-converting-intstream-to-list)5. Преобразование IntStream в список

Коллекции в Java не могут хранить примитивные значения напрямую. Они могут хранить только экземпляры/объекты.
Используя `boxed()`метод `IntStream`, мы можем получить поток объектов-оберток, которые могут быть собраны `Collectors`методами.

```java
List<Integer> list = IntStream.of(1,2,3,4,5)
            .boxed()
            .collect(Collectors.toList());
```