# Типы ссылок

```java
class Link {
    public static void main(String[] args) {
        Object object = new Object(); // STRONG
        // SOFT
        SoftReference<Object> softReference = new SoftReference<>(object);
        //WEAK
        WeakReference<Object> weakReference = new WeakReference<>(object);
        
        ReferenceQueue<Object> referenceQueue = new ReferenceQueue<>();
        PhantomReference<Object> phantomReference = new PhantomReference<>(object, referenceQueue);
        
        System.out.println("Strong reference: " + object);
        System.out.println("Soft reference:" + softReference.get());
        System.out.println("Weak reference: " + weakReference.get());
        System.out.println("Phantom reference: " + phantomReference.get());
    }
}
```

* StrongRef - обычная создается при **new**&#x20;
* SoftReference - удаляется, если не хватит памяти\
  если softReference = null, через softReference.get() можно получить ссылку
* WeakReference - удаляется при первой чистке мусора
* PhantomReference - используется совместно с ReferenceQueue для проверки УДАЛЕНИЯ ОБЪЕКТА и выполнения каких либо действий при удалении
