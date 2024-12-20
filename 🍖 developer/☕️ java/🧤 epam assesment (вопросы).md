[[☕️ Java]]
# вопросы ot Epam assesment

## **Java Core concepts, Collections, Reflection, Multithreading Java [Advanced/Expert] -**

**Object, class**

- [x]  Deep understanding of OOP model implementation in Java. Strong knowledge of Object class as the main language entity, knowledge of its methods.
- [x]  Ability to use a design of patterns and SOLID principals.
    
    answer
    
    ### Порождающие шаблоны (Creational Patterns)
    
    1. **Singleton (Одиночка)**:
        - Гарантирует существование только одного экземпляра класса и предоставляет глобальную точку доступа к нему.
    2. **Factory Method (Фабричный метод)**:
        - Определяет интерфейс для создания объекта, но позволяет подклассам изменить тип создаваемого объекта.
    3. **Abstract Factory (Абстрактная фабрика)**:
        - Предоставляет интерфейс для создания семейств взаимосвязанных объектов без указания их конкретных классов.
    4. **Builder (Строитель)**:
        - Отделяет конструирование сложного объекта от его представления, так что один и тот же процесс конструирования может создавать разные представления.
    5. **Prototype (Прототип)**:
        - Создает новые объекты путем копирования существующего объекта-прототипа.
    
    ### Структурные шаблоны (Structural Patterns)
    
    1. **Adapter (Адаптер)**:
        - Преобразует интерфейс класса в другой интерфейс, который ожидают клиенты.
    2. **Bridge (Мост)**:
        - Отделяет абстракцию от её реализации, позволяя изменять их независимо.
    3. **Composite (Компоновщик)**:
        - Составляет объекты в древовидные структуры для представления иерархий часть-целое.
    4. **Decorator (Декоратор)**:
        - Динамически добавляет новые обязанности объекту.
    5. **Facade (Фасад)**:
        - Предоставляет унифицированный интерфейс к набору интерфейсов в подсистеме.
    6. **Flyweight (Приспособленец)**:
        - Позволяет эффективно поддерживать множество мелких объектов за счет разделения общего состояния.
    7. **Proxy (Заместитель)**:
        - Предоставляет суррогат или заменитель другого объекта для контроля доступа к нему.
    
    ### Поведенческие шаблоны (Behavioral Patterns)
    
    1. **Chain of Responsibility (Цепочка обязанностей)**:
        - Передает запрос по цепочке обработчиков, где каждый обработчик решает, обработать запрос или передать следующему.
    2. **Command (Команда)**:
        - Инкапсулирует запрос как объект, позволяя параметризовать клиентами с разными запросами.
    3. **Interpreter (Интерпретатор)**:
        - Определяет грамматику представления языка и интерпретатор, использующий это представление для интерпретации предложений.
    4. **Iterator (Итератор)**:
        - Предоставляет способ последовательного доступа к элементам агрегированного объекта без раскрытия его внутреннего представления.
    5. **Mediator (Посредник)**:
        - Инкапсулирует способ взаимодействия множества объектов, снижая связанность между ними.
    6. **Memento (Хранитель)**:
        - Сохраняет и внешне сохраняет внутреннее состояние объекта для последующего восстановления.
    7. **Observer (Наблюдатель)**:
        - Определяет зависимость "один ко многим" между объектами так, что при изменении состояния одного объекта все зависящие от него объекты уведомляются и обновляются автоматически.
    
    **SOLID**
    
    пять основных принципов объектно-ориентированного программирования и дизайна
    
    - **Single Responsibility Principle (Принцип единственной ответственности)**:
        - Класс должен иметь только одну причину для изменения. Другими словами, класс должен выполнять только одну задачу или отвечать только за один аспект функциональности программы.
    - **Open/Closed Principle (Принцип открытости/закрытости)**:
        - Программные сущности (классы, модули, функции и т.д.) должны быть открыты для расширения, но закрыты для модификации. Это означает, что поведение сущности можно расширить без изменения её исходного кода.
    - **Liskov Substitution Principle (Принцип подстановки Барбары Лисков)**:
        - Объекты в программе должны быть заменяемы экземплярами их подтипов без изменения корректности программы. Если S является подтипом T, то объекты типа T в программе можно заменить объектами типа S без изменения желаемых свойств программы.
    - **Interface Segregation Principle (Принцип разделения интерфейса)**:
        - Клиенты не должны быть вынуждены зависеть от интерфейсов, которые они не используют. Лучше создать несколько специализированных интерфейсов, чем один универсальный, включающий в себя всё.
    - **Dependency Inversion Principle (Принцип инверсии зависимостей)**:
        - Модули верхнего уровня не должны зависеть от модулей нижнего уровня. Оба типа модулей должны зависеть от абстракций. Абстракции не должны зависеть от деталей, детали должны зависеть от абстракций. Это позволяет уменьшить связанность между компонентами системы.
- [x]  Ability to choose and prove a way (a concept) of objects interconnection.
    
    answer
    
    - **Наследование (Inheritance)**:
        - Один класс (дочерний) наследует свойства и методы другого класса (родительского).
        - Позволяет повторно использовать код, расширяя и модифицируя поведение родительского класса.
        - Пример: Класс "Животное" имеет подкласс "Собака", который наследует свойства и методы класса "Животное".
    - **Композиция (Composition)**:
        - Объект одного класса содержит объекты других классов.
        - Это сильная форма связи, при которой объекты включаемого класса не могут существовать отдельно от содержащего объекта.
        - Пример: Класс "Автомобиль" содержит объект класса "Двигатель".
    - **Агрегация (Aggregation)**:
        - Похож на композицию, но с более слабой связью. Объекты включаемого класса могут существовать независимо от содержащего объекта.
        - Пример: Класс "Команда" содержит объекты класса "Игрок", но игроки могут существовать и без команды.
    - **Ассоциация (Association)**:
        - Один объект связан с другим объектом.
        - Это самая общая форма связи между объектами, которая может быть однонаправленной или двунаправленной.
        - Пример: Класс "Учитель" связан с классом "Ученик".
    - **Полиморфизм (Polymorphism)**:
        - Позволяет объектам разного типа быть обработанными единообразным образом.
        - Достигается через наследование и интерфейсы.
        - Пример: Метод "draw()" может быть вызван для объектов класса "Круг", "Квадрат" и "Треугольник", каждый из которых реализует свой способ рисования.

**Exceptions**

- [x]  Knowledge of the reasons for own exceptions creation (instead of ready ones). Ability to use existing exceptions. Ability to create own exceptions if needed, and implement documentation.
- [x]  Best practices of exceptions usage. Ability to use fail-safe and fail-fast concept to exceptions.
    
    [Exception in java](https://www.notion.so/Exception-in-java-43f83f40577b4e499fef68a9c08d5208?pvs=21)
    

**Serialization**

- [ ]  Deep knowledge of Serialization mechanism and differences between Serializable  vs Externalizable. Ability to choose a way to solution of serialisation task.
- [ ]  Knowledge of alternative approaches in objects Serialization. Ability to prove a chosen method of serialization.

**Annotations**

- [ ]  Knowledge of annotations usage for the exact problems solving. Ability to analyse code in order to apply custom annotations.

**Reflection API**

- [ ]  Reflection API knowledge. Ability to get and call a necessary method, non-default constructor.
- [ ]  Balanced approach for Reflection API usage. Ability to prove the Reflection API implementation.
- [ ]  Understand pros & cons and when its use cases.

**Collections**

- [ ]  Knowledge of inner Collections implementation; knowledge of thread safe collections.
- [ ]  Ability to choose efficient implementation for a problem solution.
- [ ]  Ability to implement thread safe collections for a solution of an existing problem.

**Multithreading**

- [ ]  Good understanding of volatile, synchronized, atomicity.
- [ ]  Be aware of deadlocks, livelocks.
- [ ]  Knowledge of concurrency vs parallelism;. relation to CPU cores; performance considerations; green threads, resource starvation.
- [ ]  Understanding of producer - consumer pattern.; usage of concurrent data structures and atomic types.

**Immutability**

- [ ]  Good understanding of the concept.
- [ ]  Be able to create own custom Immutable class.
- [ ]  Understand its benefits and usages.

**Useful links**

[https://jenkov.com/tutorials/java-exception-handling/fail-safe-exception-handling.html](https://jenkov.com/tutorials/java-exception-handling/fail-safe-exception-handling.html)

[https://docs.oracle.com/javase/tutorial/reflect/index.html](https://docs.oracle.com/javase/tutorial/reflect/index.html)

[https://medium.com/edureka/java-reflection-api-d38f3f5513fc](https://medium.com/edureka/java-reflection-api-d38f3f5513fc)

[https://levelup.gitconnected.com/how-to-use-java-collections-safely-in-multi-threaded-environments-83c94be57ab8](https://levelup.gitconnected.com/how-to-use-java-collections-safely-in-multi-threaded-environments-83c94be57ab8)

[https://docs.oracle.com/javase/tutorial/essential/concurrency/index.html](https://docs.oracle.com/javase/tutorial/essential/concurrency/index.html)

[https://www.baeldung.com/cs/deadlock-livelock-starvation](https://www.baeldung.com/cs/deadlock-livelock-starvation)

[https://docs.oracle.com/javase/tutorial/essential/concurrency/immutable.html](https://docs.oracle.com/javase/tutorial/essential/concurrency/immutable.html)

[https://docs.oracle.com/javase/tutorial/jndi/objects/serial.html](https://docs.oracle.com/javase/tutorial/jndi/objects/serial.html)

[https://docs.oracle.com/javase/tutorial/java/annotations/](https://docs.oracle.com/javase/tutorial/java/annotations/)

[https://www.amazon.com/Clean-Architecture-Craftsmans-Software-Structure/dp/0134494164](https://www.amazon.com/Clean-Architecture-Craftsmans-Software-Structure/dp/0134494164)

## **Java Memory Model Java [Advanced/Expert] -**

**Classloading**

Knowledge of classloading order, staging and the main principals (delegation, uniqueness, accessibility).

Knowledge of the main approaches in custom classloaders and related troubles.

Ability to prove a need of a custom classloader.

**Garbage collector**

Knowledge of the main GC, its pros and cons.

Knowledge of Garbage collector (GC) concept, java memory modal, mark-sweep-compact. Base knowledge of JDC tools for data collecting on GC.

Knowledge of the main GC, its pros and cons.

Knowledge of the main reference types and alternative Finalize usage. Ability to choose a necessary GC and analyse capacity.

Knowledge of own GC creation concept. Ability to prove a choice of GC with set criteria  including set of requirements and environment.

**Java Memory Management in general**

Good understanding of its concepts, how memory is organised.

What is heap, stack, how do they organised?

**Useful links**

[https://miro.medium.com/max/700/1*U4AcVNtejtT1Fa3oMozm5w.png](https://miro.medium.com/max/700/1*U4AcVNtejtT1Fa3oMozm5w.png)

[https://www.ibm.com/docs/en/sdk-java-technology/7.1?topic=mm-detailed-description-global-garbage-collection](https://www.ibm.com/docs/en/sdk-java-technology/7.1?topic=mm-detailed-description-global-garbage-collection)

[https://www.ibm.com/docs/en/sdk-java-technology/7.1?topic=mm-overview-memory-management](https://www.ibm.com/docs/en/sdk-java-technology/7.1?topic=mm-overview-memory-management)

[https://www.ibm.com/docs/en/sdk-java-technology/7.1?topic=uc-class-loading](https://www.ibm.com/docs/en/sdk-java-technology/7.1?topic=uc-class-loading)

[https://www.ibm.com/docs/en/sdk-java-technology/7.1?topic=uc-jit-compiler](https://www.ibm.com/docs/en/sdk-java-technology/7.1?topic=uc-jit-compiler)

[https://medium.com/runtimeerror/java-jit-compiler-c538e5e06a2](https://medium.com/runtimeerror/java-jit-compiler-c538e5e06a2)

[https://www.linkedin.com/learning/java-memory-management?u=2113185](https://www.linkedin.com/learning/java-memory-management?u=2113185)

## **Java [Advanced/Expert] - LTS versions**

**Java 8**

Deep knowledge of key features, Streams API, Lambda, Functional Interface, default method.

Be aware of others features.

**Java 11**

Good knowledge of key features.

It is recommended to understand how to switch from Java 8 to Java 11.

**Java 17**

At least be aware of key features.

**Useful links**

[https://www.oracle.com/java/technologies/java8.html](https://www.oracle.com/java/technologies/java8.html)

[https://docs.oracle.com/en/java/javase/index.html](https://docs.oracle.com/en/java/javase/index.html)

[https://blogs.oracle.com/java/post/upgrading-major-java-versions](https://blogs.oracle.com/java/post/upgrading-major-java-versions)

[https://blogs.oracle.com/java/post/introducing-java-se-11](https://blogs.oracle.com/java/post/introducing-java-se-11)

[https://blogs.ora](https://blogs.oracle.com/java/post/announcing-java17)[cle.com/java/](http://features.java/)post/announcing-java17

## **Architecture. Code Quality. Code review**

**Design principles**

Deep understanding of SOLID, KISS, DRY, YAGNI.

**Design patterns**

GoF. Deep understanding, knowledge of variety, types, use cases.

Patterns used in Spring.

**Monolithic vs Microservices architecture**

Benefits and drawbacks of one or another architecture.

Its use cases.

Cloud native concept. *(Advanced)

12 factor app. *(Advanced)

**Code quality**

Understand what it is and tools to keep it clean. Code style formatter, guides, static code analysers (Sonar)

**Code review**

As the result, you should have come up with your own code review check list.

**Useful links**

[https://blog.cleancoder.com](https://blog.cleancoder.com/)

[https://learn.epam.com/detailsPage?id=746c87bf-5fe7-49f9-b121-863e3851f6bf](https://learn.epam.com/detailsPage?id=746c87bf-5fe7-49f9-b121-863e3851f6bf)

[https://learn.epam.com/detailsPage?id=dfbb41a1-c46c-42c6-abc6-bb632a2abf38](https://learn.epam.com/detailsPage?id=dfbb41a1-c46c-42c6-abc6-bb632a2abf38)

[https://learn.epam.com/detailsPage?id=f1fad1e4-f4a7-4d69-a8e9-956d59b95bbf](https://learn.epam.com/detailsPage?id=f1fad1e4-f4a7-4d69-a8e9-956d59b95bbf)

[https://learn.epam.com/detailsPage?id=4d29a9a3-c9ed-4016-91a0-bb2b39761698](https://learn.epam.com/detailsPage?id=746c87bf-5fe7-49f9-b121-863e3851f6bfhttps://learn.epam.com/detailsPage?id=dfbb41a1-c46c-42c6-abc6-bb632a2abf38https://learn.epam.com/detailsPage?id=f1fad1e4-f4a7-4d69-a8e9-956d59b95bbfhttps://learn.epam.com/detailsPage?id=4d29a9a3-c9ed-4016-91a0-bb2b39761698)

[https://learn.epam.com/detailsPage?id=c4912271-69e1-4506-a646-5bde24c58c71](https://learn.epam.com/detailsPage?id=c4912271-69e1-4506-a646-5bde24c58c71)

[https://www.youtube.com/watch?v=llGgO74uXMI](https://www.youtube.com/watch?v=llGgO74uXMI)

[https://www.linkedin.com/learning/spring-design-patterns?u=2113185](https://www.linkedin.com/learning/spring-design-patterns?u=2113185)

[https://www.linkedin.com/learning/programming-foundations-design-patterns-2?u=2113185](https://www.linkedin.com/learning/programming-foundations-design-patterns-2?u=2113185)

[https://www.linkedin.com/learning/advanced-design-patterns-design-principles?u=2113185](https://www.linkedin.com/learning/advanced-design-patterns-design-principles?u=2113185)

[https://www.linkedin.com/learning/learning-s-o-l-i-d-programming-principles?u=2113185](https://www.linkedin.com/learning/learning-s-o-l-i-d-programming-principles?u=2113185)

[https://learn.epam.com/detailsPage?id=77fa4ed0-9de2-4371-](https://learn.epam.com/detailsPage?id=77fa4ed0-9de2-4371-bc1e-f55bf06ac061)[bc1e-f55bf06](http://yagni.design/)ac061

[https://docs.microsoft.com/en-us/dotnet/architecture/cloud-native/definition](https://docs.microsoft.com/en-us/dotnet/architecture/cloud-native/definition)

[https://12factor.net](https://12factor.net/)

## **Spring [Advanced]**

**Spring Core**

Deep understanding of IoC & DI.

Spring Bean Lifecycle. How to change. Bean scope.

How to inject a bean. What approach is better to choose, why?

**Spring AOP (Optional)**

**Spring vs Spring Boot**

Pros and cons. Differences.

What are usages of Actuators?

**Spring Data (Optional)**

**Spring Security**

Understand how it works and how to secure your application.

**OAuth 2.0, JWT**

Good understanding of the concept.

Differences.

**Useful links**

[https://spring.io/projects/](https://spring.io/projects/)

[https://www.marcobehler.com/guides/spring-security](https://www.marcobehler.com/guides/spring-security)

[https://auth0.com/docs/authenticate/protocols/oauth](https://auth0.com/docs/authenticate/protocols/oauth)

[https://www.marcobehler.com/guides/spring-security-oauth2](https://www.marcobehler.com/guides/spring-security-oauth2)

[https://www.linkedin.com/learning/spring-spring-security-2018?u=2113185](https://www.linkedin.com/learning/spring-spring-security-2018?u=2113185)

## **Databases [Intermediate/Advanced]**

**SQL**

Knowledge of SQL, indexes, performance concerns.

Deep understanding of ACID principles.

**NoSQL**

At least be aware of what it is, for what it can be used.

Knowledge of CAP Theorem.

**Comparison of SQL & NoSQL**

It is highly recommended to understand the difference and when to choose one or another database.

Scalability.

**JDBC, ORM**

Knowledge of how to handle transactions, how they work.

Benefits and drawbacks of JDBC or ORM. Understand what to choose depending on an application.

**Hibernate**

Understand concepts, cache, transactions, N+1 problem.

**Useful links**

[https://www.linkedin.com/learning/sql-tips-and-tricks-for-data-science?u=2113185](https://www.linkedin.com/learning/sql-tips-and-tricks-for-data-science?u=2113185)

[https://www.linkedin.com/learning/advanced-sql-for-query-tuning-and-performance-optimization?u=2113185](https://www.linkedin.com/learning/advanced-sql-for-query-tuning-and-performance-optimization?u=2113185)

[https://database.guide/what-is-normalization/](https://database.guide/what-is-normalization/)

[https://learn.epam.com/detailsPage?id=b6caac6b-afbc-4c0f-9f17-ebc862603cf3](https://learn.epam.com/detailsPage?id=b6caac6b-afbc-4c0f-9f17-ebc862603cf3)

[https://database.guide/what-is-nosql/](https://database.guide/what-is-nosql/)

[https://database.guide/nosql-database-types/](https://database.guide/nosql-database-types/)

[https://www.mantralabsglobal.com/blog/sql-query-optimization-tips/](https://www.mantralabsglobal.com/blog/sql-query-optimization-tips/)

[https://www.sqlshack.com/query-optimization-techniques-in-sql-server-tips-and-tricks/](https://www.sqlshack.com/query-optimization-techniques-in-sql-server-tips-and-tricks/)

[https://hibernate.org/orm/documentation/6.1/](https://hibernate.org/orm/documentation/6.1/)

[https://www.lucidchart.com/blog/what-does-scalability-mean-for-systems-and-services](https://www.lucidchart.com/blog/what-does-scalability-mean-for-systems-and-services)

## **REST [Intermediate/Advanced]**

**Richardson Maturity Model**

Deep understanding of model, HATEOS, its benefits and drawbacks.

**REST API**

Principles.

**(Optional) REST vs SOAP**

Understand it is completely different things and cannot be compared.

Understand what is SOAP, benefits and use cases.

**Useful links**

[https://martinfowler.com/articles/richardsonMaturityModel.html](https://martinfowler.com/articles/richardsonMaturityModel.html)

[https://ninenines.eu/docs/en/cowboy/2.8/guide/rest_principles/](https://ninenines.eu/docs/en/cowboy/2.8/guide/rest_principles/)

[https://www.ibm.com/cloud/learn/rest-apis](https://www.ibm.com/cloud/learn/rest-apis)

[https://www.redhat.com/en/topics/integration/whats-the-difference-between-soap-rest](https://www.redhat.com/en/topics/integration/whats-the-difference-between-soap-rest)

[https://www.upwork.com/resources/soap-vs-rest-a-look-at-two-different-api-style](https://www.upwork.com/resources/soap-vs-rest-a-look-at-two-different-api-styles)[s](http://drawbacks.rest/)

## **JMS [Novice/Intermediate/Advanced]**

**JMS**

What is JMS?

What is Spring JMS?

Messaging Patterns like "Guaranteed Delivery", "Message Bus", etc depending on experience. *(Advanced)

**ActiveMQ**

Benefits and drawbacks of solution.

Using EIP in the ActiveMQ Broker.  *(Advanced)

**RabbitMQ**

Benefits and drawbacks of solution.

RabbitMQ patterns. *(Advanced)

**Kafka**

Benefits and drawbacks of solution.

Kafka consumer-producer pattern.

**Useful links**

ActiveMQ - [https://activemq.apache.org/](https://activemq.apache.org/)

RabbitMQ - [https://www.rabbitmq.com/](https://www.rabbitmq.com/)

Kafka - [https://kafka.apache.org/](https://kafka.apache.org/)

EPAM Course "Message Oriented MiddleWare: JMS, Active MQ, Rabbit MQ, Kafka" - [https://learn.epam.com/detailsPage?id=8b08bddb-f97f-46c0-83bb-734d375ef6ae](https://learn.epam.com/detailsPage?id=8b08bddb-f97f-46c0-83bb-734d375ef6ae)

[https://learn.epam.com/detailsPage?id=f28babc2-cefd-4fc0-901c-43a0f2079c6d](https://learn.epam.com/detailsPage?id=f28babc2-cefd-4fc0-901c-43a0f2079c6d)

[https://www.oracle.com/technical-resources/articles/java/intro-java-message-service.html](https://www.oracle.com/technical-resources/articles/java/intro-java-message-service.html)

[https://docs.oracle.com/javaee/7/tutorial/jms-concepts002.htm](https://docs.oracle.com/javaee/7/tutorial/jms-concepts002.htm)

[https://docs.spring.io/spring-framework/docs/3.2.x/spring-framework-reference/html/jms.html](https://docs.spring.io/spring-framework/docs/3.2.x/spring-framework-reference/html/jms.html)

[https://docs.oracle.com/javaee/7/tutorial/jms-concepts004.htm](https://docs.oracle.com/javaee/7/tutorial/jms-concepts004.htm)

[https://www.enterpriseintegrationpatterns.com/patterns/messaging/](https://www.enterpriseintegrationpatterns.com/patterns/messaging/)

[https://activemq.apache.org/enterprise-integration-patterns](https://activemq.apache.org/enterprise-integration-patterns)

[https://livebook.manning.com/book/rabbitmq-in-depth/chapter-1/v-13/](https://livebook.manning.com/book/rabbitmq-in-depth/chapter-1/v-13/)

[https://petermelias.medium.com/kafka-consumer-patterns-and-gotchas-1bfc04cd643b](https://petermelias.medium.com/kafka-consumer-patterns-and-gotchas-1bfc04cd643b)

## **Testing [Advanced]**

**Unit testing**

Understand "What is a good unit test."

Testing principles: FIRST, Given-When-Then, 3-A.

**Mock, Spy, Stub**

Understand the difference and its usages.

Knowledge of what can be used to create a mock, e.g. Mockito, JMokit, EasyMock, Powermock, Spock.

**BDD/TDD**

Understand the concepts and its benefits.

**The test pyramid**

Understand the pyramid and types of tests.

**Useful links**

[https://site.mockito.org](https://site.mockito.org/)

[https://jmockit.github.io](https://jmockit.github.io/)

[https://easymock.org](https://easymock.org/)

[https://github.com/powermock/powermock](https://github.com/powermock/powermock)

[https://spockframework.org/spock/docs/1.3/all_in_one.html](https://spockframework.org/spock/docs/1.3/all_in_one.html)

[https://martinfowler.com/articles/practical-test-pyramid.html](https://martinfowler.com/articles/practical-test-pyramid.html)

[https://medium.com/@tasdikrahman/f-i-r-s-t-principles-of-testing-1a497acda8d6](https://medium.com/@tasdikrahman/f-i-r-s-t-principles-of-testing-1a497acda8d6)

[https://martinfowler.com/bliki/GivenWhenThen.html](https://martinfowler.com/bliki/GivenWhenThen.html)

[https://xp123.com/articles/3a-arrange-act-assert/](https://xp123.com/articles/3a-arrange-act-assert/)

## **Infrastructure [Intermediate]**

**CI/CD**

Understand the difference between CI/CD, benefits of having CI/CD.

Understand how CI/CD is organised on your actual project, what can be improved.

How would you introduce a new CI/CD pipeline? What stages will it consist of?

**Git**

Understand git workflow types

**Application Server, Web Server**

Understand what they are, difference.

**Docker, Kubernetes**

Relation between them, purpose and difference.

**Useful links**

[https://about.gitlab.com/topics/ci-cd/](https://about.gitlab.com/topics/ci-cd/)

[https://medium.com/javarevisited/5-different-git-workflows-50f75d8783a](https://medium.com/javarevisited/5-different-git-workflows-50f75d8783a7)

[https://www.educative.io/answers/web-server-vs-application-server](https://www.educative.io/answers/web-server-vs-application-server)

[https://www.infoworld.com/article/2077354/app-server-web-server-what-s-the-difference.html](https://www.infoworld.com/article/2077354/app-server-web-server-what-s-the-difference.html)

[https://www.docker.com](https://www.docker.com/)

[https://kubernetes.io](https://kubernetes.io/)

[https://geekflare.com/docker-vs-kubernetes/](https://geekflare.com/docker-vs-kubernetes/)

## **Cloud concepts [Novice/Intermediate]**

**Fundamentals**

What is cloud? Why is it needed?

SaaS vs IaaS vs PaaS differences.

**Useful links**

[https://learn.epam.com/detailsPage?id=4c6fd73f-2582-46e4-98d9-4a0cabdfc1ec](https://learn.epam.com/detailsPage?id=4c6fd73f-2582-46e4-98d9-4a0cabdfc1ec)

Search filter - [https://learn.epam.com/explore?filter=~(isUserContent~false)&search=cloud&sorting=~(~(field~%27rating~direction~%27desc)](https://learn.epam.com/explore?filter=~(isUserContent~false)&search=cloud&sorting=~(~(field~%27rating~direction~%27desc)))&tab=catalog

[https://kb.epam.com/display/TRI/TR+AWS+Crash-course](https://kb.epam.com/display/TRI/TR+AWS+Crash-course)

[https://www.bmc.com/blogs/saas-vs-paas-vs-iaas-whats-the-difference-and-how-to-choose/](https://www.bmc.com/blogs/saas-vs-paas-vs-iaas-whats-the-difference-and-how-to-choose/)

## **SDLC [Intermediate/Advanced]**

**Methodologies**

Be aware of Scrum, Kanban, Waterfall. Understand pros & cons.

Ability to choose a proper methodology for a given situation and prove your choice.

**Agile**

Manifesto.

Ceremonies.

Roles.

**Estimation**

Be aware of estimation techniques.

Understand estimation measures.

**Useful links**

[https://agilemanifesto.org](https://agilemanifesto.org/)

[https://martinfowler.com/agile.html](https://martinfowler.com/agile.html)

[https://www.linkedin.com/learning/agile-software-development?u=2113185](https://www.linkedin.com/learning/agile-software-development?u=2113185)

[https://www.linkedin.com/learning/comparing-agile-versus-waterfall-project-management?u=2113185](https://www.linkedin.com/learning/comparing-agile-versus-waterfall-project-management?u=2113185)

[https://www.linkedin.com/learning/agile-software-development-pair-and-mob-programming?u=2113185](https://www.linkedin.com/learning/agile-software-development-pair-and-mob-programming?u=2113185)

[https://reqtest.com/agile-blog/agile-estimation-techniques/](https://reqtest.com/agile-blog/agile-estimation-techniques/)

[https://xp123.com/articles/invest-in-good-stories-and-smart-tasks/](https://xp123.com/articles/invest-in-good-stories-and-smart-tasks/)

## **NFR [Novice/Intermediate]**

**OWASP top 10**

Be aware of that list of risks and get good understanding if it and how to cope with such threats.

**Performance**

Knowledge of how to troubleshoot poor performance, what tool to use.

**Security**

Knowledge of how to secure an application, what tool to use.

**Useful links**

[https://owasp.org/www-project-top-ten/](https://owasp.org/www-project-top-ten/)

[https://jmeter.apache.org](https://jmeter.apache.org/)

[https://www.jrebel.com/blog/best-java-performance-testing-tools-and-technologies](https://www.jrebel.com/blog/best-java-performance-testing-tools-and-technologies)