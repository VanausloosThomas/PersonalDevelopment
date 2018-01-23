## Command Pattern

### Definition:
```
The Command Pattern encapsulates a request as an object, thereby letting you parameterize other objects with different requests, queue or log requests, and support undoable operations.
```

### Class Diagram:

![alt text](./CommandPatternClassDiagram.jpeg "Class Diagram")

### Macro Commands:

```java

public class MacroCommand implements Command {



```

### Bullet Points:
* The Command Pattern decouples an object, making a request from the one that knows how to perform it.
* Invokers can be parameterized with Commands, even dynamically at runtime.

### Questions:
* If you store all your commands you could replay them. Is this how Event Driven Design works?
* When to chose to make an explicit command class and when to use a lamda (assuming the command contains only one method, otherwise the choise is fairly obvious).
* Encapsulate the receiver or handle the implementation of the command in the command itself?