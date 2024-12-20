# **IoC (Inversion of Control)** — Инверсия управления

**IoC** — это принцип проектирования, согласно которому управление созданием объектов и вызовом методов передается от программиста фреймворку или контейнеру. Это означает, что вместо того, чтобы код самостоятельно создавать зависимости и управлять их жизненным циклом, фреймворк (в нашем случае Spring) берет на себя эту задачу.

#### Пример без IoC:

Допустим, у нас есть класс `Service`, который зависит от объекта класса `Repository`.

java

Копировать код

`public class Service {     private Repository repository;      public Service() {         this.repository = new Repository(); // Объект создается вручную     }      public void performTask() {         repository.doSomething();     } }`

В этом случае, если нам понадобится заменить класс `Repository` на его другую реализацию, нам придется вручную изменить код в классе `Service`.

#### Пример с IoC:

При использовании IoC, создание и управление зависимостями берёт на себя фреймворк:

java

Копировать код

`public class Service {     private Repository repository;      public Service(Repository repository) {  // Зависимость передается извне         this.repository = repository;     }      public void performTask() {         repository.doSomething();     } }`

Теперь класс `Service` не управляет созданием объекта `Repository`, а получает его извне. Таким образом, управление (control) передается фреймворку (контейнеру Spring), который сам решает, как и когда создавать объекты.

# **DI (Dependency Injection)** — Внедрение зависимостей

**Dependency Injection (DI)** — это конкретный механизм реализации IoC, при котором зависимости объекта передаются ему извне, обычно через конструктор, методы или поля. В Spring существует несколько способов внедрения зависимостей:

1. **Внедрение через конструктор** (Constructor-based Injection)
2. **Внедрение через сеттеры** (Setter-based Injection)
3. **Внедрение через поля** (Field-based Injection)

#### Пример внедрения зависимостей через конструктор:

java

Копировать код

`@Component public class Service {     private final Repository repository;      @Autowired  // Spring внедрит зависимость     public Service(Repository repository) {         this.repository = repository;     }      public void performTask() {         repository.doSomething();     } }`

#### Пример внедрения через сеттеры:

java

Копировать код

`@Component public class Service {     private Repository repository;      @Autowired     public void setRepository(Repository repository) {         this.repository = repository;     }      public void performTask() {         repository.doSomething();     } }`

### Основные типы внедрения зависимостей:

- **Внедрение через конструктор** — предпочтительный способ, так как он делает зависимости явными и помогает избежать проблем с неполностью инициализированными объектами.
- **Внедрение через сеттеры** — используется, если зависимости могут быть необязательными или могут изменяться после создания объекта.
- **Внедрение через поля** — менее предпочтительный способ, так как это нарушает инкапсуляцию (поля становятся доступными извне).

# **IoC-контейнер** — Контейнер инверсии управления

**IoC-контейнер** в Spring — это сердце фреймворка. Он управляет созданием, инициализацией, настройкой и уничтожением объектов (бинов). Это контейнер, который реализует IoC через внедрение зависимостей.

#### Основные компоненты IoC-контейнера:

1. **Контейнер создает объекты (бины).**
    - Контейнер управляет всеми компонентами приложения (которые называются "бины").
2. **Контейнер внедряет зависимости.**
    - Контейнер автоматически внедряет зависимости между объектами, что позволяет создавать модульные и легко расширяемые приложения.
3. **Контейнер управляет жизненным циклом бинов.**
    - Он создает объекты, конфигурирует их и уничтожает, когда они больше не нужны.

#### Два типа IoC-контейнеров в Spring:

1. **`BeanFactory`** — базовый контейнер, который предоставляет базовую функциональность управления зависимостями. Обычно не используется напрямую в современных приложениях, так как он предоставляет ограниченные возможности.
2. **`ApplicationContext`** — более мощный контейнер, который расширяет возможности `BeanFactory`. Он добавляет поддержку таких возможностей, как события приложения, возможность работы с аннотациями, и поддержку транзакций.

#### Пример использования IoC-контейнера:

`import org.springframework.context.ApplicationContext; import org.springframework.context.annotation.AnnotationConfigApplicationContext;  public class Main {     public static void main(String[] args) {         // Создаем IoC-контейнер         ApplicationContext context = new AnnotationConfigApplicationContext(AppConfig.class);          // Получаем бин из контейнера         Service service = context.getBean(Service.class);                  // Вызываем метод у бина         service.performTask();     } }`

В этом примере `ApplicationContext` — это IoC-контейнер, который создаёт объекты, внедряет зависимости и управляет жизненным циклом бинов. Конфигурация приложения может быть выполнена с помощью аннотаций или XML.

### Конфигурация IoC-контейнера

Конфигурация IoC-контейнера может быть выполнена двумя основными способами:

1. **Аннотации** (`@Component`, `@Service`, `@Repository`, `@Controller`, `@Configuration`, `@Autowired`):
    
    - Spring автоматически находит и регистрирует компоненты в IoC-контейнере с помощью аннотаций.
2. **Java-конфигурация** (с помощью классов с аннотацией `@Configuration` и методами с `@Bean`):
    
    - Это более гибкий и современный способ конфигурации Spring-приложений.

#### Пример Java-конфигурации:

`import org.springframework.context.annotation.Bean; import org.springframework.context.annotation.Configuration;  @Configuration public class AppConfig {      @Bean     public Repository repository() {         return new Repository();     }      @Bean     public Service service() {         return new Service(repository());     } }`

# **Spring Professional Certification**

[Опыт сдачи Spring Professional Certification 5](https://habr.com/ru/post/490812/)

[Increase your mastery of Spring with official training and certification](https://spring.io/training)

[spring boot 2.0.X](spring%20boot%202%200%20X%205b8e94d686024fbdae38de11b750d38a.md)

[Реактивное программирование](Реактивное%20программирование%200f26ae617e6a4e3c9b4695cffb77c497.md)

[DATA JPA](DATA%20JPA%206cf51ac09ab547b08f7ad8ac6cdc838e.md)

[Spring Security](Spring%20Security%203d5f8af524604844bea482ffb79603b3.md)

[session id](session%20id%200098f875e21844f8b39df00deb23a241.md)

[inject beans](inject%20beans%20097a658b807b47d0a4a111969658ecff.md)

[🦺 testing (fn)](🦺%20testing%20(fn).md)

[WebFlux](WebFlux%20cd65d629e4474a7a9b7619b3c2e049c3.md)

[@Scheduled](@Scheduled.md)

[cache](cache%206fb72df92f2741bd9e56cde3440efd1a.md)

[Spring Events](Spring%20Events%20614f13a60d1e476ead7497ac4bdf8ba2.md)

[*Interceptor*](Interceptor%20ee19aaedd40b4b85b1420268626bb224.md)

[**RestTemplate**](RestTemplate%207c4dd7181ce34949a3adaf73ff39e31e.md)

## Микросервисы со Spring Boot

[Микросервисы со Spring Boot. Часть 1. Начало работы](https://habr.com/ru/post/484130/)

[Учимся разворачивать микросервисы. Часть 1. Spring Boot и Docker](https://habr.com/ru/post/487922/)

[WebClient](WebClient%20a534f51948e440d7b8919d5d7161029d.md)

**настроить переменную среду**

[https://fooobar.com/questions/128128/using-env-variable-in-spring-boots-applicationproperties](https://fooobar.com/questions/128128/using-env-variable-in-spring-boots-applicationproperties)

## прочитать про внешнее окружение

[Spring Boot Features](https://docs.spring.io/spring-boot/docs/current/reference/html/spring-boot-features.html#boot-features-external-config)

# spring Security

[Spring Security Reference](https://docs.spring.io/spring-security/site/docs/current/reference/html5/)

### анотация @Secured

[Introduction to Spring Method Security | Baeldung](https://www.baeldung.com/spring-security-method-security)

[5. Java Configuration](https://docs.spring.io/spring-security/site/docs/4.1.x/reference/html/jc.html)

### @Qualifier

[Spring @Qualifier Annotation](https://www.baeldung.com/spring-qualifier-annotation)

## Logger

[Logging in Spring Boot | Baeldung](https://www.baeldung.com/spring-boot-logging)

Обработка исключений в контроллерах Spring

[Обработка исключений в контроллерах Spring](https://habr.com/ru/post/528116/)

**Redirects**

[A Guide To Spring Redirects | Baeldung](https://www.baeldung.com/spring-redirect-and-forward)

[Подготовка к Spring Professional Certification. Контейнер, IoC, бины](https://habr.com/ru/post/470305/)

**@Valid and @Validated**

[](https://www.baeldung.com/spring-valid-vs-validated)

[Validation with Spring Boot - the Complete Guide](https://reflectoring.io/bean-validation-with-spring-boot/)

```xml
<dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-validation</artifactId>
        </dependency>
```

[](https://www.baeldung.com/spring-validation-message-interpolation)

[](https://www.baeldung.com/javax-validation)

**in service (@Validated and @Valid)**

```java

@Service
@Validated
class ValidatingService{
    void validateInput(@Valid Input input){
      // do something
    }
}
```

[Validation with Spring Boot - the Complete Guide](https://reflectoring.io/bean-validation-with-spring-boot/)

**@Slf4j**

[](https://www.baeldung.com/slf4j-with-log4j2-logback)

[**WebSocket**](WebSocket%203bcafaba0de2414a8dc6f4f26960ea53.md)

[**`resources` in Jar**](resources%20in%20Jar%2054b41f53096e4630a298502c82bfc0c5.md)

[***application.properties***](application%20properties%20aaa2aded36d64837aeb0bbc61924e235.md)

[rest](rest%20a230c2cdbb8b417ba9a8100fbfeaaed3.md)

[spring-boot-angular](spring-boot-angular%202226a9214dd347aca28514a49905dfcc.md)

[Configuration](Configuration%2070e142c34fe948678ba91137565b0f93.md)

**Error Handling**

[Error Handling for REST with Spring | Baeldung](https://www.baeldung.com/exception-handling-for-rest-with-spring)

[**@Order**](@Order%20820512de08a3445aaa81e5f2299c8e13.md)

**OncePerRequestFilter**

[What Is OncePerRequestFilter? | Baeldung](https://www.baeldung.com/spring-onceperrequestfilter)

beenCreate

The [@ConditionalOnBean](https://docs.spring.io/spring-boot/docs/current/api/org/springframework/boot/autoconfigure/condition/ConditionalOnBean.html) annotation let a bean be loaded based on the presence of specific bean inside Spring container.

Actuator’s endpoints

[Production-ready Features](https://docs.spring.io/spring-boot/docs/current/reference/html/actuator.html)