# Inner classes

запрещено декларирование статических членов&#x20;

![](<../../.gitbook/assets/image (383).png>)

Любая переменная, определенная в методе и доступ к которой осуществляется анонимным внутренним классом, должна быть окончательной. Или, как [говорит Oracle](https://docs.oracle.com/javase/tutorial/java/javaOO/anonymousclasses.html#accessing):

> "Анонимный класс не может получить доступ к локальным переменным в своей области охвата, которые не объявлены как `final`или эффективно final"

Примечание: "эффективно окончательный" - это нечто новое, введенное в Java SE 8. Он определяется как переменная или параметр, который не объявлен как окончательный, значение которого никогда не изменяется после его инициализации.

Но зачем делать так, чтобы внутренние классы не могли изменять переменные, принадлежащие их внешней области видимости?

Причина в том, что внутренний класс "захватывает" переменную.

Чтобы понять, почему это важно, нам нужно понять, как работают захваченные переменные. Если вы знакомы с закрытиями, то это именно то, что здесь происходит.Внутренний класс-это замыкание. Он копирует переменную из области охвата в новую переменную и переносит только эту копию во внутренний класс. Все, что он делает с этой копией, не зависит от переменной в области охвата. Таким образом, если переменная изменяется во внутреннем классе, а затем используется позже во включающей области, изменения, внесенные во внутреннем классе, не сохраняются во включающей области.\
По сути, то, что происходит во внутреннем классе, остается во внутреннем классе.
