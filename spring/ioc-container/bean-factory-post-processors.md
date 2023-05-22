---
description: Настройка метаданных конфигурации с помощью BeanFactoryPostProcessor
---

# Bean Factory Post Processors

<figure><img src="../.gitbook/assets/image (5).png" alt=""><figcaption></figcaption></figure>

`BeanFactoryPostProcessor`. Семантика этого интерфейса аналогична семантике интерфейса`BeanPostProcessor`, с одним существенным отличием:

`BeanFactoryPostProcessor` работает с метаданными конфигурации компонента.&#x20;

То есть контейнер Spring IoC позволяет  `BeanFactoryPostProcessor`считывать метаданные конфигурации и потенциально изменять их _до_ того, как контейнер создаст экземпляры любых компонентов, отличных от `BeanFactoryPostProcessor`экземпляров.

Вы можете настроить несколько `BeanFactoryPostProcessor`экземпляров и управлять порядком, в котором `BeanFactoryPostProcessor`выполняются эти экземпляры, задав `order`свойство.&#x20;

Однако вы можете установить это свойство только в том случае, если `BeanFactoryPostProcessor`оно реализует `Ordered`интерфейс. Если вы пишете свой собственный`BeanFactoryPostProcessor`, вам также следует подумать о реализации `Ordered`интерфейса. См. javadoc интерфейсов [`BeanFactoryPostProcessor`](https://docs.spring.io/spring-framework/docs/6.0.4/javadoc-api/org/springframework/beans/factory/config/BeanFactoryPostProcessor.html)and [`Ordered`](https://docs.spring.io/spring-framework/docs/6.0.4/javadoc-api/org/springframework/core/Ordered.html)для получения более подробной информации.

{% hint style="info" %}
[https://docs.spring.io/spring-framework/docs/current/reference/html/core.html#beans-factory-extension-factory-postprocessors](https://docs.spring.io/spring-framework/docs/current/reference/html/core.html#beans-factory-extension-factory-postprocessors)
{% endhint %}
