# Static Method

###

{% hint style="danger" %}
### Статические методы наследуются, но участия в полиморфизме не принимают!  (JAVA 1.8)
{% endhint %}

Демонстрация наследования статических методов(JAVA 1.8):

```java
public class Main {
    final static private String secret = "BIG SECRET!";

    static private void secret() {
        System.out.println("SECRET! "+secret);
    }

    public static void main(String[] args) {
        secret();
    }
}


class A extends Main {
    static {
        System.out.println("Ляля - запускаем A.main()");
    }
}
```

![](<../.gitbook/assets/image (160).png>)

![](<../.gitbook/assets/image (284).png>)

{% hint style="danger" %}
### Не работает на интерфейсах
{% endhint %}

```java
public class Main {
    
    public static void main(String[] args) {
    Able.run();
    Bable.run(); // не скомпилируется
    }
}


interface Able {
    static void run(){
        System.out.println("is run");
    }
}

interface Bable extends Able{
}
```

![](<../.gitbook/assets/image (403).png>)
