# Constructor-based Dependency Injection

```xml
<beans>
    <bean id="beanOne" class="x.y.ThingOne">
        <constructor-arg ref="beanTwo"/>
        <constructor-arg ref="beanThree"/>
    </bean>

    <bean id="beanTwo" class="x.y.ThingTwo"/>

    <bean id="beanThree" class="x.y.ThingThree"/>
</beans>
```

```java
package x.y;

public class ThingOne {

    public ThingOne(ThingTwo thingTwo, ThingThree thingThree) {
        // ...
    }
}
```

{% hint style="info" %}
[https://docs.spring.io/spring-framework/docs/5.3.14/reference/html/core.html#beans-constructor-injection](https://docs.spring.io/spring-framework/docs/5.3.14/reference/html/core.html#beans-constructor-injection)
{% endhint %}
