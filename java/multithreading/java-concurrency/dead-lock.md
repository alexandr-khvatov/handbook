# Dead Lock

![](<../../.gitbook/assets/image (132).png>)

![](<../../.gitbook/assets/image (411).png>)

```java
     static void transfer(Queue<String> in, Queue<String> out) {
         synchronized (in) {
             synchronized (out) {
                 String res = in.poll();
                 if (res != null) {
                     out.add(res);
                 }
             }
         }
     }
```

![](<../../.gitbook/assets/image (113).png>)

```java
     Queue<String> in = new ArrayDeque<>(Arrays.asList("foo", "bar", "baz"));
     Queue<String> out = new ArrayDeque<>(Arrays.asList("foo", "bar", "baz"));
     Thread t1 = new Thread(() -> {
         for(int i=0; i<100000; i++) {
             System.out.println("Thread1: "+i);
             transfer(in, out);
         }
     });
     Thread t2 = new Thread(() -> {
         for(int i=0; i<100000; i++) {
             System.out.println("Thread2: "+i);
             transfer(out, in);
         }
     });
System.out.println("Started");
        t1.start();t2.start();
        t1.join(); t2.join();
        System.out.println("Finished");
```
