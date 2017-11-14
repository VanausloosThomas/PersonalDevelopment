# Spring

### Configuration

1) Classpath scanning (using annotations to register beans)
2) Configuration inside (uses configfiles) 

### Adding beans to the IOC container

1) Using configuration files:

Register beans by returning a new instance of the object (the bean) in a by `@Bean` annotated method.
``` java
@Configuration
public class HelloWorldConfig {
   @Bean 
   public HelloWorld helloWorld(){
      return new HelloWorld();
   }
}
```

By using the `@Import` annotation we can import other config files. When in the example below we load the ApplicationConfig.class we also import all beans configured in the `HelloWorld` class, the `Blablabla` class and the `SomeOtherConfigFile` class!

``` java
@Import({HelloWorld.class, 
        Blalalala.class,
        SomeOtherConfigFile.class
        })
@Configuration
public class ApplicationConfig {
   
}
```


2) Using annotations on the beans class:
``` java 
@Named // or @Component, @Repository, @Service, ...
public class HelloWorld(){
    public HelloWorld(){

        //required by Spring to make the bean!!!
    }
}
```
## Spring Boot

1) Configuration
