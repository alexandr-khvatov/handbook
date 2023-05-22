---
description: '[ Из спецификации] : Блокам инициализации доступна вся мощь языка.'
---

# Initializer blocks \[ static, non-static]

### Порядок отработки блоков инициализации:

* <mark style="color:green;">**static blocks,**</mark>
* <mark style="color:green;">**non - static blocks,**</mark>
* <mark style="color:green;">**constructor**</mark>

```java
public class Main {

    public static void main(String[] args) {
        new A();
        System.out.println("___________________________________________________________");
        new A();
    }
}

class A {
    int a;

    {
        System.out.println("non - static blocks initializer");
    }

    static {
        System.out.println("static blocks initializer");
    }

    {
        System.out.println("non - static blocks initializer 2");
    }

    static {
        System.out.println("static blocks initializer 2");
    }

    A() {
        System.out.println("constructor");
    }
}
```

![](<../.gitbook/assets/image (276).png>)

```java
public class Main {

    public static void main(String[] args) {
        new A();
        System.out.println("___________________________________________________________");
        new A();
    }
}

class A {
    static int a = run();

    {
        System.out.println("non - static blocks initializer");
    }

    static {
        System.out.println("static blocks initializer");
    }

    {
        System.out.println("non - static blocks initializer 2");
    }

    static {
        System.out.println("static blocks initializer 2");
    }

    static int run(){
        System.out.println("run!");
        return 11;
    }

    A() {
        System.out.println("constructor");
    }
}
```

![](<../.gitbook/assets/image (155).png>)

```java
public class Main {

    public static void main(String[] args) {
        new A();
        System.out.println("___________________________________________________________");
        new A();
    }
}

class A {

    {
        System.out.println("non - static blocks initializer");
    }

    static {
        System.out.println("static blocks initializer");
    }

    static int a = run();

    {
        System.out.println("non - static blocks initializer 2");
    }

    static {
        System.out.println("static blocks initializer 2");
    }

    static int run() {
        System.out.println("run!");
        return 11;
    }

    A() {
        System.out.println("constructor");
    }
}
```

![](<../.gitbook/assets/image (312).png>)

```java
public class Main {

    public static void main(String[] args) {
        new A();
        System.out.println("___________________________________________________________");
        new A();
    }
}

class A {

    {
        System.out.println("non - static blocks initializer");
    }

    static {
        System.out.println("static blocks initializer");
    }

     int a = run();

    {
        System.out.println("non - static blocks initializer 2");
    }

    static {
        System.out.println("static blocks initializer 2");
    }

     int run() {
        System.out.println("run!");
        return 11;
    }

    A() {
        System.out.println("constructor");
    }
}
```

![](<../.gitbook/assets/image (114).png>)
