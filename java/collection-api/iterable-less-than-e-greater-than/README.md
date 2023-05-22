# Iterable\<E>

* iterator()
* forEach(Consumer)

Iterable  - "обходимое", Iterator - "обходчик"

при собственной реализации Iterable , необходимо реализовать только метод iterator, остальные методы имеют дефолтную реализацию.

![](<../../.gitbook/assets/image (357).png>)

![](<../../.gitbook/assets/image (153).png>)

![](<../../.gitbook/assets/image (263).png>)

### Очень часто remove просто выбрасывает UnsupportedOperationException (UOE) - это означает, что remove не поддерживается, данный Iterator не может изменять нашу коллекцию ( в 8 java  remove() сделали default, который просто кидает UOE):

![](<../../.gitbook/assets/image (38).png>)

```java
    /**
     * Removes from the underlying collection the last element returned
     * by this iterator (optional operation).  This method can be called
     * only once per call to {@link #next}.
     * <p>
     * The behavior of an iterator is unspecified if the underlying collection
     * is modified while the iteration is in progress in any way other than by
     * calling this method, unless an overriding class has specified a
     * concurrent modification policy.
     * <p>
     * The behavior of an iterator is unspecified if this method is called
     * after a call to the {@link #forEachRemaining forEachRemaining} method.
     *
     * @implSpec
     * The default implementation throws an instance of
     * {@link UnsupportedOperationException} and performs no other action.
     *
     * @throws UnsupportedOperationException if the {@code remove}
     *         operation is not supported by this iterator
     *
     * @throws IllegalStateException if the {@code next} method has not
     *         yet been called, or the {@code remove} method has already
     *         been called after the last call to the {@code next}
     *         method
     */
    default void remove() {
        throw new UnsupportedOperationException("remove");
    }
```

при собственной реализации Iterator: необходимо реализовать HasNext() и next(),        remove() (если необходима поддержка удаления!!!)

если бы вместо проверки на равенство, была бы проверка на больше или равно то: могло бы возникнуть переполнение.

![](<../../.gitbook/assets/image (213).png>)

![](<../../.gitbook/assets/image (394).png>)
