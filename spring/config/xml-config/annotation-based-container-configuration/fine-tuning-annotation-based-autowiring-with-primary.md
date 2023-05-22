# Fine-tuning Annotation-based Autowiring with @Primary

Поскольку автоматическое подключение по типу может привести к появлению нескольких кандидатов, часто необходимо иметь больший контроль над процессом отбора. Один из способов сделать это-с `@Primary`помощью аннотации Spring. `@Primary` указывает, что конкретному компоненту следует отдавать предпочтение, когда несколько компонентов являются кандидатами на автоматическое подключение к однозначной зависимости. Если среди кандидатов существует ровно один основной компонент, он становится автоматически подключенным значением.

Рассмотрим следующую конфигурацию, которая определяет `firstMovieCatalog`в качестве основной`MovieCatalog`:

```java
@Configuration
public class MovieConfiguration {

    @Bean
    @Primary
    public MovieCatalog firstMovieCatalog() { ... }

    @Bean
    public MovieCatalog secondMovieCatalog() { ... }

    // ...
}
```

В предыдущей конфигурации следующее `MovieRecommender`автоматически подключается к `firstMovieCatalog`:

```java
public class MovieRecommender {

    @Autowired
    private MovieCatalog movieCatalog;

    // ...
}
```

Ниже приведены соответствующие определения компонентов:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xmlns:context="http://www.springframework.org/schema/context"
    xsi:schemaLocation="http://www.springframework.org/schema/beans
        https://www.springframework.org/schema/beans/spring-beans.xsd
        http://www.springframework.org/schema/context
        https://www.springframework.org/schema/context/spring-context.xsd">

    <context:annotation-config/>

    <bean class="example.SimpleMovieCatalog" primary="true">
        <!-- inject any dependencies required by this bean -->
    </bean>

    <bean class="example.SimpleMovieCatalog">
        <!-- inject any dependencies required by this bean -->
    </bean>

    <bean id="movieRecommender" class="example.MovieRecommender"/>

</beans>
```

{% hint style="info" %}
[https://docs.spring.io/spring-framework/docs/5.3.14/reference/html/core.html#beans-autowired-annotation-primary](https://docs.spring.io/spring-framework/docs/5.3.14/reference/html/core.html#beans-autowired-annotation-primary)
{% endhint %}
