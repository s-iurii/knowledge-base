BASE — это концепция, противопоставляющаяся ACID и применяемая для распределенных систем, особенно для **NoSQL** баз данных. Если ACID нацелен на строгие гарантии целостности данных в реляционных базах данных, то BASE предлагает более гибкий подход, который позволяет системам быть более масштабируемыми и устойчивыми к сбоям.

### BASE расшифровывается как:

1. **Basically Available** (Базовая доступность)
2. **Soft state** (Непостоянное состояние)
3. **Eventual consistency** (Окончательная согласованность)

### Разберем эти термины подробнее:

### 1. **Basically Available (Базовая доступность)**

Это означает, что система всегда будет доступна для обработки запросов, даже если она не может гарантировать, что данные будут на 100% актуальны или целостны в момент обработки. Это противоположно концепции доступности в ACID, где система может стать недоступной, если требуется поддерживать строгую консистентность данных.

**Пример**: В распределенной системе может быть временно доступен узел с устаревшими данными, но система не перестанет отвечать на запросы и предоставлять хотя бы частично правильные данные.

### 2. **Soft state (Непостоянное состояние)**

Данные в системе могут быть в непостоянном состоянии, то есть могут изменяться или синхронизироваться со временем, даже без каких-либо внешних изменений. Это связано с тем, что для достижения окончательной согласованности данные могут реплицироваться между узлами системы. В отличие от ACID, где состояние данных фиксируется после транзакции, в BASE данные могут временно находиться в состоянии изменений, пока не синхронизируются.

**Пример**: Когда данные распространяются по узлам распределенной системы, состояние может быть временно разным в разных местах. Например, в одной реплике данных может быть одна версия записи, а в другой — другая, пока данные не синхронизируются.

### 3. **Eventual consistency (Окончательная согласованность)**

Это основной принцип BASE, который означает, что данные не всегда консистентны (согласованы) мгновенно, но система гарантирует, что через некоторое время они станут согласованными. Другими словами, если никаких новых обновлений не происходит, все копии данных в системе в конечном итоге станут одинаковыми.

**Пример**: Предположим, ты обновляешь запись в базе данных, которая реплицируется между несколькими серверами. Эти изменения не сразу отразятся на всех серверах, но через некоторое время (обычно через секунды или минуты) все серверы будут иметь одинаковую версию данных.

### Основные различия между ACID и BASE:

|Свойство|ACID|BASE|
|---|---|---|
|**Atomicity (Атомарность)**|Транзакция либо выполняется, либо откатывается|Гарантий нет, транзакции могут быть неполными|
|**Consistency (Консистентность)**|Данные всегда в согласованном состоянии|Консистентность в конечном итоге достигается|
|**Isolation (Изоляция)**|Транзакции изолированы друг от друга|Могут быть видны промежуточные состояния данных|
|**Durability (Надежность)**|После завершения транзакции данные сохраняются|Надежность меньше важна, данные могут быть временно недоступны|
|**Basically Available**|Система может стать недоступной для поддержания консистентности|Система всегда доступна, даже если данные не актуальны|
|**Soft State**|Состояние данных фиксировано и неизменно|Данные могут быть в процессе изменений|
|**Eventual Consistency**|Консистентность достигается немедленно после транзакции|Консистентность достигается со временем|

### Когда используют BASE?

BASE-подход часто используется в **NoSQL** базах данных и распределенных системах, где приоритетом является масштабируемость и доступность, а не мгновенная консистентность данных. Примеры таких систем включают **Cassandra**, **MongoDB**, **Amazon DynamoDB**, где часто жертвуют строгой консистентностью в пользу более высокой доступности и производительности.

### Пример системы с BASE:

Представь распределенную базу данных для крупного интернет-магазина. Когда пользователь делает заказ, система может немедленно подтвердить заказ и продолжить обработку. Однако информация о новом заказе может распространяться по различным узлам базы данных с задержкой, и может быть ситуация, когда разные серверы в сети видят разные данные о заказе. Через некоторое время все узлы системы будут синхронизированы, и данные о заказе станут согласованными на всех серверах.