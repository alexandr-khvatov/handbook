# TypeFilters

<figure><img src="../../.gitbook/assets/image (33).png" alt=""><figcaption></figcaption></figure>

```xml
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xmlns:context="http://www.springframework.org/schema/context"
       xsi:schemaLocation="http://www.springframework.org/schema/beans
                             http://www.springframework.org/schema/beans/spring-beans.xsd
                             http://www.springframework.org/schema/context
                             http://www.springframework.org/schema/context/spring-context-4.0.xsd">
    <context:component-scan base-package="com.dmdev.spring"
                            annotation-config="true"
                            resource-pattern="**/*.class"
                            scoped-proxy="no"
                            use-default-filters="true"><!--Type filters is annotation-->
        <context:include-filter type="annotation" expression="org.springframework.stereotype.Component"/>
        <context:include-filter type="assignable" expression="com.dmdev.spring.database.repository.CrudRepository"/>
        <context:include-filter type="regex" expression="com\..+Repository"/>
    </context:component-scan>

    <context:property-placeholder location="classpath:application.properties"/>

    <bean class="org.springframework.context.annotation.CommonAnnotationBeanPostProcessor"/>

    <bean class="org.springframework.context.support.PropertySourcesPlaceholderConfigurer">
        <property name="locations" value="classpath:application.properties"/>
    </bean>

    <bean id="driver" class="java.lang.String">
        <constructor-arg type="java.lang.String" value="${db.driver}"/>
    </bean>
    
    <bean id="companyRepository" class="com.dmdev.spring.database.repository.CompanyRepository" init-method="init"/>

</beans>
```





<figure><img src="../../.gitbook/assets/image (16).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (37).png" alt=""><figcaption></figcaption></figure>
