# PartitionBy

```java
package com.company;

import java.util.Arrays;
import java.util.List;
import java.util.Map;
import java.util.stream.Collectors;

public class PartitionBy {
    public static void main(String[] args) {
        List<Integer> integers = Arrays.asList(638, 819, 326, 984, 980, 108, 326);

        Map<Boolean, List<Integer>> map = integers.stream()
                .collect(Collectors.partitioningBy(n -> n > 500));
        System.out.println(map);
        System.out.println("***********************");
        System.out.println("Values:");
        map.forEach((k, v) -> System.out.println(v));
        System.out.println("***********************");

        System.out.println("***********************");
        System.out.println("Values:");
        map.entrySet().forEach(System.out::println);
        System.out.println("***********************");
    }
}
```

![](<../../.gitbook/assets/image (317).png>)
