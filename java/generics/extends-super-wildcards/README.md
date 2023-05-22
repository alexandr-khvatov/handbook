# extends, super,wildcards(?)

<mark style="color:green;">**ЧТОБЫ ИСПОЛЬЗОВАТЬ**</mark>** параметризированный типы **<mark style="color:green;">**НЕОБХОДИМО ПОДСТАВИТЬ**</mark>** все параметры с помощью **<mark style="color:green;">**ЯВНЫХ НЕПРИМИТИВНЫХ ТИПОВ**</mark>**, либо **<mark style="color:green;">**С ПОМОЩЬЮ МАСКИ**</mark>

|          ref\_type         |   get   |       put      |       act\_type       |
| :------------------------: | :-----: | :------------: | :-------------------: |
|            Type            |  Object |       all      |          all          |
|          Type \<?>         |  Object |      null      |          all          |
|       Type\<Student>       | Student | Student +child |        Student        |
| Type \<? extends Student>  | Student |      null      | Student + все потомки |
|  Type \<? super Student>   |  Object | Student +child |      все родители     |

At heart, these terms describe how the subtype relation is affected by type transformations.\
(По сути, эти термины описывают, как отношение подтипов зависит от преобразования типов.)\
То есть, если

* A and B are types,
* f a type transformation, and
* ≤ the subtype relation (i.e. A ≤ B means that A is a subtype of B),



* f является **КОВАРИАНТНЫМ**, если A ≤ B подразумевает, что f(A) ≤ f(B)
* f является **КОНТРАВАРИАНТНЫМ**, если A ≤ B подразумевает, что f(B) ≤ f(A)
* f является **инвариантным**, если ни одно из вышеперечисленных не выполняется

````java
// КОВАРИАНТНОСТЬ
List <? extends Animal> animals = new ArrayList<Cat>();
Animal a = animals.get(0);

animals.add(new Cat()) // compiler error
animals.add(null) // good

```
````

### Ковариантность:

В этом случае вместо использования типа `T`в качестве аргумента типа данного универсального типа мы используем подстановочный знак, объявленный как`? extends T`, где `T`известен базовый тип.

```java
List<? extends Number> myNums = new ArrayList<Integer>();
List<? extends Number> myNums = new ArrayList<Float>();
List<? extends Number> myNums = new ArrayList<Double>();
```

И мы можем читать из нашей общей структуры`myNums`, делая:

```java
Number n = myNums.get(0);
```

Потому что мы можем быть уверены, что независимо от того , что содержит фактический список, он может быть преобразован в a `Number` (в конце концов, все, что расширяется`Number` , является a`Number`, верно?)&#x20;

Однако нам не разрешается ничего помещать в ковариантную структуру.

```java
myNumst.add(45L); //compiler error
```

Это было бы недопустимо, поскольку компилятор не может определить, каков фактический тип объекта в общей структуре. Это может быть все, что расширяется `Number` (например`Integer`,`Double`,`Long`), но компилятор не может быть уверен, что именно, и поэтому любая попытка получить универсальное значение считается небезопасной операцией, и она немедленно отклоняется компилятором. Так что мы можем читать, но не писать.

~~? или extends - не даёт добавлять элементы после того, как коллекция будет полностью готова. Т.к компилятор не сможет гарантировать, какие методы могут быть вызваны после при работе с элементами:~~

```java
public class Main {
    public static void main(String[] args) {
        List<? extends Number> numbers = Arrays.asList(10,2.0,17L);
        numbers.add(10L); // compile error
    }
}
```

### Контравариантность

Для контравариантности мы используем другой подстановочный знак , называемый`? super T`, где `T`наш базовый тип. С помощью контравариантности мы можем сделать обратное. Мы можем поместить вещи в общую структуру, но мы не можем ничего из нее прочитать.

В этом случае фактическая природа объекта имеет `List Object`место, и благодаря контравариантности мы можем поместить `Number` в него а , в основном потому`Number` , что у `Object` а есть общий предок. Таким образом, все числа также являются объектами, и поэтому это справедливо.

Однако мы не можем безопасно прочитать что-либо из этой контравариантной структуры, предполагая, что мы получим число.

```java
Number myNum = myNums.get(0); 
```

Как мы видим, если бы компилятор позволил нам написать эту строку, мы бы получили a `ClassCastException` во время выполнения. Таким образом, опять же, компилятор не рискует допустить эту небезопасную операцию и немедленно отклоняет ее.

### Принцип получения/Размещения

Таким образом, мы используем ковариацию, когда намерены извлекать из структуры только общие значения. Мы используем контравариантность, когда намереваемся поместить в структуру только общие значения, и мы используем инвариант, когда намереваемся сделать и то, и другое.

Лучший пример, который у меня есть, - это следующий, который копирует любые числа из одного списка в другой список.

```java
    publicstaticvoidcopy(List<? extendsNumber> source,
                         List<? superNumber> destiny) {
        for(Number number : source) {
            destiny.add(number);
        }
    }
    
    
    List<Integer> myInts = asList(1,2,3,4);
    List<Integer> myDoubles = asList(3.14, 6.28);
    List<Object> myObjs = newArrayList<Object>();
    copy(myInts, myObjs);
    copy(myDoubles, myObjs);
```

#### Bounded wildcard

* <mark style="color:green;">extends</mark> - ограничение сверху
* <mark style="color:blue;">super</mark> - ограничение снизу
* <mark style="color:orange;">IN</mark> - аргумент: предоставляет значение
* <mark style="color:orange;">OUT</mark> - аргумент: получает значение

```java
    void copy(List<? extends Product> src, List<? super Product> dest) {
        for (Product p : src) {
            dest.add(p);
        }
    }
```

* <mark style="color:orange;">IN</mark> - используйте <mark style="color:green;">extends</mark>
* <mark style="color:yellow;">OUT</mark> - используйте <mark style="color:blue;">super</mark>
* Если до IN можно достучаться через методы Object, тогда используйте ?
* Если переменная одновременно IN и OUT - не используйте wildcard
