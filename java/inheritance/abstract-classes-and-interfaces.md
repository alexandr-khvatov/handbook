# abstract classes and interfaces

Применение абстрактных классов и интерфейсов:

* Ключевое слово abstract представляет собой один из спецификаторов (точнее говоря, non-access modifiers), которые меняют дефолтные характеристики Джава-класса и/или его членов.
* Класс можно объявить абстрактным даже в том случае, когда в нем не определено ни одного абстрактного метода.&#x20;
* Абстрактный тип нельзя инстанцировать и, следовательно, его код можно использовать на практике только после расширения/имплементации конкретным подтипом.&#x20;
* У абстрактного метода нет тела; с другой стороны, он следует всем правилам переопределения, которые распространяются на обычные методы.
* Первый же конкретный класс, который расширяет абстрактный класс, обязан имплементировать все унаследованные абстрактные методы.

{% hint style="info" %}
Абстрактные классы и методы не могут быть private или final.
{% endhint %}

* Абстрактный класс может расширять конкретный класс, и наоборот.&#x20;
* Интерфейс – это абстрактный тип → нельзя инстанцировать; ловушка на экзамене!&#x20;
* Помимо абстрактных методов и static final переменных (иными словами, констант), которые были допустимы в интерфейсах до версии Java 1.8, сейчас интерфейсы могут иметь default- и static-методы.

```java
import java.util.ArrayList;
import java.util.List;
class Test {
    public static void main(String[] args){
        final List<String> list = new ArrayList<>();
        list.add("Changed!");
        System.out.println(list); // печатает [Changed!]
// list = new ArrayList<>(); // INVALID
    }
}
```

* Все интерфейсные члены являются имплицитно public ← ловушка на экзамене!&#x20;
* Любой интерфейсный метод, который не объявлен в явном виде как default или static, считается абстрактным.
* Интерфейс не может расширить класс, но ему разрешено расширять несколько интерфейсов одновременно.&#x20;
* Субинтерфейс наследует все абстрактные и default-методы, объявленные в его суперинтерфейсе (или суперинтерфейсах).&#x20;
* Класс не может расширить интерфейс, но зато имеет право имплементировать несколько интерфейсов, что тем самым позволяет воспользоваться преимуществами множественного наследования.&#x20;
* default-методы можно переопределять, abstract-методы как раз и созданы для того, чтобы их переопределяли, ну а static-методы переопределить вообще нельзя: они становятся скрытыми.

{% hint style="info" %}
Переопределяющий метод может быть абстрактным, что, в свою очередь, подразумевает, что класс-наследник обязан быть абстрактным.
{% endhint %}

{% hint style="success" %}
Интерфейсные static-методы очень удобны в роли ютилити, например, для сортировки, проверки на null, и т.п. → больше не надо вводить самостоятельные utility-классы.
{% endhint %}

{% hint style="success" %}
Интерфейсный static-метод можно вызывать только на имени его интерфейса.
{% endhint %}

Данное правило – вызов интерфейсного static-метода исключительно через имя его интерфейса – существует по многим причинам, и одна из них обусловлена необходимостью защиты информации (data security): ведь имплементирующие классы не смогут тогда переопределять такие методы, в противном случае JVM просто- напросто исполнит актайп-версию, как она это делает с классами.

```java
interface Inter { static void run(){ System.out.println("Inter"); } }
class Test implements Inter{
    public void run(){ System.out.println("Test"); }
    public static void main(String[] args) {
        Inter t = new Test();
// t.run(); // INVALID
        Inter.run(); // Inter
        ((Test)t).run(); // Test
    }
}
```

Да, но отчего же мы можем вызывать static-методы на объектных ссылках в классах, но не имеем права это делать с интерфейсами? Отвечает сам Брайан Гетц (Brian Goetz):

> Мы считаем, что возможность вызывать статический метод через экземпляр является ошибкой языкового дизайна, к сожалению, один, который мы не можем исправить задним числом для классов   \[ [http://stackoverflow.com/questions/34709082/illegal-static-interface-method-call](http://stackoverflow.com/questions/34709082/illegal-static-interface-method-call) ]

* От своего непосредственного суперкласса класс наследует все конкретные методы (как static, так и instance);&#x20;
* От своего непосредственного суперкласса и непосредственных суперинтерфейсов класс наследует все abstract- и default-методы;

Непереопределенные default-методы могут конфликтовать:

```java
interface I1 {
    default void run(){}
}
interface I2 {
    default void run(){}
}
// interface I3 extends I1, I2 {} // INVALID
interface I4 extends I1, I2 {
    default void run(){}
}
```

Класс не наследует static-методы, объявленные в суперинтерфейсах.

Подобно классам, интерфейсы тоже могут оказаться недоступными при обращении к ним извне пакета (это только их члены имплицитно считаются public) → будьте настороже, если код заглядывает в разные пакеты:

```java
package one;
interface Inter{}
package two;
        import one.*;
class Test implements Inter{} // INVALID: "Inter is not public in one,
                            // cannot be accessed from outside package"
```

ЕЩЁ РАЗ:

1. static-метод поверх non-static’а – это ВСЕГДА ошибка, то есть ВО ВСЕХ случаях: интерфейс-интерфейс, класс-класс или интерфейс-класс, причем по ВСЕЙ цепочке наследования (см.Примечание ниже).
2. Когда речь идет о переопределении между классами, static и non-static-методы НИКОГДА НЕ совместимы.&#x20;
3. ЛЮБОЕ иное переопределение валидно, КРОМЕ сочетаний ‛abstract static’, которое само по себе нарушает синтаксис.

{% hint style="info" %}
Памятка: Зато интерфейсный non-static-метод может «переопределить» супер- интерфейсный static-метод. (Это просто видимость переопределения, т.к. статические методы в интерфейсах попросту не наследуются).
{% endhint %}



```java
interface I{
    // static void run(){ System.out.println("Inter static"); }
// default void run(){ System.out.println("Inter default"); }
   static void run(){};
}
class Parent { // ***********************************
    public static void run(){ // * подлинный злодей живет здесь *
        System.out.println("Parent"); // ***********************************
    }
}
class Child extends Parent implements I { // INVALID: ’overriding method is static’
     //public static void run(){ // даже закомментировали, чтобы Child не имел
// System.out.println("Child"); // своего run()... и все равно унаследованный
// } // run() конфликтует с методом run() из I
    public static void main(String[] args) {
        new Child().run();
    }
}
```

Простые следствия:

* Субинтерфейс может заново объявить default-метод и даже сделать его абстрактным.&#x20;
* Субинтерфейс может заново объявить static-метод, но это не переопределение.&#x20;
* Между интерфейсами static-метод не может переопределять abstract-метод, зато обратное допустимо (это опять чистая видимость; @Override здесь будет ошибка компиляции).

Когда речь заходит о переменных, static может спрятать non-static, и наоборот.

ЕЩЕ РАЗ, под другим углом:

Поля и static-методы не подлежат переопределению, поэтому возможность доступа к полям и static-методам выясняется уже на этапе компиляции согласно типу переменной (в то время как instance-методы исполняются согласно фактическому типу объекта, на который ссылается данная переменная).&#x20;

Класс не может унаследовать два интерфейса, имеющих по default-методу с одинаковой сигнатурой, если только этот имплементирующий класс не переопределит конфликтующие методы своим абстрактным или конкретным методом.

Еще на тему разницы между static- и default-/ abstract-методами в интерфейсах:

Интерфейсы задают поведение, и это поведение наследуется только через non-static- методы (укороченная формулировка: <mark style="color:green;">интерфейсные static-методы не наследуются</mark>).

```java
interface Inter{
    static void method1(){}
    default void method2(){}
    void method3();
}
abstract class Parent implements Inter{
    public void method3(){}
}
class Child extends Parent{
    public static void main(String[] args) {
// method1(); // не валиден, зато Inter.method1() скомпилируется
        new Child().method2(); // VALID
        new Child().method3(); // VALID
    }
}
```

static-методы, объявленные классе Parent, исполняются, если рефтайп тоже Parent:

```java
class Parent {
    void one() { System.out.println("parent: one"); }
    static void two() { System.out.println("parent: two"); }
    public static void main(String[] args) {
        Parent p1 = new Parent();
        p1.one(); // parent: one
        p1.two(); // parent: two
// p1.three(); //<-- не видит
        Parent c1 = new Child();
        c1.one(); // child: one
        c1.two(); // parent: two
// c1.three(); //<-- не видит
// Child p2 = new Parent(); // требуется каст
// p2.one();
// p2.two();
        Child c2 = new Child();
        c2.one(); // child: one
        c2.two(); // child: two
        c2.three(); // child: three
    }
}
class Child extends Parent {
    void one() { System.out.println("child: one"); }
    static void two() { System.out.println("child: two");}
    void three() {System.out.println("child: three");}
}
```

### ТА ЖЕ ИСТОРИЯ С ИНТЕРФЕЙСАМИ:

```java
interface Parent {
    void zero();
    default void one() { System.out.println("parent: one"); }
    static void two() { System.out.println("parent: two"); }
}
class Child implements Parent {
    public void zero(){System.out.println("child: zero");}
    public void one() { System.out.println("child: one"); }
    static void two() { System.out.println("child: two"); }
    public static void main(String[] args) {
        Parent c1 = new Child();
        c1.zero(); // child: zero
        c1.one(); // child: one
// c1.two(); // этот некорректен, зато следующий скомпилируется
        Parent.two(); // parent: two
        Child c2 = new Child();
        c1.zero(); // child: zero
        c2.one(); // child: one
        c2.two(); // child: two
    }
}
```

**В ПОСЛЕДНИЙ РАЗ:**&#x20;

### <mark style="color:green;">**рефтайп**</mark> <mark style="color:blue;">**определяет,**</mark> <mark style="color:green;">**какие методы и поля доступны**</mark>** **<mark style="color:blue;">**тому или иному**</mark>** **<mark style="color:green;">**объекту**</mark><mark style="color:blue;">**, в то время как**</mark>** **<mark style="color:yellow;">**актайп**</mark> <mark style="color:orange;">**выбирает конкретную версию**</mark><mark style="color:blue;">**,**</mark>** **<mark style="color:red;">**КРОМЕ полей**</mark><mark style="color:blue;">**:**</mark>** **<mark style="color:green;">**поля ВСЕГДА**</mark>** **<mark style="color:blue;">**берутся**</mark>** **<mark style="color:green;">**из рефтайпа**</mark><mark style="color:blue;">**.**</mark>

Следствие: Когда объявленная в интерфейсе переменная НЕ СКРЫТА имплементирующим классом, мы не можем изменить ее значение (просто оттого, что она имплицитно final → комперр)&#x20;

Допустим:

1. класс Parent объявил int a = 0;
2. класс Child объявил int a = 100;

```java
Parent p = new Child();
System.out.println(p.a); // 0
System.out.println(((Child)p).a); // 100
Child c = new Child();
System.out.println(c.a); // 100
System.out.println(((Parent)p).a); // 0
Parent obj = new Parent();
System.out.println(obj.a); // 0
System.out.println(((Child)obj).a); // CCE на этапе исполнения
```

Это же относится и к интерфейсам, правда, с поправкой на тот факт, что их нельзя инстанцировать.
