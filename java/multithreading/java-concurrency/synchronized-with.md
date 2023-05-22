# synchronized-with

{% embed url="https://docs.oracle.com/javase/specs/jls/se7/html/jls-17.html#jls-17.4.4" %}

Synchronization order (порядок синхронизации, но лучше не переводить) — общий порядок всех действий по синхронизации в выполнении программы.

Действия по синхронизации вводят связь **synchronized-with** (синхронизировано с):

* Действие освобождения блокировки монитора _synchronizes-with_ все последующие действия по взятию блокировки этого монитора.
* Присвоение значения volatile переменной _synchronizes-with_ все последующие чтения этой переменной любым потоком.
* Действие запуска потока synchronizes-with с первым действием внутри запущенного потока.
* Присвоение значения по умолчанию (0, false, null) каждой переменной _synchronizes-with_ с первым действием каждого потока.
* Последнее действие в потоке synchronizes-with с любым действием других потоков, которые [проверяют, что первый поток завершился](https://urvanov.ru/2016/05/27/java-8-%D0%BC%D0%BD%D0%BE%D0%B3%D0%BE%D0%BF%D0%BE%D1%82%D0%BE%D1%87%D0%BD%D0%BE%D1%81%D1%82%D1%8C/#joins).
* Если поток 1 [прерывает поток 2](https://urvanov.ru/2016/05/27/java-8-%D0%BC%D0%BD%D0%BE%D0%B3%D0%BE%D0%BF%D0%BE%D1%82%D0%BE%D1%87%D0%BD%D0%BE%D1%81%D1%82%D1%8C/#interrupts), то прерывание выполнения потока 2 synchronizes-with с любой точкой, где другой поток (и прерывающий тоже) проверяет, что поток 2 был прерван ( InterruptedException, Thread.interrupted, Thread.isInterrupted).
