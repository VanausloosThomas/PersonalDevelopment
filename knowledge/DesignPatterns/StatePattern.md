## State Pattern

### Definition:
```
The State Pattern allows an object to alter its behavior when its internal state changes.
The object will appear to change its class.

```

Design priciples used:

* Encapsulate what varies (the implementation of each method varies depending on the state we are in)
* Faver composition over inheritance (we will use composition withstate objects)


This means we will easely be able to add an other state when we want/need to.

### Usage
Where we use the stategy pattern as a flexible alternative to subclassing, we use the state pattern as alternative to using alot of conditionals in our context class. Changing the state object will (as with the strategy pattern) chance the behaviour of our context class.


### Class Diagram:
![alt text](./StatePatterClassDiagram.jpeg "Class Diagram")

### Example

Iterating over a composition:

```java

```

```java


```

### Bullet Points:

* The State Pattern allows an object to have many different behaviors that are based on its internal state.
* Het oproepen van een bepaalde methode in een state zorgt voor transitie naar de volgende state. Hiervoor moete de state implementaties van elkaar weten? Kan dit niet meer losgekoppeld worden?