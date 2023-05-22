# Инъекция с @Resource

Spring также поддерживает внедрение с помощью аннотации JSR-250 `@Resource`(`javax.annotation.Resource`) для полей или методов набора свойств компонентов. Это распространенный шаблон в Java EE: например, в компонентах, управляемых JSF, и конечных точках JAX-WS. Spring также поддерживает этот шаблон для объектов, управляемых Spring.

`@Resource` принимает атрибут имени. По умолчанию Spring интерпретирует это значение как имя компонента, которое будет введено. Другими словами, он следует семантике имени, как показано в следующем примере:

```java
public class SimpleMovieLister {

    private MovieFinder movieFinder;

    @Resource(name="myMovieFinder") 
    public void setMovieFinder(MovieFinder movieFinder) {
        this.movieFinder = movieFinder;
    }
}
```

Если имя явно не указано, имя по умолчанию является производным от имени поля или метода настройки. В случае поля оно принимает имя поля. В случае метода сеттера он принимает имя свойства компонента. В следующем примере компонент с именем `movieFinder`будет введен в метод установщика:

```java
public class SimpleMovieLister {

    private MovieFinder movieFinder;

    @Resource
    public void setMovieFinder(MovieFinder movieFinder) {
        this.movieFinder = movieFinder;
    }
}
```
