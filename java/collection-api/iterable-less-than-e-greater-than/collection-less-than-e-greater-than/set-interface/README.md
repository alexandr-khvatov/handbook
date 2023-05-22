---
description: реализованы на Map-ах
---

# Set  (Interface)

## <mark style="color:red;">**no duplicates**</mark>

At most one null value depending on implementation; no null if this Set uses nator or its Comparator doesn't allow nulls.

Максимум одно нулевое значение в зависимости от выполнение; нет нуля, если этот набор использует nator или его компаратор не допускают пустых значений.

![](<../../../../.gitbook/assets/image (157).png>)

Пример создания своего Set:

![](<../../../../.gitbook/assets/image (334).png>)

Дефолтная реализация метода contains работает через перебор всего сета через итератор, что не производительно, и стоит задуматься при создании собственных Set реализаций. Дефолтная реализация в AbstractCollection:

&#x20;

![](<../../../../.gitbook/assets/image (407).png>)

Стоит переопределить при необходимости: например, что - то типо того:

![](<../../../../.gitbook/assets/image (280).png>)
