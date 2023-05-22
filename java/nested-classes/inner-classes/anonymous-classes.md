# Anonymous classes

Анонимный класс - это возможность совместить описание и создание единого(одного) объекта этого класса.

Ермаков\*: анон. класс нужен для того, чтобы переопределить некий метод.

#### **Применение анонимных классов**:

* Шаблон event subscribe:  listener реализующий некий интерфейс&#x20;

```java
switcher.addElectricityListener(new ElectricityConsumer() { // ElectricityConsumer - interface
        @Override
        public void electricityOn() {
        System.out.println("air conditioning on");
    }
});

// or lambda syntax
switcher.addElectricityListener(() -> System.out.println("air conditioning on"));
```

* Шаблон адаптер
* Собственный компаратор: переопределить compare
