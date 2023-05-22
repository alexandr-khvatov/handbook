# singleton \[Тагир Валеев]

в if() могут зайти сразу несколько потоков

![](<../../.gitbook/assets/image (73).png>)

![](<../../.gitbook/assets/image (421).png>)

С синхронизацией, но будет потеря производительности т.к метод синхронизирован.

Хотя синхронизация необходима только при первом обращении, когда не создан объект, далее она не требуется.

![](<../../.gitbook/assets/image (424).png>)

![](<../../.gitbook/assets/image (286).png>)

## Пример как не надо:

![](<../../.gitbook/assets/image (362).png>)

![](<../../.gitbook/assets/image (432).png>)

![](<../../.gitbook/assets/image (264).png>)

## РЕШЕНИЕ ПРОБЛЕМЫ:

**Добавляем ребро happens - before**&#x20;

![](<../../.gitbook/assets/image (413).png>)

## или

![](<../../.gitbook/assets/image (115).png>)

## ПРИМЕР 2:

Переложить проблемы на плечи машины JVM:  <mark style="color:red;">**JVM гарантирует, что каждый класс будет ИНИЦИАЛИЗИРОВАН ЕДИНОЖДЫ.**</mark> Внутренний статический класс Holder будет инициализирован единожды при первом обращении - вызов метода getInstance();

![](<../../.gitbook/assets/image (170).png>)

{% embed url="https://compscicenter.ru/courses/java/nsk/2020-spring/classes/5767" %}
