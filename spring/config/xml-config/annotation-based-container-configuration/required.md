---
description: Применять аннотацию  @Autowired можно сеттерам.
---

# @Required

```java
public class SimpleMovieLister {

    private MovieFinder movieFinder;

    @Required
    public void setMovieFinder(MovieFinder movieFinder) {
        this.movieFinder = movieFinder;
    }

    // ...
}
```

Эта аннотация указывает, что затронутое свойство компонента должно быть заполнено во время настройки с помощью явного значения свойства в определении компонента или с помощью автоматического подключения. Контейнер создает исключение, если затронутое свойство компонента не было заполнено. Это позволяет избежать нетерпеливого и явного сбоя, избегая `NullPointerException` случаев и тому подобного в дальнейшем. Мы по-прежнему рекомендуем помещать утверждения в сам класс bean (например, в метод инициализации). Это обеспечивает выполнение этих требуемых ссылок и значений, даже если вы используете класс вне контейнера.

{% hint style="danger" %}
`@Required`аннотации и `RequiredAnnotationBeanPostProcessor`формально устарели с Spring Framework 5.1, в пользу использования инъекции конструктора для требуемых настроек (или пользовательской реализации `InitializingBean.afterPropertiesSet()`или пользовательского @PostConstruct метода вместе с методами настройки свойств компонентов).
{% endhint %}

{% hint style="info" %}
[https://docs.spring.io/spring-framework/docs/5.3.14/reference/html/core.html#beans-required-annotation](https://docs.spring.io/spring-framework/docs/5.3.14/reference/html/core.html#beans-required-annotation)
{% endhint %}
