## Iterator Pattern

### Definition:
```
The Iterator Pattern provides a way to access the elements of an aggregate object sequentially 
without exposing its underlying representation.

```

### Example

```java

public class DinerMenuIterator implements Iterator {	MenuItem[] items;	int position = 0;
		public DinerMenuIterator(MenuItem[] items) {		this.items = items;	}
		public Object next() {		MenuItem menuItem = items[position];		position = position + 1;		return menuItem;	}
		public boolean hasNext() {		if (position >= items.length || items[position] == null) {			return false;		} else {			return	 true;		}							}}

```

### Class Diagram:
![alt text](./IteratorPatternClassDiagram.jpeg "Class Diagram")

### Design Principle: Single Responsibility
```
A class should have only one reason to change.
```
* class is an area of potential change. More than one responsibility means more than one area of change.
* This principle guides us to keep each class to a single responsibility.

### Nested structures
This is where the [composite pattern](https://github.com/VanausloosThomas/PersonalDevelopment/blob/master/knowledge/DesignPatterns/CompositePattern.md) comes in!
### Bullet Points:
### Vragen/opmerkingen:
* Iterator helpt ons met loose-coupling tussen onze client en de implementatie van collecties! This makes the client easyer to extend!
* All of the java collection implementations have a build-in iterator!
* De for-each loop gebruikt achterliggend de iterator!

```java

for (Object o : collection){

}

```
* Gebruik maken van generics om geen Object te moeten terug geven in de next() methode!!

TESTEN OF DIT WERKt VOOR VERSCHILLENDE TYPES! (p328)

```java

public interface Iterator<T>{

	boolean has next();

	T next();
}

```
