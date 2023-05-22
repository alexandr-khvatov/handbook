# JAVA concurrency

Каждый поток связан с экземпляром класса [`Thread`](https://docs.oracle.com/javase/8/docs/api/java/lang/Thread.html). Существует две основные стратегии использования `Thread`объектов для создания параллельного приложения.

* Чтобы напрямую управлять созданием и управлением потоками, просто создавайте экземпляр `Thread`каждый раз, когда приложению необходимо инициировать асинхронную задачу.
* Чтобы абстрагировать управление потоками от остальной части приложения, передайте задачи приложения _исполнителю_.

[https://docs.oracle.com/javase/tutorial/essential/concurrency/threads.html](https://docs.oracle.com/javase/tutorial/essential/concurrency/threads.html)

![](<../../.gitbook/assets/image (60).png>)

JVM - завершает работу, не когда завершается поток Main, а когда завершаются все остальные потоки не demon.
