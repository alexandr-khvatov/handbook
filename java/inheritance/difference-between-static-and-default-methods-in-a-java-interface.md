# difference between static and default methods in a Java interface?

Различия между статическими методами и методами по умолчанию в Java 8:

* Методы по умолчанию **могут быть** переопределены в классе реализации, в то время как статические-**нет**.
* Статический метод принадлежит **только** классу интерфейса, поэтому вы можете вызывать статический метод только в классе интерфейса, а не в классе, реализующем этот интерфейс, см.:

```java
public interface MyInterface {
    default void defaultMethod(){
        System.out.println("Default");
    }

    static void staticMethod(){
        System.out.println("Static");
    }
}

public class MyClass implements MyInterface {

    public static void main(String[] args) {

        MyClass.staticMethod(); //not valid - static method may be invoked on containing interface class only
        MyInterface.staticMethod(); //valid
    }
}
```

* И класс, и интерфейс **могут иметь** статические методы с одинаковыми именами, и ни один из них не переопределяет другой!

```java
public class MyClass implements MyInterface {

    public static void main(String[] args) {

        //both are valid and have different behaviour
        MyClass.staticMethod();
        MyInterface.staticMethod();
    }

    static void staticMethod(){
        System.out.println("another static..");
    }
}
```

Иначе сказано:

**статический метод** в интерфейсе:

* Вы можете вызвать его напрямую (InterfacetA.staticMethod())
* Подкласс не сможет переопределить.
* Подкласс может иметь метод с тем же именем, что и staticMethod

**метод по умолчанию** в интерфейсе:

* Вы не можете назвать это напрямую.
* Подкласс сможет переопределить его

**Преимущество:**

* **статический метод:** Вам не нужно создавать отдельный класс для служебного метода.
* **метод по умолчанию:** Предоставьте общие функциональные возможности в методе по умолчанию.
