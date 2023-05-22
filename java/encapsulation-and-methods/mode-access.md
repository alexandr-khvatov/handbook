# Mode access

## PUBLIC

<mark style="color:green;">**Доступен всем**</mark>

## PROTECTED

#### [<mark style="color:green;">**Доступен внутри пакета, а наследникам и за пределами пакета**</mark>** (click me)**](mode-access.md#protected-1)

## DEFAULT

<mark style="color:green;">**Доступен внутри пакета**</mark>

## PRIVATE

<mark style="color:green;">**Доступен внутри класса**</mark>

![](<../.gitbook/assets/image (453).png>)

![](<../.gitbook/assets/image (68).png>)

![](<../.gitbook/assets/image (353).png>)

```java
package modeAccess;

public class ModeAccess {
    public int pub;
    protected int prot;
    int def;
    private int priv;
}
```

```java
package org.example;

import modeAccess.ModeAccess;

public class Main {

    public static void main(String[] args) {
        ModeAccess modeAccess = new ModeAccess();
        System.out.println(modeAccess.pub);
        System.out.println(modeAccess.prot);// 'prot' has protected access in 'modeAccess.ModeAccess'
        System.out.println(modeAccess.def);// 'def' is not public in 'modeAccess.ModeAccess'. Cannot be accessed from outside packag
        System.out.println(modeAccess.priv);// 'priv' has private access in 'modeAccess.ModeAccess'
        

    }
}
```

#### PROTECTED&#x20;

```java
package modeAccess;

public class ModeAccess {
    public int pub;
    protected int prot;
    int def;
    private int priv;
}
```

```java
package org.example;

import modeAccess.ModeAccess;

public class Main extends ModeAccess { // extends

    public static void main(String[] args) {
        Main children = new Main();   // children instance
        System.out.println(children.pub);
        System.out.println(children.prot); // SUCCESS ACCESS
        
        ModeAccess notChildren = new Main();
        System.out.println(notChildren.pub);
        System.out.println(notChildren.prot); // DENIED ACCESS !!!
    }
}
```
