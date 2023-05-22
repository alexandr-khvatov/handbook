# max Entry

```java
package com.company;

import java.util.Collections;
import java.util.Comparator;
import java.util.HashMap;
import java.util.Map;

class UniMax {
    static <K, V> Map.Entry<K, V> maxEntryByValue(Map<K, V> sourceMap, Comparator<V> comp) {
        return Collections.max(
                sourceMap.entrySet(),
                Map.Entry.<K, V>comparingByValue(comp));
    }

}

public class UniMaxDemo {
    public static void main(String[] args) {
        HashMap<String, Long> longs = new HashMap<>();
        longs.put("-10L", -10L);
        longs.put("10L", 10L);
        HashMap<String, Double> doubles = new HashMap<>();
        doubles.put("-10.0", -10.);
        doubles.put("10.0", 10.);


        System.out.println(UniMax.maxEntryByValue(longs, Long::compare)); // 10L =10
        System.out.println(UniMax.maxEntryByValue(doubles, Double::compare)); //10.0=10.0

    }
}
```

![](<../../.gitbook/assets/image (428).png>)
