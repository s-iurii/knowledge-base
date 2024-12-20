

- **Mast usifull Exception**
    
    **IllegalArgumentException** - Неверное ненулевое значение параметра
    
    **IllegalStateException** - Неверное состояние объекта для вызова ме­ тода
    
    **NullPointerException** - Неразрешенное нулевое значение параметра
    
    **IndexOutOfBoundsException** - Индексный параметр за границей допусти­ мого диапазона
    
    **СоncurrentModificationException** - Обнаружено запрещенное параллельное из­ менение объекта
    
    **UnsupportedOperationException** - Объект не поддерживает метод
    
    **ArithmeticException** и **NumberFormatException**.
    
    **DataFormatException**
    
    **TimeoutException**
    
    **IOException**
    
    **GeneralSecurityException**
    
    **KeySelectorException**
    
    **RuntimeException**
    

![image.jpeg](image.jpeg)

[Курс Java Syntax Pro - Лекция: Виды исключений в Java](https://javarush.ru/quests/lectures/questsyntaxpro.level14.lecture03)

**Error Handling for REST with Spring**

[Error Handling for REST with Spring | Baeldung](https://www.baeldung.com/exception-handling-for-rest-with-spring)

- **Причины создания собственных исключений**
    - **Более точное описание ошибки**: Готовые исключения, такие как `IllegalArgumentException` или `NullPointerException`, могут не предоставлять достаточной информации о конкретной ошибке. Создание собственного исключения позволяет задать конкретное название и сообщение, что упрощает понимание и диагностику ошибки.
    - **Логическая структура приложения**: Собственные исключения могут быть созданы для конкретных логических частей приложения. Это позволяет лучше структурировать код и сделать его более понятным и поддерживаемым. Например, можно создать `UserNotFoundException` для ошибок, связанных с пользователями, или `OrderProcessingException` для ошибок при обработке заказов.
    - **Улучшенная обработка ошибок**: Использование собственных исключений позволяет более гибко обрабатывать ошибки. Можно создавать иерархию исключений и обрабатывать их на разных уровнях приложения в зависимости от типа и специфики ошибки.
    - **Логирование и отладка**: Собственные исключения могут содержать дополнительную информацию, полезную для логирования и отладки. Например, можно передать в исключение данные о состоянии объекта или контексте, в котором произошла ошибка.
    - **Обеспечение инкапсуляции**: Создание собственных исключений помогает скрыть внутренние детали реализации от

```java
class CustomException extends Exception {
    public CustomException(String message) {
        super(message);
    }
}
```

**try**

[Исключения в Java, Часть I (try-catch-finally)](https://habr.com/ru/company/golovachcourses/blog/223821/)

**try with resources**

В качестве ресурса можно использовать любой объект, класс которого реализует интерфейс **java.lang.AutoCloseable** или **java.io.Closable**.

[Курс Java Syntax Pro - Лекция: Оператор try with resources](https://javarush.ru/quests/lectures/questsyntaxpro.level15.lecture00)

best practices

[9 Best Practices to Handle Java Exceptions - Stackify](https://stackify.com/best-practices-exceptions-java/)

call from spring

```java

//init
@ResponseStatus(value = CONFLICT)
public class FeedbackRatingAlreadyExistsException extends RuntimeException {

    public FeedbackRatingAlreadyExistsException(String message) {
        super(message);
    }

    public static FeedbackRatingAlreadyExistsException ratingWithSuchIdAlreadyExists(String id) {
        return new FeedbackRatingAlreadyExistsException(format("Feedback rating with id = %s already exists", id));
    }
}

//call
ratingWithSuchIdAlreadyExists(id)
```