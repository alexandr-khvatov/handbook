# Декартово произведение

Декартово произведение:

```java
package com.company;

import java.util.Arrays;
import java.util.List;

public class Main {

    public static void main(String[] args) {

        /**
         * Декартово произведение 2-х коллекций
         */

        List<Integer> l1 = Arrays.asList(304, 561, 855, 4, 973, 597, 338);
        List<Integer> l2 = Arrays.asList(549, 689, 616, 682, 486, 131, 517);
        var start = System.currentTimeMillis();
        System.out.println(Arrays.deepToString(l1.stream()
                .flatMap(i -> l2.stream().map(j -> new int[]{i, j}))
                .toArray()));
        System.out.println("Time:    " + (float) (System.currentTimeMillis() - start) / 1000);

        /**
         * ************************************************************************************
         */
    }
}
```

![](<../../.gitbook/assets/image (146).png>)

{% embed url="https://onlinegdb.com/BZb8QY2xY" %}
