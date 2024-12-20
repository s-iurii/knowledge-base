

[Понимание брокеров сообщений. Изучение механики обмена сообщениями посредством ActiveMQ и Kafka. Глава 1](https://habr.com/ru/post/466385/)

[WebSphere MQ для начинающих](https://habr.com/ru/post/176209/)

# RabbitMQ

[RabbitMQ Spring tutorial](https://habr.com/ru/post/262069/)

[Messaging with RabbitMQ](https://spring.io/guides/gs/messaging-rabbitmq/)

[RabbitMQ против Kafka: отказоустойчивость и высокая доступность в кластерах](https://habr.com/ru/company/itsumma/blog/471858/)

практика

[RabbitMQ Spring tutorial](https://habr.com/ru/post/262069/)

[Messaging with RabbitMQ](https://spring.io/guides/gs/messaging-rabbitmq/)


# Kafka

### Понимание брокеров сообщений. Изучение механики обмена сообщениями посредством ActiveMQ и Kafka. Глава 3. Kafka
https://habr.com/ru/articles/466585/

[kafka](kafka%207fbc7c42e2c84748b35570f1b8a57618.md)
[spring-kafka](https://www.baeldung.com/spring-kafka)
### тебования к Kafka:

- Быть чрезвычайно быстрой
- Предоставлять большую пропускную способность при работе с сообщениями
- Поддерживать модели «Издатель-Подписчик» и «Точка-Точка»
- Не замедляться с добавлением потребителей. Например, производительность и очереди, и топика в ActiveMQ ухудшается при росте количества потребителей на адресате
- Быть горизонтально масштабируемой; если один брокер, сохраняющий (persists) сообщения, может делать это только на максимальной скорости диска, то для увеличения производительности имеет смысл выйти за пределы одного экземпляра брокера
- Разграничивать доступ к хранению и повторному извлечению сообщений



```jsx
@KafkaListener(
            id = "examinator.topic.attendances",
            containerFactory = "examinatorKafkaListenerContainerFactory",
            topics = "${hit.messaging.consumer.examinator.topic.attendances}",
            containerGroup = "${hit.messaging.consumer.examinator.group}",
            groupId = "${hit.messaging.consumer.examinator.group}"
    )
    @RunAsSystemUser
    @RequireDbConnection(fetchStrategy = OrientRepository.FETCH_PLAN_ALL)
    public void consumeAttendances(
            @Payload Attendances attendances,
            @Header(KafkaHeaders.RECEIVED_TOPIC) String topic,
            @Header(KafkaHeaders.RECEIVED_MESSAGE_KEY) String key,
            @Header(KafkaHeaders.OFFSET) String offset
    ) {
        LogHelper.trace(log, RECEIVED_TOPIC_LOG, topic, offset, key, attendances);
        Optional.ofNullable(attendances).ifPresent(examinatorService::sync);
        LogHelper.debug(log, PROCESSED_TOPIC_LOG, topic, offset, key);
    }
```

**Avro serialization в Kafka**