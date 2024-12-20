Аннотации в Java — это специальные метаданные, которые могут быть добавлены к коду (классам, методам, полям, параметрам и т.д.) для предоставления дополнительной информации. Аннотации не влияют напрямую на выполнение программы, но могут использоваться компилятором или средствами времени выполнения (например, фреймворками) для управления поведением кода.

### Примеры стандартных аннотаций:

1. **`@Override`**
    
    - Используется для указания, что метод переопределяет метод суперкласса.
    - Пример:

        
        `@Override public String toString() {     return "MyClass"; }`
        
2. **`@Deprecated`**
    
    - Помечает элемент как устаревший. Использование устаревшего элемента вызывает предупреждение во время компиляции.
    - Пример:
    
        
        `@Deprecated public void oldMethod() {     System.out.println("This method is deprecated"); }`
        
3. **`@SuppressWarnings`**
    
    - Инструктирует компилятор игнорировать определенные предупреждения.
    - Пример:

        
        `@SuppressWarnings("unchecked") public void myMethod() {     List rawList = new ArrayList(); }`
        
4. **`@FunctionalInterface`**
    
    - Помечает интерфейс как функциональный (с единственным абстрактным методом).
    - Пример:
        `@FunctionalInterface public interface MyFunction {     void execute(); }`
        

### Пользовательские аннотации

Ты можешь создавать свои собственные аннотации. Для этого используется ключевое слово `@interface`.

#### Пример создания пользовательской аннотации:

java

Копировать код

`import java.lang.annotation.ElementType; import java.lang.annotation.Retention; import java.lang.annotation.RetentionPolicy; import java.lang.annotation.Target;  @Target(ElementType.METHOD) // Указывает, где можно использовать аннотацию (на методах в данном случае) @Retention(RetentionPolicy.RUNTIME) // Указывает, когда аннотация доступна (в данном случае во время выполнения) public @interface MyAnnotation {     String value(); }`

В этом примере аннотация `MyAnnotation` имеет один параметр `value`. Мы можем использовать её следующим образом:

`public class MyClass {      @MyAnnotation(value = "Example annotation")     public void myMethod() {         System.out.println("Method with custom annotation");     } }`

### Разбор важных параметров аннотаций:

1. **`@Target`**
    
    - Определяет, где аннотация может быть применена (например, к полям, методам, классам, параметрам).
    - Возможные значения:
        - `ElementType.FIELD` — поле.
        - `ElementType.METHOD` — метод.
        - `ElementType.TYPE` — класс, интерфейс или перечисление.
        - `ElementType.PARAMETER` — параметр метода.
2. **`@Retention`**
    
    - Определяет, когда аннотация будет доступна.
    - Возможные значения:
        - `RetentionPolicy.SOURCE` — аннотация доступна только на этапе компиляции и отбрасывается компилятором.
        - `RetentionPolicy.CLASS` — аннотация сохраняется в байт-коде, но недоступна во время выполнения.
        - `RetentionPolicy.RUNTIME` — аннотация сохраняется в байт-коде и доступна во время выполнения с использованием рефлексии.

### Чтение аннотаций с помощью рефлексии:

Аннотации с политикой `RetentionPolicy.RUNTIME` могут быть прочитаны во время выполнения. Пример использования рефлексии для получения информации об аннотациях:

```java
import java.lang.reflect.Method;  
public class Main {     
public static void main(String[] args) throws Exception {
	Method method = MyClass.class.getMethod("myMethod");
	MyAnnotation annotation = method.getAnnotation(MyAnnotation.class);          
	if (annotation != null) {
	System.out.println("Annotation value: " + annotation.value());         }     
}}
```

Этот код получает аннотацию `MyAnnotation` из метода `myMethod` и выводит её значение.

### Применение аннотаций на практике:

1. **Фреймворки** (например, Spring) активно используют аннотации для настройки поведения программ, например, для создания бинов или настройки транзакций.
2. **JPA/Hibernate** используют аннотации для маппинга классов на таблицы базы данных.
3. **Тестирование** (например, JUnit, TestNG) использует аннотации для маркировки тестовых методов.