# ConcurrentHashMap

Использовать когда много операций чтения, но мало записи, т.к при большом количестве блокировок, производительность будет на равне с HashTable и synchronizedMap.

Синхронизация на уровне сегментов - блокируется доступ к одному элементу.

не допускает null K и V.

**Constructors of ConcurrentHashMap**

* **Concurrency-Level:** It is the number of threads concurrently updating the map. The implementation performs internal sizing to try to accommodate this many threads.
* **Load-Factor:** It’s a threshold, used to control resizing.
* **Initial Capacity:** Accommodation of a certain number of elements initially provided by the implementation. if the capacity of this map is 10. It means that it can store 10 entries.
