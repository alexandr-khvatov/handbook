# Fine-tuning Annotation-based Autowiring with Qualifiers

`@Primary` это эффективный способ использовать автоподключение по типу в нескольких случаях, когда можно определить одного основного кандидата. Когда вам нужно больше контролировать процесс выбора, вы можете использовать `@Qualifier`аннотацию Spring. Вы можете связать значения квалификатора с конкретными аргументами, сузив набор совпадений типов, чтобы для каждого аргумента был выбран конкретный компонент. В простейшем случае это может быть простое описательное значение, как показано в следующем примере:

```java
public class MovieRecommender {

    @Autowired
    @Qualifier("main")
    private MovieCatalog movieCatalog;

    // ...
}
```

Вы также можете указать `@Qualifier`аннотацию к отдельным аргументам конструктора или параметрам метода, как показано в следующем примере:

```java
public class MovieRecommender {

    private MovieCatalog movieCatalog;

    private CustomerPreferenceDao customerPreferenceDao;

    @Autowired
    public void prepare(@Qualifier("main") MovieCatalog movieCatalog,
            CustomerPreferenceDao customerPreferenceDao) {
        this.movieCatalog = movieCatalog;
        this.customerPreferenceDao = customerPreferenceDao;
    }

    // ...
}
```

В следующем примере показаны соответствующие определения компонентов.

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

    <bean class="example.SimpleMovieCatalog">
        <qualifier value="main"/> 

        <!-- inject any dependencies required by this bean -->
    </bean>

    <bean class="example.SimpleMovieCatalog">
        <qualifier value="action"/> 

        <!-- inject any dependencies required by this bean -->
    </bean>

    <bean id="movieRecommender" class="example.MovieRecommender"/>

</beans>
```

&#x20;Компонент со значением main квалификатора связан с аргументом конструктора, который имеет то же значение.

&#x20;Компонент со значением action квалификатора связан с аргументом конструктора, который имеет то же значение.



Тем не менее, если вы намерены выразить инъекцию, основанную на аннотациях , по имени, не используйте ее в первую очередь`@Autowired`, даже если она способна выбирать по имени компонента среди кандидатов, подходящих по типу. Вместо этого используйте аннотацию JSR-250`@Resource`, которая семантически определена для идентификации конкретного целевого компонента по его уникальному имени, при этом объявленный тип не имеет значения для процесса сопоставления. `@Autowired` имеет несколько иную семантику: после выбора компонентов-кандидатов по типу указанное `String`значение квалификатора учитывается только в тех кандидатах, выбранных по типу (например, соответствие `account` квалификатор против бобов, помеченных той же меткой квалификатора).

{% hint style="danger" %}
#### `@Autowired` применяется к полям, конструкторам и методам с несколькими аргументами, позволяя сужать аннотации квалификаторов на уровне параметров. Напротив, `@Resource`поддерживается только для полей и методов задания свойств компонентов с одним аргументом. Как следствие, вам следует придерживаться классификаторов, если вашей целью внедрения является конструктор или метод с несколькими аргументами.
{% endhint %}

{% hint style="info" %}
[https://docs.spring.io/spring-framework/docs/5.3.14/reference/html/core.html#beans-autowired-annotation-qualifiers](https://docs.spring.io/spring-framework/docs/5.3.14/reference/html/core.html#beans-autowired-annotation-qualifiers)
{% endhint %}
