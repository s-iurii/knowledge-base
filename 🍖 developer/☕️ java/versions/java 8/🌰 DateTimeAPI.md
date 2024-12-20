
[[🏆 Java8]]

https://www.geeksforgeeks.org/new-date-time-api-java8/

New date-time API is introduced in Java 8 to overcome the following drawbacks of old date-time API : 

1. **Not thread safe :** Unlike old java.util.Date which is not thread safe the new date-time API is _immutable_ and doesn’t have setter methods.
2. **Less operations :** In old API there are only few date operations but the new API provides us with many date operations.

Java 8 under the package java.time introduced a new date-time API, most important classes among them are :  

1. **Local :** Simplified date-time API with no complexity of timezone handling.
2. **Zoned :** Specialized date-time API to deal with various timezones.

- **LocalDate/LocalTime** and **LocalDateTime API :** Use it when time zones are NOT required
