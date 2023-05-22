# final

![](<../../.gitbook/assets/image (289).png>)

> Если у Вашего объекта все поля final, то другие потоки видят гарантированно проинициализированные final  поля. \[ Тагир Валеев ]   с такими объектами можно не использовать volatile.

Если нужны изменяемые поля, необходима внешняя синхронизация

[https://docs.oracle.com/javase/specs/jls/se17/html/jls-17.html#jls-17.5](https://docs.oracle.com/javase/specs/jls/se17/html/jls-17.html#jls-17.5)
