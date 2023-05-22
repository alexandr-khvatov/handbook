# Filter-Distinct

```java
package com.company;

import java.util.ArrayList;
import java.util.List;
import java.util.Map;
import java.util.Objects;
import java.util.concurrent.ConcurrentHashMap;
import java.util.function.Function;
import java.util.function.Predicate;

public class DistinctFilter {

    // this is stateful Predicate
    static <T> Predicate<T> distinktByKey(Function<? super T, ?> keyExtractor) {
        Map<Object, Boolean> seen = new ConcurrentHashMap<>();
        return dog -> seen.putIfAbsent(keyExtractor.apply(dog), Boolean.TRUE) == null;
    }

    public static void main(String[] args) {
        Dog white = new Dog("White", 2);
        Dog fluffy1 = new Dog("Fluffy", 4);
        Dog spot = new Dog("Spot", 19);
        Dog fluffy2 = new Dog("Fluffy", 1);

        List<Dog> dogs = new ArrayList<>();
        dogs.add(white);
        dogs.add(fluffy1);
        dogs.add(spot);
        dogs.add(fluffy2);

        dogs.stream()
                .distinct()
                .forEach(System.out::println);
        System.out.println("*****************************");
        dogs.stream()
                .filter(distinktByKey(Dog::getName))
                .forEach(System.out::println);
    }
}

class Dog {
    private String name;
    private int age;

    Dog(String color, int age) {
        this.name = color;
        this.age = age;
    }

    public String getName() {
        return name;
    }

    @Override
    public boolean equals(Object o) {
        if (this == o) return true;
        if (o == null || getClass() != o.getClass()) return false;
        Dog dog = (Dog) o;
        return age == dog.age && Objects.equals(name, dog.name);
    }

    @Override
    public int hashCode() {
        return Objects.hash(name, age);
    }

    @Override
    public String toString() {
        return "Dog{" +
                "color='" + name + '\'' +
                ", age=" + age +
                '}';
    }
}
```

![](<../../.gitbook/assets/image (266).png>)
