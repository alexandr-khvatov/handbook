# Using @Value

`@Value` is typically used to inject externalized properties:

```java
@Component
public class MovieRecommender {

    private final String catalog;

    public MovieRecommender(@Value("${catalog.name}") String catalog) {
        this.catalog = catalog;
    }
}
```

Со следующей конфигурацией:

```java
@Configuration
@PropertySource("classpath:application.properties")
public class AppConfig { }
```

И следующий `application.properties`файл:

```
catalog.name=MovieCatalog
```

В этом случае `catalog`параметр и поле будут равны `MovieCatalog`значению.

По умолчанию мягкий преобразователь встроенных значений предоставляется Spring. Он попытается разрешить значение свойства, и если оно не может быть разрешено, в качестве значения будет введено имя свойства (например`${catalog.name}`). Если вы хотите сохранить строгий контроль над несуществующими значениями, вам следует объявить `PropertySourcesPlaceholderConfigurer`компонент, как показано в следующем примере:

```java
@Configuration
public class AppConfig {

    @Bean
    public static PropertySourcesPlaceholderConfigurer propertyPlaceholderConfigurer() {
        return new PropertySourcesPlaceholderConfigurer();
    }
}
```
