# Наследование

Можем создать другой параметризованный тип, либо конкретный параметризованный тип

![](<../../../.gitbook/assets/image (224).png>)

![](<../../../.gitbook/assets/image (151).png>)

![](<../../../.gitbook/assets/image (86).png>)

Нужно <mark style="color:yellow;"><mark style="color:orange;">МЕНЬШЕ ВОЗМОЖНОСТЕЙ<mark style="color:orange;"></mark> - <mark style="color:orange;">**НАД**</mark><mark style="color:yellow;"><mark style="color:orange;">**тип**<mark style="color:orange;"></mark>, <mark style="color:green;">БОЛЬШЕ ВОЗМОЖНОСТЕЙ</mark> - <mark style="color:green;">ПОДтип</mark>.

Если S является надтипом T, тип X\<S> не является надтипом X\<T>

![](<../../../.gitbook/assets/image (363).png>)

![](<../../../.gitbook/assets/image (408).png>)

## PECS

![т.к не находятся на одно линии наследования](<../../../.gitbook/assets/image (341).png>)

т.к не находятся на одно линии наследования

Можем читать, но проблема записи.

![](<../../../.gitbook/assets/image (218).png>)

![](<../../../.gitbook/assets/image (16).png>)

Можем записывать, но проблема чтения.

![](<../../../.gitbook/assets/image (323).png>)

![](<../../../.gitbook/assets/image (332).png>)

![](<../../../.gitbook/assets/image (85).png>)

![](<../../../.gitbook/assets/image (333).png>)

![](<../../../.gitbook/assets/image (288).png>)

![](<../../../.gitbook/assets/image (441).png>)

Пример из java collection api:&#x20;

![](<../../../.gitbook/assets/image (201).png>)

Можно было сделать лучше:

![](<../../../.gitbook/assets/image (111).png>)

![](<../../../.gitbook/assets/image (189).png>)

![](<../../../.gitbook/assets/image (365).png>)

RAW - TYPE  - это generic без параметров

![](<../../../.gitbook/assets/image (247).png>)

#### ДЖЕНЕРИКИ и МАССИВЫ: <mark style="color:red;">нельзя параметризовать</mark> т.к в java массив приводим к Object

![](<../../../.gitbook/assets/image (29).png>)

![](<../../../.gitbook/assets/image (14).png>)

![](<../../../.gitbook/assets/image (40).png>)
