# AA in Spring Security

Spring предоставляет `Filter`реализацию с именем[`DelegatingFilterProxy`](https://docs.spring.io/spring-framework/docs/5.3.22/javadoc-api/org/springframework/web/filter/DelegatingFilterProxy.html), которая позволяет соединять жизненный цикл контейнера сервлета и Spring `ApplicationContext`. Контейнер сервлета позволяет регистрировать `Filter`s, используя свои собственные стандарты, но он не знает о компонентах, определенных Spring. `DelegatingFilterProxy`может быть зарегистрирован с помощью стандартных механизмов контейнеров сервлетов, но делегирует всю работу компоненту Spring, который реализует `Filter`.

Вот картина того, как `DelegatingFilterProxy`вписывается в [`Filter`s и`FilterChain`](https://docs.spring.io/spring-security/reference/servlet/architecture.html#servlet-filters-review) .

<figure><img src="../../.gitbook/assets/image (8).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (44).png" alt=""><figcaption></figcaption></figure>
