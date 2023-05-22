# Императивный(процедурный) стиль - (как сделать?)

Описывается способ достижения цели.

Характерной чертой являются циклы и условные выражения.

**Imperative Approach:**

```java
    /*
     * find all managers of all departments with an employee older than 65
     */
    Manager[] find(Corporation c) {
        List<Manager> result = new ArrayList<>();
        for (Department d : c.getDepartments()) {
            for (Employee e : d.getEmployees()) {
                if (e.getAge() > 65) {
                    result.add(d.getManager());
                }
            }
        }
        return result.toArray(new Manager[0]);
    }
```
