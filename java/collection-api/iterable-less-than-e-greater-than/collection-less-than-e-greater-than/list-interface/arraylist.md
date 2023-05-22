# ArrayList

## <mark style="color:yellow;">accessing</mark>  thru(через) index, <mark style="color:yellow;">add</mark>( to end) 0(1)

## <mark style="color:yellow;">other</mark> operations 0(n)

* <mark style="color:green;">**разрешает добавление  дубликатов и NULL-значения**</mark>

<mark style="color:orange;">**increase the size by 50%**</mark> we use right shift operator

Оптимизационные методы: ТримТуСайз() - обрезать массив по размеру, ЕнжурКапасити() - увеличить емкость на заданную величину (например, когда знаем, что будем добавлять 1\__000\__000 элементов, можно выделить сразу необходимую емкость)

To create an ArrayList, First need to create Object of ArrayList class.. ArrayList contains 3 types of constructors in Java 8

1. **ArrayList()**: This constructor is to initialize an empty List.
2. **ArrayList(int capacity):** This constructor we can pass capacity as a parameter, used to initialize the capacity by the user.
3. **ArrayList(Collection c):** In this constructor, we can pass a Collection c as a parameter, In which an Array list will contain the elements of Collection c.

```java
List<String> arrayList = new ArrayList<String>();
```

* private int <mark style="color:green;">**size**</mark>  - The size of the ArrayList (the number of elements it contains).
* transient Object\[] <mark style="color:green;">**elementData**</mark>  - The array buffer into which the elements of the ArrayList are stored. The capacity of the ArrayList is the length of this array buffer. Any empty ArrayList with elementData == DEFAULTCAPACITY\_EMPTY\_ELEMENTDATA will be expanded to DEFAULT\_CAPACITY when the first element is added.

```java
    /**
     * Default initial capacity.
     */
    private static final int DEFAULT_CAPACITY = 10;
    
      /**
     * The array buffer into which the elements of the ArrayList are stored.
     * The capacity of the ArrayList is the length of this array buffer. Any
     * empty ArrayList with elementData == DEFAULTCAPACITY_EMPTY_ELEMENTDATA
     * will be expanded to DEFAULT_CAPACITY when the first element is added.
     */
    transient Object[] elementData; // non-private to simplify nested class access

     /**
     * The size of the ArrayList (the number of elements it contains).
     *
     * @serial
     */
    private int size;
```

{% hint style="info" %}
[https://docs.oracle.com/javase/8/docs/api/java/util/ArrayList.html](https://docs.oracle.com/javase/8/docs/api/java/util/ArrayList.html)
{% endhint %}

{% hint style="warning" %}
[https://knpcode.com/java/collections/arraylist-internal-implementation-in-java/](https://knpcode.com/java/collections/arraylist-internal-implementation-in-java/)
{% endhint %}

Некоторые методы:

1. **add(int index, E element)**– This method inserts the passed element at the specified position in this list.
2. **add(E e)**– This method appends the specified element to the end of this list.
3. **addAll(int index, Collection\<? extends E> c)**– This method inserts all of the elements in the passed collection into this list, starting at the specified position.
4. **addAll(Collection\<? extends E> c)**– This method appends all of the elements in the specified collection to the end of this list, in the order that they are returned by the specified collection’s Iterator.
5. **clear()**– Method to remove all of the elements from this list.
6. **contains(Object o)**– Returns true if this list contains the specified element.
7. **get(int index)**– Returns the element at the specified position in this list.
8. **indexOf(Object o)**– Returns the index of the first occurrence of the specified element in this list, or -1 if this list does not contain the element.
9. **isEmpty()**– Returns true if this list contains no elements.
10. **iterator()**– Returns an iterator over the elements in this list in proper sequence.
11. **lastIndexOf(Object o)**– Returns the index of the last occurrence of the specified element in this list, or -1 if this list does not contain the element.
12. **remove(int index)**– Removes the element at the specified position in this list.
13. **remove(Object o)**– Removes the first occurrence of the specified element from this list, if it is present.
14. **removeIf(Predicate\<? super E> filter)**– Removes all of the elements of this collection that satisfy the given predicate.
15. **set(int index, E element)**– Replaces the element at the specified position in this list with the specified element.
16. **size()**– Returns the number of elements in this list.

#### <mark style="color:orange;">**Итератор Java ArrayList**</mark>

Используя итератор в ArrayList, вы можете последовательно просматривать список. Вы можете получить итератор, используя **метод iterator (), и список, используя метод ListIterator ()**. Разница между итератором и  [ListIterator](https://knpcode.com/java/collections/listiterator-in-java/) заключается в том, что листератор позволяет перемещаться по списку в любом направлении.

Итераторы, возвращаемые методами iterator и ListIterator, работают без сбоев. Если список структурно изменен в любое время после создания итератора любым способом, кроме как с помощью собственных методов удаления или добавления итератора, итератор создаст исключение **ConcurrentModificationException**. Обратите внимание, что итератор списка предоставляет как методы добавления, так и удаления, в то время как интерфейс итератора предоставляет только метод remove ().

#### <mark style="color:orange;">**ArrayList не является потокобезопасным**</mark>

ArrayList в Java не является потокобезопасным. Если экземпляр ArrayList является общим для нескольких потоков, и любой поток изменяет список структурно, то другие потоки могут не получить обновленный список. В таком сценарии список массивов должен быть синхронизирован извне с помощью **Collections.synchronizedList()**.
