# CopyOnWriteArrayList

Для чтения используется ребро HB (happens before), блокировка(синхронизация, Reentrant Lock ) нужна только для предоставления эксклюзивного доступа записывающим потокам.

![](<../../../.gitbook/assets/image (254).png>)

![](<../../../.gitbook/assets/image (241).png>)
