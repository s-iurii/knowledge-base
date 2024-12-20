
https://www.baeldung.com/spring-retry

```java
@Configuration @EnableRetry public class AppConfig { ... }


@Service 
public interface MyService { 
@Retryable 
void retryService(String sql); 
}
```