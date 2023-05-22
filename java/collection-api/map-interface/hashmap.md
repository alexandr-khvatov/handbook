# HashMap

## <mark style="color:yellow;">put()</mark>,<mark style="color:yellow;">get()</mark> 0(1)

_HashMap_ работает по принципу **хеширования — алгоритму сопоставления данных объекта с некоторым репрезентативным целочисленным значением**. Функция хэширования применяется к ключевому объекту для вычисления индекса корзины для хранения и извлечения любой пары ключ-значение.

DEFAULT\_INITIAL\_CAPACITY **is the number of buckets in the HashMap.** _по умолчанию_ составляет 16.

```java
/** * The default initial capacity - MUST be a power of two. */
static final int DEFAULT_INITIAL_CAPACITY = 1 << 4; // aka 16
```

<mark style="color:green;">В частности, когда количество элементов становится больше емкости хеш-множества, умноженной на коэффициент заполнения, такое хеш-множество расширяется</mark>**.** Коэффициент загрузки по умолчанию составляет 75% от емкости.

**threshold=capacity \* loadFactor Когда емкость достигает threshold, ёмкость увеличивается вдвое и происходит перерасчет мапы(за счет чего изменяется порядок элементов).**&#x20;

Аналогично, мы можем создать нашу _мапу_, используя initial capacity, так и loadFactor:

```java
Map<String, String> mapWithInitialCapacityAndLF = new HashMap<>(5, 0.5f);
```

Новоявленный объект hashmap, содержит ряд свойств:

* **table** — Массив типа Node\<K,V> ,  который является хранилищем ссылок на списки (цепочки) значений;
* **loadFactor** — Коэффициент загрузки. Значение по умолчанию 0.75 является хорошим компромиссом между временем доступа и объемом хранимых данных;
* **threshold** — Предельное количество элементов, при достижении которого, размер хэш-таблицы увеличивается вдвое. Рассчитывается по формуле **(capacity \* loadFactor)**;
* **size** — Количество элементов HashMap-а;

\


![](<../../.gitbook/assets/image (366).png>)

{% hint style="info" %}
[**https://www.baeldung.com/java-hashmap-load-factor**](https://www.baeldung.com/java-hashmap-load-factor)
{% endhint %}
