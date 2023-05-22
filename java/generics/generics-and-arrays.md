# generics and arrays

#### ДЖЕНЕРИКИ и МАССИВЫ: <mark style="color:red;">нельзя параметризовать</mark> т.к в java массив приводим к Object

![](<../.gitbook/assets/image (278).png>)

![](<../.gitbook/assets/image (271).png>)

Heap pollution

В языке [программирования Java](https://en.wikipedia.org/wiki/Java\_programming) Heap pollution - это ситуация, возникающая, когда переменная [параметризованного типа](https://en.wikipedia.org/wiki/Java\_syntax#Generics) ссылается на объект, который не относится к этому параметризованному типу.

![](<../.gitbook/assets/image (439).png>)

Если из массива только читаем, то @SafeVarargs можно писать спокойно.

![](<../.gitbook/assets/image (440).png>)

{% embed url="https://youtu.be/usiKCn7SwxI?list=PLlb7e2G7aSpRZSRZxANkvpYC82BXUzCTY" %}
