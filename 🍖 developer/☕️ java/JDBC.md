[[🌻 ORM]]

MyBatis

Hibernate

[Hibernate and Java Persistence API (JPA) Fundamentals](https://www.oreilly.com/library/view/hibernate-and-java/9781771373494/)

[https://github.com/97rajeev/All/blob/master/Java Persistence with Hibernate%2C 2nd Edition by rajeev.pdf](https://github.com/97rajeev/All/blob/master/Java%20Persistence%20with%20Hibernate%2C%202nd%20Edition%20by%20rajeev.pdf)

асоциации

[Hibernate ORM 5.0 User Guide](https://docs.jboss.org/hibernate/orm/5.0/userguide/html_single/Hibernate_User_Guide.html#associations-many-to-one)

пагинация

[Hibernate Pagination | Baeldung](https://www.baeldung.com/hibernate-pagination)

пагинация количество строк с отбором

страница 464 java Persistens API

[Hibernate cache](Hibernate%20cache%2006bc9c2014c440e0a85e03c497aad48e.md)

[Spring JPA](Spring%20JPA%201163ccffce7145a2b94415ac52b56fd2.md)

**24.15. Автоматическая генерация схемы**

```jsx
spring.jpa.hibernate.ddl-auto
hibernate.hbm2ddl.auto

create, create-drop, validate, update
```

[Hibernate ORM 5.4.30.Final User Guide](https://docs.jboss.org/hibernate/orm/5.4/userguide/html_single/Hibernate_User_Guide.html#configurations-hbmddl)

[migrations](migrations%20a0e04c39c7c442a5a3cd7525eb3d9e1a.md)


# Основные аннотации в ORM (на примере JPA/Hibernate):

1. **`@Entity`**:
    
    - Указывает, что класс представляет собой таблицу в базе данных.
    
2. **`@Table`**:
    
    - Указывает имя таблицы в базе данных, к которой привязан этот класс.
    
3. **`@Id`**:
    
    - Помечает поле как первичный ключ.
4. **`@GeneratedValue`**:
    
    - Указывает, как генерировать значение для поля. Например, автоинкремент.
5. **`@OneToMany`, `@ManyToOne`, `@OneToOne`, `@ManyToMany`**:
    
    - Эти аннотации используются для описания отношений между сущностями в базе данных.


# **Session**

### Как работает `Session` в Hibernate?

1. **Создание сессии**:
    
    - `Session` создаётся через **`SessionFactory`**, которая инициализируется один раз для каждого приложения и используется для создания сессий. Каждая сессия — это краткосрочное соединение с базой данных.
2. **Операции с объектами**:
    
    - С помощью сессии выполняются операции над объектами (сохранение, получение, обновление, удаление и т.д.).
    - Сессия поддерживает кэширование первого уровня, что значит, что изменения объектов автоматически отслеживаются и синхронизируются с базой данных в конце транзакции.
3. **Закрытие сессии**:
    
    - После завершения работы с сессией её необходимо закрыть, чтобы освободить ресурсы.

### Пример использования `Session` в Hibernate:

java

Копировать код

`import org.hibernate.Session; import org.hibernate.Transaction;  public class HibernateExample {      public static void main(String[] args) {         // Получаем фабрику сессий из утилитарного класса         SessionFactory sessionFactory = HibernateUtil.getSessionFactory();          // Открываем новую сессию         Session session = sessionFactory.openSession();          // Начинаем транзакцию         Transaction transaction = session.beginTransaction();          // Создаём новый объект (сущность)         User user = new User();         user.setUsername("john_doe");         user.setEmail("john.doe@example.com");          // Сохраняем объект в базе данных         session.save(user);          // Подтверждаем транзакцию         transaction.commit();          // Закрываем сессию         session.close();     } }`

### Основные методы интерфейса `Session`:

1. **`save()`**:
    
    - Сохраняет новый объект в базе данных и возвращает идентификатор, присвоенный объекту.
    
    `session.save(user);`
    
2. **`get()`** и **`load()`**:
    
    - Эти методы используются для получения объекта из базы данных по его идентификатору.
    - **`get()`** немедленно выполняет запрос к базе данных и возвращает объект или `null`, если объект не найден.
    - **`load()`** возвращает прокси-объект (ленивую загрузку), и реальный запрос будет выполнен только при попытке получить доступ к данным объекта.
    
    `User user = session.get(User.class, 1); // Немедленный запрос User userProxy = session.load(User.class, 1); // Прокси-объект, запрос отложен`
    
3. **`update()`**:
    
    - Обновляет существующий объект в базе данных. Этот метод используется для обновления отсоединённых объектов (то есть тех, которые больше не связаны с текущей сессией).
    
    `session.update(user);`
    
4. **`merge()`**:
    
    - Похож на `update()`, но более гибкий. Если объект уже находится в текущей сессии, `merge()` объединяет данные сессии с данными отсоединённого объекта, иначе создаёт новый объект.
    
    `session.merge(user);`
    
5. **`delete()`**:
    
    - Удаляет объект из базы данных.
    
    `session.delete(user);`
    
6. **`createQuery()`**:
    
    - Создаёт запрос для выполнения произвольных операций на языке **HQL (Hibernate Query Language)** или **JPQL (Java Persistence Query Language)**.
    
    java
    
    Копировать код
    
    `List<User> users = session.createQuery("FROM User", User.class).list();`
    
7. **`beginTransaction()`** и **`getTransaction()`**:
    
    - Эти методы используются для начала и управления транзакциями. Обычно, после начала транзакции, ты выполняешь несколько операций и затем подтверждаешь транзакцию с помощью `commit()`.
    
    java
    
    Копировать код
    
    `Transaction transaction = session.beginTransaction(); session.save(user); transaction.commit();`
    

### Кэширование в `Session` (Кэш первого уровня):

- **Первичный кэш**: Каждый объект, который загружается или сохраняется в сессии, кэшируется в рамках этой сессии. Это значит, что если в течение одной сессии объект был получен из базы данных, при повторном доступе к нему Hibernate не будет обращаться к базе, а вернёт объект из кэша.
- **Особенности**:
    - Кэш первого уровня привязан к конкретной сессии. Как только сессия закрывается, кэш первого уровня уничтожается.
    - Это помогает уменьшить количество обращений к базе данных и повысить производительность.

### Жизненный цикл объекта и сессии в Hibernate:

1. **Transient (Транзиентное состояние)**:
    
    - Объект создаётся в Java, но ещё не связан с сессией и не существует в базе данных.
    
    `User user = new User(); // Объект находится в транзиентном состоянии`
    
2. **Persistent (Персистентное состояние)**:
    
    - Объект сохранён в базе данных или загружен из неё. Он связан с сессией и любые изменения объекта автоматически синхронизируются с базой данных при закрытии транзакции.
    
    `session.save(user); // Объект становится персистентным`
    
3. **Detached (Отсоединённое состояние)**:
    
    - После закрытия сессии объект больше не связан с сессией, но его можно обновить или удалить с помощью новой сессии.
    
    `session.close(); // Объект становится отсоединённым`
    
4. **Removed (Удалённое состояние)**:
    
    - Объект помечен для удаления, и будет удалён из базы данных после вызова `delete()`.
    
    `session.delete(user); // Объект будет удалён из базы данных`
    

### Пример с транзакциями и сессиями:

`Session session = sessionFactory.openSession(); Transaction transaction = null;  try {     transaction = session.beginTransaction();          User user = new User();     user.setUsername("john_doe");     user.setEmail("john@example.com");          session.save(user); // Сохраняем объект     transaction.commit(); // Подтверждаем транзакцию      } catch (Exception e) {     if (transaction != null) {         transaction.rollback(); // Откатываем изменения в случае ошибки     }     e.printStackTrace(); } finally {     session.close(); // Обязательно закрываем сессию }`
