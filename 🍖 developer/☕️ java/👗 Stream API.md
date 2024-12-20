[[☕️ Java]]


# groupingBy

https://www.baeldung.com/java-groupingby-collector


```java
class BlogPost { 
String title;
String author;
BlogPostType type;
int likes; 
}

enum BlogPostType { NEWS, REVIEW, GUIDE }

//Простая группировка по одному столбцу
Map<String, List<BlogPost>> result = 
posts.stream()
.collect(Collectors.groupingBy(BlogPost::getAuthor));

//groupingBy с типом сложного ключа карты
Map<Pair<BlogPostType, String>, List<BlogPost>> pareResult = posts.stream()  
        .collect(Collectors.groupingBy(blog -> new Pair<>(blog.type, blog.author)  
));

//Изменение типа возвращаемого значения карты  
Map<BlogPostType, Set<BlogPost>> setResult = posts.stream()  
        .collect(Collectors.groupingBy(BlogPost::getType, Collectors.toSet()));

//Группировка по нескольким полям  
Map<String, Map<BlogPostType, List<BlogPost>>> map = posts.stream()  
        .collect(Collectors.groupingBy(BlogPost::getAuthor, Collectors.groupingBy(BlogPost::getType)));

```



# toMap

https://www.baeldung.com/java-collectors-tomap


```java
public Map<String, String> listToMap(List<Book> books) { return books.stream()
.collect(Collectors.toMap(Book::getIsbn, Book::getName)); 
													   }

public Map<Integer, Book> listToMapWithDupKeyError(List<Book> books) { 
return books.stream()
.collect( Collectors.toMap(Book::getReleaseYear, Function.identity())); 
}

public Map<Integer, Book> listToMapWithDupKey(List<Book> books) { 
returnbooks.stream()
.collect(Collectors.toMap(
	Book::getReleaseYear,
	Function.identity(),
	(existing, replacement) -> existing)); 
}

//mapSupplier — это функция, которая возвращает новую //пустую _карту_ с результатами.


Collectors.toMap(
	Book::getReleaseYear,
	Function.identity(),
	(o1, o2) -> o1,
	 ConcurrentHashMap::new) 
}

//с сортировкой
Collectors.toMap(
	Book::getName,
	Function.identity(), 
	(o1, o2) -> o1, 
	TreeMap::new)
```


# Function.identity()

```java

Map<String, String> map = names.stream() .collect(Collectors.toMap(Function.identity(), Function.identity()));

//тоже самое что 

.toMap(x -> x, x -> x)
```
