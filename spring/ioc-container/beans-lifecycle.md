# 👾 Beans Lifecycle

1. BeanFactoryPostProcessor - докрутить bean definition (например, заменить выражение SpEL на значения из  property файла).
2. Sorted Bean Definition  - отсортировать bean-definition (сначала идут bean-def без зависимостей и bean - def реализующие интерфейс BeanFactoryPostProcessors и опционально Ordered для указания порядка выполнения BeanFactoryPostProcessors ).
3. Bean Constructor called
4. Setters called
5. <mark style="color:blue;">**BPP**</mark>** **<mark style="color:green;">**Before**</mark>** **<mark style="color:blue;">**Initialization**</mark>  (например, обработка аннотаций @Inject) - в фазе <mark style="color:green;">**BEFORE**</mark> возвращаем тот же самый bean
6. <mark style="color:green;">Initialization</mark> _<mark style="color:purple;">**callbacks**</mark>_:
   1. Methods annotated with _**`@PostConstruct`**_
   2. _**`afterPropertiesSet()`**_ as defined by the `InitializingBean` callback interface
   3. A custom configured _**`init()`**_ method     (xml)
7. <mark style="color:blue;">**BPP**</mark>**  **<mark style="color:red;">**After**</mark>**  **<mark style="color:blue;">**Initialization**</mark>  (например, обработка аннотаций @Transaction) - в фазе <mark style="color:red;">**AFTER**</mark> возвращаем proxy, при этом в <mark style="color:green;">**BEFORE**</mark> при необходимости необходимо сохранить метаинформацию о bean т.к может быть несколько BPP, которые уже возращают Proxy
8. Готовые beans
9. <mark style="color:red;">Destruction</mark> <mark style="color:purple;">**`callbacks`**</mark>:   Для Singleton Bean
   1. Methods annotated with _**`@PreDestroy`**_
   2. _**`destroy()`**_ as defined by the `DisposableBean` callback interface
   3. A custom configured _**`destroy()`**_ method    (xml)

<figure><img src="../.gitbook/assets/image (14).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (10).png" alt=""><figcaption></figcaption></figure>

При поднятии Context происходит сканирование classpath и собираются bean-definition&#x20;





Bean Constructor Called

&#x20;
