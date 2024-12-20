
[Обзор модульного и интеграционного тестирования Spring Boot](https://habr.com/ru/post/561520/)

[](https://www.baeldung.com/spring-boot-testing)

# **jUnit**

[JUnit 5 User Guide](https://junit.org/junit5/docs/current/user-guide/)

[Guide to Testing With the Spring Boot Starter Test | rieckpil](https://rieckpil.de/guide-to-testing-with-spring-boot-starter-test/)

```java
import static org.junit.jupiter.api.Assertions.*;
 
assertNotNull(result);
assertNotEquals("John", "Duke");
assertThrows(NumberFormatException.class, () -> Integer.valueOf("duke"));
assertEquals("Hello World", sampleService.getData());
```

[Spring на практике - Spring Boot и тестирование](https://www.youtube.com/watch?v=UjGTCCkKnvs)

```java
//junit 5
@Test
public void whenExceptionThrown_thenAssertionSucceeds() {
    Exception exception = assertThrows(NumberFormatException.class, () -> {
        Integer.parseInt("1a");
    });

    String expectedMessage = "For input string";
    String actualMessage = exception.getMessage();

    assertTrue(actualMessage.contains(expectedMessage));
}
```

```java
//junit 4
//exempl 1
@Test(expected = NullPointerException.class)
public void whenExceptionThrown_thenExpectationSatisfied() {
    String test = null;
    test.length();
}

//exempl 2
@Rule
public ExpectedException exceptionRule = ExpectedException.none();

@Test
public void whenExceptionThrown_thenRuleIsApplied() {
    exceptionRule.expect(NumberFormatException.class);
    exceptionRule.expectMessage("For input string");
    Integer.parseInt("1a");
}
```

[](https://www.baeldung.com/junit-assert-exception)

**@RunWith()**

Если вы используете Junit версии <5, вы должны использовать `@RunWith(SpringRunner.class)`или `@RunWith(MockitoJUnitRunner.class)`т. Д.

```
@Before
public void setUp() {
    MockitoAnnotations.initMocks(this);
}
```

Если вы используете Junit version = 5, вам нужно использовать `@ExtendWith(SpringExtension.class)`или `@ExtendWith(MockitoExtension.class)`и т. Д.

`@RunWith(PowerMockRunner.class)?`

[https://stackoverflow.com/questions/55276555/when-to-use-runwith-and-when-extendwith](https://stackoverflow.com/questions/55276555/when-to-use-runwith-and-when-extendwith)

**@WebMvcTest**

[Spring Boot Test Slices: Overview and Usage | rieckpil](https://rieckpil.de/spring-boot-test-slices-overview-and-usage/)

[Spring Boot + JUnit 5 + Mockito - Mkyong.com](https://mkyong.com/spring-boot/spring-boot-junit-5-mockito/)

# **Интеграционные тесты**

**MockMvcResultMatchers**

```java
mockMvc.perform(post("/api/candidate/interviews/{ticket}/decline_reasons", "ticket")
                .contentType(MediaType.APPLICATION_JSON)
                .content(JsonUtils.beanToJson(CandidateInterviewDeclineReasonDto.builder()
                        .reasonId("1")
                        .comment(lineSize226)
                        .build()))
                .with(user(CredentialUtils.createUser(testUserPrincipal, HitUserRole.CANDIDATE))))
                .andDo(print())
                .andExpect(status().isBadRequest());
```

[](https://www.baeldung.com/integration-testing-in-spring)

[](https://www.baeldung.com/spring-mock-rest-template)

[Testing the Spring RestTemplate With @RestClientTest | rieckpil](https://rieckpil.de/testing-your-spring-resttemplate-with-restclienttest/)

# **mockito**

[](https://www.baeldung.com/tag/mockito/)

[](https://www.baeldung.com/mockito-annotations)

[](https://www.baeldung.com/mockito-behavior)

заглушка одного и того же метода несколько раз с использованием API :

**'given (). will ()'** или **'when (). then ()**'

```java
when(foo.doSomething()).thenReturn(somethingElse);

given(foo.doSomething()).willReturn(somethingElse);
```

Пожалуйста, используйте API:

 '**will (). Given ()**' или **'doReturn (). When ()**' для создания заглушек.

verify(mock).someMethod();
verify(mock, times(10)).someMethod();
verify(mock, atLeastOnce()).someMethod();

verify(mock, never()).someMethod();
not: verify(mock.someMethod());

```java
@RunWith(MockitoJUnitRunner.class)
public class Test_Mockito
{
    @Mock 
    ICalculator mcalc;

    // используем аанотацию @InjectMocks для создания mock объекта
    @InjectMocks 
    Calculator calc = new Calculator(mcalc);

    @Test
    public void testCalcAdd() 
    {
        // определяем поведение калькулятора для операции сложения
        when(calc.add(10.0, 20.0)).thenReturn(30.0);

        // проверяем действие сложения
        assertEquals(calc.add(10, 20), 30.0, 0);
        // проверяем выполнение действия
        verify(mcalc).add(10.0, 20.0);

        // определение поведения с использованием doReturn 
        doReturn(15.0).when(mcalc).add(10.0, 5.0);

        // проверяем действие сложения
        assertEquals(calc.add(10.0, 5.0), 15.0, 0);
        verify(mcalc).add(10.0, 5.0);
    }
}
```

[JUnit и фреймворк Mockito](http://java-online.ru/junit-mockito.xhtml)

# **@Spy** 

[](https://www.baeldung.com/mockito-spy)

`@Spy` [док](http://static.javadoc.io/org.mockito/mockito-core/2.24.0/org/mockito/Spy.html) говорит:

> Поле, аннотированное @Spy, может быть инициализировано явно в точке объявления. В качестве альтернативы, если вы не предоставите экземпляр, Mockito попытается найти конструктор без аргументов (даже закрытый) и создаст для вас экземпляр.
# **@SpyBean**

https://www.baeldung.com/spring-spy-vs-spybean

`@SpyBean` [док](https://docs.spring.io/spring-boot/docs/current/api/org/springframework/boot/test/mock/mockito/SpyBean.html) говорит:

> Аннотация, которую можно использовать для применения шпионов Mockito к Spring ApplicationContext.
> 
> Все бины в контексте одного и того же типа будут обернуты шпионом. Если существующий бин не определен, будет добавлен новый.

Итак, главное отличие в том, что `@SpyBean`это специфичная для Spring Boot аннотация `@Spy`, но она является частью самого Mockito `@SpyBean`и `@Spy`по сути делает то же самое, но `@SpyBean`может разрешать специфичные для Spring зависимости, например `@Autowired`, `@Spy`может создавать объекты только с пустым конструктором.




# **Parameterized**

```java
@RunWith(Parameterized.class)
 public class AdditionTest {
     @Parameters(name = "{index}: {0} + {1} = {2}")
     public static Iterable<Object[]> data() {
         return Arrays.asList(new Object[][] { { 0, 0, 0 }, { 1, 1, 2 },
                 { 3, 2, 5 }, { 4, 3, 7 } });
     }

     private int firstSummand;

     private int secondSummand;

     private int sum;

     public AdditionTest(int firstSummand, int secondSummand, int sum) {
         this.firstSummand = firstSummand;
         this.secondSummand = secondSummand;
         this.sum = sum;
     }

     @Test
     public void test() {
         assertEquals(sum, firstSummand + secondSummand);
     }
 }
```

[Parameterized (JUnit API)](https://junit.org/junit4/javadoc/latest/org/junit/runners/Parameterized.html)

[Using SpringJUnit4ClassRunner with Parameterized | Baeldung](https://www.baeldung.com/springjunit4classrunner-parameterized)

```java
@RunWith(JUnitParamsRunner.class)
public class UserSettingsServiceImplTest {

@Test
    @Parameters({
            "A1, A, 1",
            "A5, B, 1",
            "A1, C, 1",
            "A1, A, 6"
    })
    public void testUpdateConfirmedCandidateLevels_SuccessCall(String candidateLevel,
                                                               String userTrack,
                                                               String userLevel)

@Parameters({
    "auto:20|c_fill\\,w_auto:20",
    "auto:20:350|c_fill\\,w_auto:20:350",
   })
@TestCaseName("Width {0}: {1}")
@Test
public void testShouldSupportAutoWidth(String width, String result) {
  String trans;
  trans = new Transformation().width(width).crop("fill").generate();
  assertEquals(result, trans);
}
```

[](https://www.baeldung.com/junit-params)

[void method throws an exception](https://stackoverflow.com/questions/15156857/mockito-test-a-void-method-throws-an-exception)

```java
Mockito.doThrow(new AccessDeniedException("AccessDeniedException")).when(interviewServiceMock).finish("ticket");
```

# Matchers

```jsx
Assert.assertThat(template.getErrorHandler(), Matchers.instanceOf(CommonResponseErrorHandler.class));
        Assert.assertThat(template.getInterceptors(), Matchers.hasItem(Matchers.instanceOf(ClientLoggingInterceptor.class)));
```

[Employee employee = new Employee();

ReflectionTestUtils.setField(employee, "id", 1);
ReflectionTestUtils.invokeMethod(employee, "employeeToString");](../Reflection%2076bf7177d4b4419ba215d483fc421b94.md) 

**Static Methods With Mockito**

[Mocking Static Methods With Mockito | Baeldung](https://www.baeldung.com/mockito-mock-static-methods)

```jsx
@Test
void givenStaticMethodWithArgs_whenMocked_thenReturnsMockSuccessfully() {
    assertThat(StaticUtils.range(2, 6)).containsExactly(2, 3, 4, 5);

    try (MockedStatic<StaticUtils> utilities = Mockito.mockStatic(StaticUtils.class)) {
        utilities.when(() -> StaticUtils.range(2, 6))
          .thenReturn(Arrays.asList(10, 11, 12));

        assertThat(StaticUtils.range(2, 6)).containsExactly(10, 11, 12);
    }

    assertThat(StaticUtils.range(2, 6)).containsExactly(2, 3, 4, 5);
}
```

```jsx
<dependency>
    <groupId>org.mockito</groupId>
    <artifactId>mockito-inline</artifactId>
    <version>3.8.0</version>
    <scope>test</scope>
</dependency>
```

# **Mockito**

```jsx
@Mock(answer = Answers.RETURNS_DEEP_STUBS)
private PizzaBuilder anotherBuilder;
```

Mockito.RETURNS_DEEP_STUBS

```jsx
@Test
public void givenDeepMocks_whenServiceInvoked_thenPizzaIsBuilt() {
    PizzaBuilder builder = Mockito.mock(Pizza.PizzaBuilder.class, Mockito.RETURNS_DEEP_STUBS);

    Mockito.when(builder.name(anyString())
      .size(any(Pizza.PizzaSize.class))
      .withExtraTopping(anyString())
      .withStuffedCrust(anyBoolean())
      .withExtraTopping(anyString())
      .willCollect(anyBoolean())
      .applyDiscount(anyInt())
      .build())
      .thenReturn(expectedPizza);

    PizzaService service = new PizzaService(builder);
    Pizza pizza = service.orderHouseSpecial();
    assertEquals("Expected Pizza", expectedPizza, pizza);
}
```

[Mockito and Fluent APIs | Baeldung](https://www.baeldung.com/mockito-fluent-apis)

```java
ArgumentCaptor<Consumer> previousRoundArgumentCaptor = ArgumentCaptor.forClass(Consumer.class);
        verify(interviewRepository).save(eq(previousInterview), previousRoundArgumentCaptor.capture());
```