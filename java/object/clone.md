---
description: Object.clone()  не вызывает конструктор при клонировании
---

# clone

имеет модификатор доступа protected, что говорит о том, что должен быть переопределен.

Как переопределить Object.clone():

* сделать метод общедоступным
* чтобы использовать нативную реализацию необходимо вызвать super.clone();
* реализовать интерфейс Cloneable, иначе выбросится CloneNotSupportedException
* <mark style="color:red;">по умолчанию будет выполнено поверхстное копирование.</mark>



```java
@Override
public Person clone() throws CloneNotSupportedException {
    return (Person)super.clone();
}
```

![](<../.gitbook/assets/image (34).png>)

## Глубокое копирование

~~ну такое:~~

~~В других случаях необходимо обеспечить функциональность глубокого копирования. Проблема в том, что вы больше не можете использовать механизм клонирования объекта для этого, и вам нужно реализовать свой собственный. В таких случаях может быть проще попробовать один из альтернативных подходов клонирования (см. Альтернативы ниже). Если вы хотите реализовать его в любом случае, у вас есть в основном два варианта. Сначала - сделайте все клонирование вручную - создайте новый экземпляр с помощью конструктора и заполните все поля. Второй - все еще использовать `super.clone()`но вместо того , чтобы возвращать клонированный объект напрямую, просто вручную скопируйте небезопасные поля - примитивные или неизменяемые.~~

<mark style="color:red;">**Нельзя перезаписать final переменные при последнем описанном подходе.**</mark>

## Альтернативы&#x20;

### Конструктор копирования

```java
public Person(Person personToCopy) {
    this.firstName = personToCopy.firstName;
    this.lastName = personToCopy.lastName;
    ...
}
```

### Статический фабричный метод

```java
public static Person deepCopyPerson(Person personToCopy) {
    Person copiedPerson = new Person();
    copiedPerson.firstName = personToCopy.firstName;
    copiedPerson.lastName = personToCopy.lastName;
    ...
    return copiedPerson;
}
```

### Сериализация/десериализация <a href="#serializationdeserialization" id="serializationdeserialization"></a>

### Reflection <a href="#reflection" id="reflection"></a>
