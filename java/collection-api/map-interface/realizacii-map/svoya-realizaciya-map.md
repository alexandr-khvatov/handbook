# Своя реализация Map

Минимальная реализация Map:

![](<../../../.gitbook/assets/image (37).png>)

У AbstractMap необходимо реализовать методы iterator() и size()

У такой реализации ряд проблем с производительностью:

Во - первых  нужно реализовать contains...()

Если не переопределить метод containsKey(), то будет происходить следующее: будет реализация по умолчанию вызывать EntrySet и у него брать Iterator и идти по Map, сравнивая каждый элемент с тем, что передали - что НЕ ПРОИЗВОДИТЕЛЬНО!

Стоит containsKey() реализовать, например в этом случае вот -так по простому: + get()

![](<../../../.gitbook/assets/image (141).png>)
