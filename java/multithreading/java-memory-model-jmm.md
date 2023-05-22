# Java Memory Model - JMM

{% hint style="info" %}
JMM  - это спецификация или набор правил, которые гарантируют видимость полей при изменении порядка инструкций.
{% endhint %}

JMM говорит о записях в кучу, с локальными переменными все просто они пишутся в стэк и их видит только один поток.

согласно спецификации в JVM допускаются различные оптимизации в рамках одного потока,&#x20;

поэтому обращение к не синхронизированным переменным одного потока из другого потока может приводить к не очевидным вещам.

![](<../.gitbook/assets/image (393).png>)

## Выполнение вне очереди

![](<../.gitbook/assets/image (257).png>)

допускаются перестановки



![](<../.gitbook/assets/image (252).png>)

![](<../.gitbook/assets/image (90).png>)

## Видимость полей

![](<../.gitbook/assets/image (293).png>)

![](<../.gitbook/assets/image (177).png>)

![](<../.gitbook/assets/image (450).png>)

![](<../.gitbook/assets/image (329).png>)

РЕШЕНИЕ:

![](<../.gitbook/assets/image (455).png>)

## [happens - before](java-memory-model-jmm.md#undefined)



![](<../.gitbook/assets/image (103).png>)

{% embed url="https://www.youtube.com/watch?ab_channel=DefogTech&index=4&list=PLhfHPmPYPPRk6yMrcbfafFGSbE2EPK_A6&v=Z4hMFBvCDV4" %}
