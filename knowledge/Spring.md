# Spring in action

## 1) Dependency injection

Given some configuration, spring takes care of dependency injection. What is DI ? In every project there are classes that need other classes (or dependencies) for their internal working. We don't want our classes to know about the construction of their dependencies. This is where Spring and its dependency injection comes in. Spring will inject all the dependencies so that our classes can be loosly coupled.

There are three kinds of dependency injection:

**1. Constructor injection**
```java 
public class Example{

    private SomeClass dependency;

    @Inject
    public Example (SomeClass constructorDependency){
        this.dependency = constructorDependency;
    }
}
```
**2. Setter injection**
```java
public class Example{

    private SomeClass dependency;

    @Inject
    public void setDependecy (SomeClass setterDependency){
        this.dependency = setterDependency;
    }
} 
```
**3. Field injection**
```java
public class Example{

    @Inject
    private SomeClass dependency;

 } 
```
Field injection can only be achieved using reflection. We use the `@Inject` annotation to let Spring know this is where we expect a dependency to be injected of type `SomeClass`.
We will also use this annotation for setter- and constructorinjection!


### A. Wiring the beans:
The act of creating these associations between application objects is the essence of
dependency injection (DI) and is commonly referred to as wiring.

Sring offers us a feature called autowiring where spring will automaticly satisfy a beans dependencies. It will look for those dependencies in its own applicationcontext. This feature together with componentscanning (where spring automatically discovers beans to be created in its applicationcontext) helps keeping explicit configuration to a minimum.


### How does Spring inject dependencies?

* Application context
* Beans
* Configuration
    * XML
    * Java config
    * Annotations (automatic discovery)

Springs configuration can be mixed and matched to suit your own needs. Typically in modern applications we use annotation based configuration for beans we write ourselves and java config or xml config for third-party beans.


### B. The spring container

In spring, the container manages the applications beans, configures them, wires them and takes care of their creation and destruction.
Spring has many containes that can be categorised in two types: beanfactories and application contexts. Beanfactories are basic containers that support dependency injection. Applications contexts on the other hand are the combination of a bean factory and application-framework services such as reading application properties from a text file and publishing application events. When building applications the application context is mostly the preferred choice since a bean factory is to low level for most usages.

There are many different forms of initiating an application context. Some examples are the ClassPathXmlApplicationContext and the FileSystemXmlApplicationContext. Examples on how to startup these contextst can be found below: 

```java
ApplicationContext context = new
FileSystemXmlApplicationContext("c:/someConfigFile.xml");
```

```java
ApplicationContext context = new
ClassPathXmlApplicationContext("anotherConfigFileOnTheClasspath.xml");
```
We can also use javaconfiguration to tell our application where it can find its beans. This can be done using the AnnotationConfigApplicationContext. An instantiation example: 

```java
ApplicationContext context = new AnnotationConfigApplicationContext(
com.myapplication.mypackage.config.JavaConfig.class);
```
### The bean lifecle

Inside the spring container each bean goes through a lifecycle containing multiple steps:

1. TODO: make clear overview of lifecycle steps.


### C. Naming the beans

When we mark a class as a spring bean, spring will automatically give the bean an ID. The ID is the beans class-name, starting with a lowercase letter. For example the ID of `MyClass` would be `myClass`.
We can also pass the beans ID as an argument to the @Component of @Named annotations.
When using javaconfig the beans ID will be the name of the method providing that bean.

### D. Setting the base-package when classpath scanning

By default, spring uses the package of the configuration file as base-package for its classpath scanning. Since we might want to group our configuration files together in a config module, we need to be able to tell spring to use another base-package from where to start scanning. We can do this either by passing the `basePackages` or `basePackageClasses` attribute to the @ComponentScan annotation. When we want to pass multiple values we need to pass it as an array of Strings! This is refactor-unsafe. A way around this is to add an empty marker-class or marker-interface to the packages to be scanned and let that class be picked up with the `basePackageClasses` option. The advantage here is that the markers dont have any production code and won't be refactored.

### E. Annotating beans to be automatically wired.
Using the `@Autowired` annotation we can tell spring to satisfy the dependency. Spring will wire in a matching bean if there is one available in the application context. If there is no valid matching bean available, spring will throw an exeption. If we do not require spring to satisfy the dependency, we can make use of the required property of the annotation and set it to false.

The `@Autowired` annotation can be placed above fields, constructors and methods that take arguments.

An alternative to springs `@Autowired` annotation is the `@Named` annotaton of the Java Dependency Injection specification. Although both have subtle differenced, they are mostly interchangable! 

### Advanced Wiring

* Profile beans:

    Using the @Profile annotation we can tell spring which profile a bean belongs to. With this, spring can wire the appropriate bean depending on our currently selected profile. The annotation can both be used on the class level and on the method level (WHAT ABOUT IN COMBINATION WITH THE @COMPONENT OR @NAMED ANNOTATION?)

    Spring offers us two properties to set the active profile: spring.profiles.active and spring.profiles.default. Sring will fall back to the default profile if no active profile was set and will run without any profile if neither of the above properties are set. It is possible to activate multiple profiles at the same time by passing multiple names to the properties! 
    If we use profiles in our testst, we can manually activate them by annotating our test class with @ActiveProfiles("someProfilesName").

* Conditional beans:

    



## 2. Aspect Oriented Programming

Where dependency injection takes care of loose coupling of our classes, AOP promotes separation of concerns. 
AOP is typically used with cross cutting concerns. Cross cutting concerns are system services with functionality that can be used troughout our entire application. By using AOP we can group these concerns together and both avoid duplication of code trough the application and restore our single responsibility principle in our classes.    

## 3. Avoiding boiler plate code (templates)   




=======================To revise================================
## Bean Configuration

1) Classpath scanning (using annotations to register beans)
2) Configuration inside (uses configfiles) 

## Adding beans to the IOC container

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
