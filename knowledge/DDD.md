# Domain Driven Design

This is a summary of the DDDquicky book by  Floyd Marinescu.

### Questions

Whats in the applicaton layer? Are this services???
```
An application layer
is necessary in many cases. There has to be a manager over the
business logic which supervises and coordinates the overall
activity of the application
```

 Try to figure out how the following layers correspond to our application at the VDAB.
* User Interface
* Application Layer
    This is where the application logic lives. Application logic mostly uses behavior of many domain objects to express business logic.
    In the application layer we dont we will orchastrate a certain application behavior and mostly have connections to the infrastructure layer to persist state in the database.
* Domain Layer
    This is where the domain classes and concepts live
* Infrastructure Layer
    Here is everything related to infrastructure like for example mannaging storage and retrieval of the database.


### Services
Application layer service => application logic, these services encapsulate mostly a repository

Domain layer service => a service responsible for business logic processes

### Agregates

```
An Aggregate is a group of
associated objects which are considered as one unit with regard
to data changes.
```

The aggregate can ensure data integrity by not exposing references to its encapsulated objects. Objects outside the aggregate can only obtain a reference to the aggregate itself. All those objects can do is make changes on the aggregate itself or ask the aggregate to perform some changes.
When a root is deleted all the objects it contains are also deleted since there is no longer an object holding a reference to them.
When anything on the root changes that has effect on objects encapsulated in the root the root takes care of the invariance. The fact that there are no external objects holding references to the internal objects of the aggregate root makes this a lot easyer!
For this to work we will need to pass copies of the internal objects when someone asks the root object for them. This will result in immutable getters on the level of our root!
=> make static analsis tests to check this!

When the internal objects of the root are stored in a database, only the root should be obtainable by querries. The internal objects should follow in a transitive way.

References to other aggregates should be allowed in the internals of an aggregate.

The aggregate consists of entities and value objects. Choose one entity to be the root and that root will control acces to all other entities and value objects.

### Factories

To encapsulate the knowledge of creating a domain object (especially an aggregate) we use factories. Typically when an aggregate needs to be created all its internal objects need to be created aswell so that all of the invariants are inforced at the time of creation.
* Maybe we could use TestFactories instead of persistable testbuilders. 
* Why choose for static builders instead of factories? Because it makes making mappers easyer? Make mapping a part of some factories? But then where will the factories end...

Since the factory will be responsible for the creation of the aggregate root, it has a place inside our domain layer!

There are two common options for factories: 
1. The static factory or factory method. 
    The aggregate itself offers a method for its creation
2. A concrete factory class.
    Used when there is alot of logic involved in creating the aggregate and its internal objects. We dont want this logic embedded in all the objects so we encapsulate it in a factory object.

Sometimes a factory is to complicated. We can use a constructor when:
* The construction is not complicated
* The creation of the object does not involve the creation of other objects.
* All arguments needed for the creation can be passes to the constructor.
* When the calling client is interested in the implementation, for example wants to choose the Strategy being used. 

(why cant this be done in a factory?? Because the factory will need to know about the possible stategies?)

* The class is the type being created. There is no hyierchy of concrete implementations.

### Repositories

Where factories take care of object creation, repositories take care of its archivation or persistance.

Repositories encapsulate all everything needed to connect to the infrastructure level. This way the domain does not needt to know the underlying database. The repository can also use a certain strategy for its persistance. 

It is adviced to make a repository for each aggregate. This makes sure the client stays focussed on the model.
Although the repository can and probalbly will contain detailed information to acces the database infrastructure, it's interface should be very simple!

The repository can not only contain a set of methods for saving and retrieving objects based on certain criteria, it can also offer some utility methods to for example calculate the amount of objects of a certain type.

It can be noted that the implementation of a repository can be
closely liked to the infrastructure, but that the repository
interface will be pure domain model.