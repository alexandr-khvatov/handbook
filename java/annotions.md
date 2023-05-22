---
description: >-
  Аннотации - форма метаданных, предоставляет данные о программе, которые не
  являются частью самой программы. Аннотации не оказывают прямого влияния на
  работу кода, который они аннотируют.
---

# @Annotions

Annotations have a number of <mark style="color:orange;">uses</mark>, among them:

* <mark style="color:yellow;">**Information for the compiler**</mark> — Annotations can be used by the compiler to detect errors or suppress warnings.
* <mark style="color:yellow;">**Compile-time**</mark>** and deployment-time processing** — Software tools can process annotation information to generate code, XML files, and so forth.
* <mark style="color:yellow;">**Runtime processing**</mark> — Some annotations are available to be examined at runtime.
* <mark style="color:blue;">@Override -</mark> указывает, что метод переопределяет, объявленный в суперклассе или интерфейсе метод.
* <mark style="color:blue;">@Deprecated -</mark> помечает код, как устаревший.
* <mark style="color:blue;">@SafeVarargs -</mark> указывает, что никакие небезопасные действия, связанные с параметром переменного количества аргументов, недопустимы. Применяется только к методам и конструкторам с переменным количеством аргументов, которые объявлены как **static** или **final**. &#x20;
* <mark style="color:blue;">@SuppressWarnings  -</mark> отключает для аннотированного элемента предупреждения компилятора. Обратите внимание, что если необходимо отключить несколько категорий предупреждений, их следует добавить в фигурные скобки, например @SuppressWarnings ({"unchecked", "cast"}).
* <mark style="color:blue;">@FunctionalInterface</mark>  - помечает интерфейсы, имеющие только один абстрактный метод (<mark style="color:orange;">при этом они могут содержать любое количество методов по умолчанию или статическиx</mark>)
* [@Native](https://docs.oracle.com/en/java/javase/15/docs/api/java.base/java/lang/annotation/Native.html) -  указывает, что аннотированное поле является константой, на которую можно ссылаться с нативного кода.

```java
public final class Integer {
    @Native public static final int MIN_VALUE = 0x80000000;
    // последующий код опущен
}
```

Annotation for annotation:

*   <mark style="color:purple;">@Retention  -</mark> определяет, как отмеченная аннотация может храниться — в исходном коде(<mark style="color:yellow;">RetentionPolicy.SOURCE</mark> )<например,Lombok>, в скомпилированном  классе(<mark style="color:yellow;">RetentionPolicy.CLASS</mark>) или во время работы кода(<mark style="color:yellow;">RetentionPolicy.RUNTIME</mark>).&#x20;

    Аннотация @Retention позволяет указать жизненный цикл аннотации: будет она присутствовать только в исходном коде, в скомпилированном файле, или она будет также видна и в процессе выполнения. Выбор нужного типа зависит от того, как вы хотите использовать аннотацию, например, генерировать что-то побочное из исходных кодов, или в процессе выполнения стучаться к классу через **reflection**.&#x20;
* <mark style="color:purple;">@Target -</mark> _@Target_ определяет контекст, для которого она применима. ([<mark style="color:blue;">click me</mark>](annotions.md#kontekst-primenimosti-target))
* <mark style="color:purple;">@Documented -</mark> по умолчанию аннотации не включаются в _javadoc_. Аннотация, помеченная _@Documented_ информирует, что такая аннотация должна быть задокументирована с помощью инструмента _javadoc_.
* <mark style="color:purple;">@Inherited</mark>
* <mark style="color:purple;">@Repeatable</mark>&#x20;



#### Контекст применимости @Target:

* **ElementType.ANNOTATION\_TYPE**: применяется для определения другой аннотации
* **ElementType.CONSTRUCTOR**: применяется для определения конструктора
* **ElementType.FIELD**: применяется для определения поля, включая константы Enum
* **ElementType.LOCAL\_VARIABLE**: применяется для определения локальной переменной
* **ElementType.METHOD**: применяется для определения метода
* **ElementType.MODULE**: применяется для определения модуля (с Java 9)
* **ElementType.PACKAGE**: применяется для определения пакета
* **ElementType.PARAMETER**: применяется для определения параметра
* **ElementType.TYPE**: применяется для определения класса, интерфейса (включая аннотируемый тип), Enum или record.
* **ElementType.TYPE\_PARAMETER**: применяется для определения типа параметра (с Java 8)
* **ElementType.TYPE\_USE**: применяется для определения используемого типа (с Java 8)
* **ElementType.RECORD\_COMPONENT**: ассоциируется с records как компонент записи (с Java 14)

[_ElementType_](https://docs.oracle.com/en/java/javase/15/docs/api/java.base/java/lang/annotation/ElementType.html) представляет собой _Enum_, обеспечивая простую классификацию возможных мест для размещения аннотаций в коде. В свою очередь, они делятся на контексты объявления, где аннотации применяются к объявлениям, и на контексты типов, где аннотации применяются к типам, используемые в объявлениях и выражениях.\
Константы ANNOTATION\_TYPE, CONSTRUCTOR, FIELD, LOCAL\_VARIABLE, METHOD, PACKAGE, MODULE, PARAMETER, TYPE и TYPE\_PARAMETER соответствуют контекстам объявления. TYPE\_USE соответствует контекстам типа, а также двум контекстам объявления: объявлениям типов (включая объявления типов аннотаций) и объявлениям параметров типа.\
Например, аннотация, тип которой аннотирован с помощью _@Target (ElementType.FIELD)_, может быть записан только как модификатор для объявления поля. В тоже время аннотация, тип которой аннотирован с помощью _@Target (ElementType.TYPE\_USE)_, может быть записана в типе поля, а также может выступать в качестве модификатора, например, для объявления класса.
