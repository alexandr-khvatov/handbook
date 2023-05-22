# Bean definition readers

В BeanDefinitionReaders передаются Type Filters (по умолчанию annotation) и на основании этих фильтров выполняется поиск классов, на основании которых создаются bean definition и попадают в [жизненный цикл бина](../beans-lifecycle.md) и создаются полноценные бины.

```xml
<context:component-scan base-package="com.dmdev.spring"
                            annotation-config="true"
                            resource-pattern="**/*.class"
                            scoped-proxy="no"
                            use-default-filters="false">
        <context:include-filter type="annotation" expression="org.springframework.stereotype.Component"/>
        <context:include-filter type="assignable" expression="com.dmdev.spring.database.repository.CrudRepository"/>
        <context:include-filter type="regex" expression="com\..+Repository"/>
    </context:component-scan>
```

<figure><img src="../../.gitbook/assets/image (18).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (27).png" alt=""><figcaption></figcaption></figure>
