# Lifecycle Callbacks

## **Initialization Callbacks**

`org.springframework.beans.factory.InitializingBean` интерфейс позволяет компоненту выполнять работу по инициализации после того, как контейнер установит все необходимые свойства компонента(после setter). `InitializingBean`  интерфейс определяет один метод:

```java
void afterPropertiesSet() throws Exception;
```

Мы рекомендуем вам не использовать `InitializingBean` интерфейс, потому что он излишне связывает код с Spring. В качестве альтернативы мы предлагаем использовать [`@PostConstruct`](https://docs.spring.io/spring-framework/docs/5.3.14/reference/html/core.html#beans-postconstruct-and-predestroy-annotations) аннотация или указание метода инициализации POJO. В случае метаданных конфигурации на основе XML вы можете использовать `init-method` атрибут, указывающий имя метода, имеющего пустую подпись без аргумента. С помощью конфигурации Java вы можете использовать `initMethod` атрибут `@Bean`. Видеть [Получение Обратных Вызовов Жизненного Цикла](https://docs.spring.io/spring-framework/docs/5.3.14/reference/html/core.html#beans-java-lifecycle-callbacks). Рассмотрим следующий пример:

```markup
<bean id="exampleInitBean" class="examples.ExampleBean" init-method="init"/>
```

```java
public class ExampleBean {

    public void init() {
        // do some initialization work
    }
}
```

Предыдущий пример имеет почти такой же эффект, как и следующий пример (который состоит из двух списков).:

```markup
<bean id="exampleInitBean" class="examples.AnotherExampleBean"/>
```

```java
public class AnotherExampleBean implements InitializingBean {

    @Override
    public void afterPropertiesSet() {
        // do some initialization work
    }
}
```

Однако первый из двух предыдущих примеров не связывает код с Spring.

## **Destruction Callbacks**

Осуществление программы `org.springframework.beans.factory.DisposableBean` интерфейс позволяет компоненту получить обратный вызов, когда контейнер, содержащий его, уничтожен. `DisposableBean`. Интерфейс определяет один метод:

```java
void destroy() throws Exception;
```

Мы рекомендуем вам не использовать `DisposableBean` интерфейс обратного вызова, потому что он излишне связывает код с Spring. В качестве альтернативы мы предлагаем использовать [`@PreDestroy`](https://docs.spring.io/spring-framework/docs/5.3.14/reference/html/core.html#beans-postconstruct-and-predestroy-annotations) аннотация или указание универсального метода, поддерживаемого определениями компонентов. С помощью метаданных конфигурации на основе XML вы можете использовать `destroy-method` атрибут на `<bean/>`. С помощью конфигурации Java вы можете использовать `destroyMethod` атрибут `@Bean`. Видеть [Получение Обратных Вызовов Жизненного Цикла](https://docs.spring.io/spring-framework/docs/5.3.14/reference/html/core.html#beans-java-lifecycle-callbacks). Рассмотрим следующее определение:

```markup
<bean id="exampleInitBean" class="examples.ExampleBean" destroy-method="cleanup"/>
```

```java
public class ExampleBean {

    public void cleanup() {
        // do some destruction work (like releasing pooled connections)
    }
}
```

Предыдущее определение имеет почти точно такой же эффект, как и следующее определение:

```markup
<bean id="exampleInitBean" class="examples.AnotherExampleBean"/>
```

```java
public class AnotherExampleBean implements DisposableBean {

    @Override
    public void destroy() {
        // do some destruction work (like releasing pooled connections)
    }
}
```

Однако первое из двух предыдущих определений не связывает код с Spring.
