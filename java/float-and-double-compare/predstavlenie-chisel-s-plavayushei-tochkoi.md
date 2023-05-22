# Представление чисел с плавающей точкой

#### Перевод из 10 в 2:

![Перевод из 10 в 2](<../.gitbook/assets/image (380).png>)

#### Экспоненциальная запись:

![](<../.gitbook/assets/image (307).png>)

* **Мантиса - дробная часть числа, перед которой всегда идет 1.**
* **Экспонента - степень основания, которая равняется числу на которое ТОЧКА была СМЕЩЕНА ОТНОСИТЕЛЬНО своего начального положения.**

**Приведем(подгоним) число к экспоненциальному виду( Перед точкой должна находится только одна 1):**

![](<../.gitbook/assets/image (100).png>)

{% tabs %}
{% tab title="Вправо" %}
**Если нужно сдвигать вправо, то степень со знаком "-"**
{% endtab %}

{% tab title="Пример" %}
![](<../.gitbook/assets/image (98).png>)
{% endtab %}
{% endtabs %}

Вернемся к примеру, представим число в 2-ом виде (степень тоже представлена в 2--ом виде):

![](<../.gitbook/assets/image (35).png>)

Для хранения такого числа стандарт IEEE754 предлагает следующие форматы:

![](<../.gitbook/assets/image (451).png>)

### Рассмотрим на примере 32 битного числа :

32 бита разбиваются на три части: 1 бит - знак, 8 бит - экспонента, 23 бита - мантисса.

![](<../.gitbook/assets/image (292).png>)

<details>

<summary>Double</summary>

![](<../.gitbook/assets/image (11).png>)



</details>

<mark style="color:green;">**Т.к в экспоненциальной форме записи двоичного числа целая часть всегда равна единице (1), то хранить в памяти ее не требуется:**</mark>

Дробная часть числа сохраняется относительно 23 бит с левой стороны, свободное место справа заполняется 0:

![](<../.gitbook/assets/image (261).png>)

Основание всегда равно 10 следовательно хранить его так же как и целую часть не требуется.

Степень, для ее хранение используется 8 бит, т.к. она может иметь знак " - ", необходимо это учитывать, но кодирование в формате Дополнительный код не подойдет( по ряду причин), т.к не даст процессору быстро выполнять сравнение чисел.

Поэтому  решили хранить ПОЛОЖИТЕЛЬНЫЕ и ОТРИЦАТЕЛЬНЫЕ числа относительно числа 127 8-битного ( 0-255 ) диапазона, где  знак мантиссы учитывается  с помощью выражения (127 + степень):&#x20;

![](<../.gitbook/assets/image (368).png>)

если число (127 + степень ) ОТРИЦАТЕЛЬНОЕ, то получим число МЕНЬШЕ 127, если ПОЛОЖИТЕЛЬНОЕ - БОЛЬШЕ 127.

из этого диапазона ( 0 - 255 ) предусмотренного для хранения экспоненты, доступно не 255 значений, 254, т.к стандарт IEEE предусматривает хранение специальных значений   -               " +Infinity "  и " - Infinity ".

NaN - ЗНАКовый бит - не имеет значения, степень( экспонента) - все единицы( 11111111 ), дробная часть - любое число отличное от 0 (т.к 0  необходим для Infinity ).

![](<../.gitbook/assets/image (101).png>)

![](<../.gitbook/assets/image (285).png>)

JAVA EXAMPLE :

![](<../.gitbook/assets/image (385).png>)

![](<../.gitbook/assets/image (243).png>)

![](<../.gitbook/assets/image (21).png>)

#### Автор изображений: [https://www.youtube.com/channel/UCIn6hza5Ai119FJnLMJzECQ](https://www.youtube.com/channel/UCIn6hza5Ai119FJnLMJzECQ)

{% embed url="https://youtu.be/U0U8Ddx4TgE" %}

{% embed url="https://youtu.be/VCC6ltusicA?list=PLoNpsSBBpDYfjNSWpkKsKB0dTDJ6maZEB" %}

{% embed url="https://youtu.be/2NC1keTruVY?list=PLoNpsSBBpDYfjNSWpkKsKB0dTDJ6maZEB" %}