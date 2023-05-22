# Замечания

## Одновременно нельзя  реализовать коллекцию с использованием интерфейсов Set и List, причина Equals и HashCode

Если два объекта равны по , то у них одинаковый Equals и HashCode.

Set-ы должны быть равны по Equals, даже если у них порядок разный. Следовательно, чтобы организовать hashCode для Set необходимо просуммировать HashCode все его элементов.

Однако такой HashCode для произвольной коллекции - плохой вариант! Может оказаться ситуация, что имеется много разных списков, которые отличаются только порядком элементов, в этом случае, если сделать для списка такой же hashCode, то он будет везде одинаковый и hashMap превратится в чёрт знает что - они не будут нормально работать, поэтому для списка hashCode работает примерно также как для строк: " через перебор и умножение на 31".  Суть в том что контракт hashCode для List и Set не совместим - это написано в документации.&#x20;

Хотя и можно скомпилировать AbstractList implements Set,  но он будет неправильным с точки зрения контракта, т.к. расширяли  AbstractList, то Equals и HashCode придут из списка тем самым контракт Set будет нарушен, у него и HashCode и Equals будет неправильный, Equals всегда вернет false.

Нужно делать отдельную реализацию List и Set.