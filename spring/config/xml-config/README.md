# XML - config

С помощью xml - config указываем  как брать java - код и вызывать его. (Через xml можно сделать некий список бинов, а реальную генерацию писать через java - код)

{% code title="XmlConfig.xml" %}
```xml
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="http://www.springframework.org/schema/beans
        https://www.springframework.org/schema/beans/spring-beans.xsd">
    <bean class="codesjava.A"/>
    <bean id="first" name="1,uno" class="codesjava.A"/>
    <bean id="second" class="codesjava.Creator" factory-method="getA"/>
    <bean id="third" class="codesjava.A" factory-bean="generator" factory-method="getA"/>
    <bean id="generator" class="codesjava.CreatorFromObject"/>
</beans>
```
{% endcode %}

{% code title="CodesJava.java" %}
```java
class A {
    public A(){
    }
    public A(int x){
        sout("creating A"+x);
    }
}

class Creator {
    A getA(){
    return new A(5);
    }
}

class CreatorFromObject {
    A getA(){
    return new A(5);
    }
}
```
{% endcode %}

{% embed url="https://www.youtube.com/watch?ab_channel=%D0%95%D1%80%D0%BC%D0%B0%D0%BA%D0%BE%D0%B2Java&index=29&list=PLoNpsSBBpDYeByCUgtV9W2hZOybtBAF0m&v=y9cPIE4SVXc" %}
