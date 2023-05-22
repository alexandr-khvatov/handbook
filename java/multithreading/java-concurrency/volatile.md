# volatile

[https://docs.oracle.com/javase/specs/jls/se7/html/jls-17.html#jls-17.4.5](https://docs.oracle.com/javase/specs/jls/se7/html/jls-17.html#jls-17.4.5)

по спецификации JVM  обязана, при изменении поля промаркированного VOLATILE, сообщить другим потокам о изменении соответствующего поля.

VOLATILE не дает JVM кэшировать и или выполнять различные оптимизации с этим полем.

Объявления переменной counter как volatile достаточно, когда один поток изменяет переменную, а другой поток читает ее значение. Если два потока изменяют общую переменную, то использования ключевого слова volatile недостаточно — будет race condition. Ключевое слово volatile гарантирует следующее:

1. <mark style="color:green;">Если первый поток записывает в volatile переменную, а затем второй поток читает значение из этой переменной, тогда все переменные, видимые потоку A перед записью в переменную volatile, также будут видны потоку B, после того как он прочитал переменную volatile.</mark>
2. Если поток A считывает переменную volatile, то все переменные, видимые потоку A при чтении переменной volatile, также будут перечитаны из основной памяти.

![](<../../.gitbook/assets/image (345).png>)

> ### Volatile - это свойство операции чтения и свойство операции записи, а не свойство поля.        \[ Тагир Валеев ]

![](<../../.gitbook/assets/image (202).png>)

## ПРИМЕР 1:

```java
package com.company.volatileLearn;

public class AVolatile {

    static volatile boolean run = true;
//    static boolean run = true;

    public static void main(String[] args) {

        new Thread(new Runnable() {
            @Override
            public void run() {
                while (run) ;
            }
        }).start();

        /**
         *  @param run
         *  при volatile точно остановится, при non - volatile - не очивидно,
         *  по спецификации может выполняться любое конечное время, или бесконечно
         */
        run = false;

    }
}
```

## ПРИМЕР 2:

```java
package com.company.volatileLearn;

public class Main {
    static  int i = 0;
//    static volatile int i = 0;


    public static void main(String[] args) throws InterruptedException {
        new ThreadRead().start();
        new ThreadWrite().start();
    }

    static class ThreadWrite extends Thread {
        @Override
        public void run() {
            while (i < 5) {
                System.out.println("increment i " + (++i));
                try {
                    Thread.sleep(1000);
                } catch (InterruptedException e) {
                    e.printStackTrace();
                }
            }
        }
    }

    static class ThreadRead extends Thread {
        @Override
        public void run() {
            int localI = i;
            while (localI < 5) {
                if (localI != i) {
                    System.out.println("        new value i " + i);
                    localI = i;
                }
            }
        }
    }
}
```

![](<../../.gitbook/assets/image (184).png>)

![](<../../.gitbook/assets/image (214).png>)

## ПРИМЕР 3:

![](<../../.gitbook/assets/image (123).png>)

## ПРИМЕР 4:

![](<../../.gitbook/assets/image (359).png>)

## ПРИМЕР 5:

![](<../../.gitbook/assets/image (306).png>)

## ПРИМЕР 6:

![](<../../.gitbook/assets/image (324).png>)

![](<../../.gitbook/assets/image (65).png>)

![](<../../.gitbook/assets/image (229).png>)

![](<../../.gitbook/assets/image (347).png>)

![](<../../.gitbook/assets/image (358).png>)

## ПРИМЕР 7:

![](<../../.gitbook/assets/image (137).png>)
