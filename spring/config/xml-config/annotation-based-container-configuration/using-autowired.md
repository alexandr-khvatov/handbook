---
description: Применять аннотацию  @Autowired можно к полям, сеттерам, конструктору.
---

# Using @Autowired

Конструкторам:

```java
public class MovieRecommender {

    private final CustomerPreferenceDao customerPreferenceDao;

    @Autowired
    public MovieRecommender(CustomerPreferenceDao customerPreferenceDao) {
        this.customerPreferenceDao = customerPreferenceDao;
    }

    // ...
}
```

Сеттерам:

```java
public class SimpleMovieLister {

    private MovieFinder movieFinder;

    @Autowired
    public void setMovieFinder(MovieFinder movieFinder) {
        this.movieFinder = movieFinder;
    }

    // ...
}
```

Вы также можете применить аннотацию к методам с произвольными именами и несколькими аргументами, как показано в следующем примере:

```java
public class MovieRecommender {

    private MovieCatalog movieCatalog;

    private CustomerPreferenceDao customerPreferenceDao;

    @Autowired
    public void prepare(MovieCatalog movieCatalog,
            CustomerPreferenceDao customerPreferenceDao) {
        this.movieCatalog = movieCatalog;
        this.customerPreferenceDao = customerPreferenceDao;
    }

    // ...
}
```

Вы также можете применить `@Autowired`его к полям и даже смешать с конструкторами, как показано в следующем примере:

```java
public class MovieRecommender {

    private final CustomerPreferenceDao customerPreferenceDao;

    @Autowired
    private MovieCatalog movieCatalog;

    @Autowired
    public MovieRecommender(CustomerPreferenceDao customerPreferenceDao) {
        this.customerPreferenceDao = customerPreferenceDao;
    }

    // ...
}
```

Вы также можете поручить Spring предоставить все компоненты определенного типа из`ApplicationContext`, добавив `@Autowired`аннотацию к полю или методу, который ожидает массив этого типа, как показано в следующем примере:

```java
public class MovieRecommender {

    @Autowired
    private MovieCatalog[] movieCatalogs;

    // ...
}
```

То же самое относится и к типизированным коллекциям, как показано в следующем примере:

```java
public class MovieRecommender {

    private Set<MovieCatalog> movieCatalogs;

    @Autowired
    public void setMovieCatalogs(Set<MovieCatalog> movieCatalogs) {
        this.movieCatalogs = movieCatalogs;
    }

    // ...
}
```

{% hint style="info" %}
#### `@Autowired`, `@Inject`,`@Value`, и `@Resource`аннотации обрабатываются Spring `BeanPostProcessor` реализации. Это означает, что вы не можете применять эти аннотации в своих собственных `BeanPostProcessor`или `BeanFactoryPostProcessor`типах (если таковые имеются). Эти типы должны быть "подключены" явно с помощью XML или `@Bean`метода Spring.
{% endhint %}

{% hint style="info" %}
[https://docs.spring.io/spring-framework/docs/5.3.14/reference/html/core.html#beans-autowired-annotation](https://docs.spring.io/spring-framework/docs/5.3.14/reference/html/core.html#beans-autowired-annotation)
{% endhint %}
