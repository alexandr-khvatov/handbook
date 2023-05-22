# Overloaded Constructor

```java
class A {

    A(){
    }
    
    A( int a){
        this();
        
    }
}
```

```java
class A {

    A(){
        this(10);
    }

    A( int a){

    }
}
```

```java
class A {

    A(){          // compilation error:  Recursive constructor invocation
        this(10);
    }

    A( int a){    // compilation error:  Recursive constructor invocation
        this();

    }
}
```
