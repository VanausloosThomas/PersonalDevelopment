## Composite Pattern

### Definition:
```
The Composite Pattern allows you to compose objects into tree structures to represent 
part-whole hierarchies. Composite lets clients treat individual objects and compositions 
of objects uniformly.

```
* The Composite Pattern allows us to build structures of objects in the form of trees that contain both compositions of objects and individual objects as nodes.
* Using a composite structure, we can apply the same operations over both composites and individual objects. In other words, in most cases we can ignorethe differences between compositions of objects and individual objects.
* The Component is a general interface, containing default methods for both the leafs and composites. The leafs and composites override the methods that make sense for them and use the default implementation for those who dont! A typical default implementation would be to throw an UnsupportedOperationException. So if we were to call a method ment for a leaf on a composite we would get an exception back.


### Class Diagram:
![alt text](./CompositePatternClassDiagram.jpeg "Class Diagram")

### Example

Iterating over a composition:

```java


	
	
	
	

```
NullIterator:

```java

public class NullIterator implements Iterator {
	
	

```

### Bullet Points:


* Revieuw the iterating over a composition part
 