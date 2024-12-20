
[[🏆 Java8]]

Comparable and Comparator are interfaces used to order objects. They are particularly useful in sorting operations and collections that require natural ordering. Here we will learn about Comparable and Comparator in depth.


## **Comparable**

Сравнимый объект способен сравнивать себя с другим объектом. Сам класс должен реализовывать интерфейс **java.lang.Comparable** для сравнения своих экземпляров.   
Рассмотрим класс Movie, который имеет такие члены, как рейтинг, название, год. Предположим, мы хотим отсортировать список фильмов по году выпуска. Мы можем реализовать интерфейс Comparable с классом Movie и переопределить метод compareTo() интерфейса Comparable.

```
class Movie implements Comparable<Movie> {

    private double rating;
    private String name;
    private int year;

    public int compareTo(Movie m) {
        return this.year - m.year;

    }
}

//использование
Collections.sort(list);
```


## Comparator

Теперь предположим, что мы хотим сортировать фильмы по рейтингу и названиям. Когда мы делаем элемент коллекции сопоставимым (реализовав Comparable), у нас есть только один шанс реализовать метод compareTo(). Решение — использовать [Comparator.](https://www.geeksforgeeks.org/comparator-interface-java/)

В отличие от Comparable, Comparator является внешним по отношению к типу элемента, который мы сравниваем. Это отдельный класс. Мы создаем несколько отдельных классов (которые реализуют Comparator) для сравнения по разным членам.  
Класс Collections имеет второй метод sort(), и он принимает Comparator. Метод sort() вызывает compare() для сортировки объектов.

```
class NameCompare implements Comparator<Movie> {

    public int compare(Movie m1, Movie m2){
        return m1.getName().compareTo(m2.getName());
    }
}

//использование
Collections.sort(list, nameCompare);
```