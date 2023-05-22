# Instantiating Beans



```xml
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="http://www.springframework.org/schema/beans
        https://www.springframework.org/schema/beans/spring-beans.xsd">
    <bean class="codesjava.A"/>
    <bean id="first" name="1,uno" class="codesjava.A"/>
    <bean id="2" class="codesjava.A">
            <constructor-arg 
                index="0" 
                type="int" 
                value="23"/>
            <constructor-arg 
                index="1"
                type="String"
                value="beanTwo"/>
    </bean>
</beans>
```

```java
class A {
    public A(){
    }
    
    public A(int x){
        sout("creating A"+x);
    }
    
    public A(int x, String str){
        sout("creating A"+x + str);
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
