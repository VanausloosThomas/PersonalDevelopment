# Design patterns

1. Decorator (Paulien & Steven)
2. Strategy (Sanne & Jens)
3. Singleton (Christoph & Rodrigo)
4. Iterator (Elise & Xan)
5. Composite (Elise & Xan)
6. Observer (Sophie & Wouter)
7. MVC (Roel & William)
8. Template (Kevin & Kevin)
9. Factory (Stijn & Thomas)
10. Filter/Criteria (Marijn & David)
11. Flyweight (Dieter & Pieter)
12. Adapter (Dieter & Pieter)
13. Builder

## Excercises
Before you start on the excercises try to classify the 12 design patterns.

Creational patterns:
1. 
2. 
3. 

Structural Patterns:
1. 
2. 
3. 
4. 
5. 

Behavioral Patterns:
1. 
2. 
3. 
4. 

Architectural Patterns:
1. 


###Excercise 1
Create a class Car with the following fields:
* Model name
* Year
* Brand
* Horse power
* Engine
* Transmission type
* Vin
* License plate
* Dedicated driver
* Color

which creational pattern should we use in this case?

### Excercise 2
Create a class Book with the following fields:
* ISBN
* Title
* Author

Throw a validation exception when one of those fields are empty.

Which creational pattern should we use in this case?
Why isn't this a complete fit?

Could you add some code to make it a better example of this pattern?

### Excercise 3
Create a class Counter.
This should contain a method add() that will add 1 to an int.
Make a method on Counter that prints the current number.
This Counter should be shared over all classes.
Which creational pattern should we use ?
Try to initialise it lazily.

### Excercise 4
When ordering a Cruise you can add some packages:
* All inclusive
* Spa
* Massage
* Excursion
* Fitness
* Better restaurant
* Cuban cigar package

At the end of your yourney they will print a detailed list about your packages and have your total sum.

Which Structural pattern would we use?

### Excercise 5
You have 3 classes that you cannot change:
* Car with a method fillMeUp();
* Bus with a method fillMeAlready();
* Truck with a method fillMeSlowImOnABreak();

Create ServiceStation class that has only 1 method and can fill the 3 vehicles.
**No inheritance!**

Which Structural pattern would we use?

### Excercise 6
Create a family tree.

Which Structural pattern would we use?

### Excercise 7
Make sure we can do a foreach loop over the family tree so that we can print all the names.

Which Structural pattern would we use?

### Excercise 8
To add a pet into the system a user can type in the Name of the pet, the type of a pet, the name of the owner and the INSS of the owner. 
Create a service that has these strings as in input and the pet as an output. 
Because of memory constraints we don't want to create an Owner for all the pets.


Which Structural pattern would we use?
Are we using an Creational pattern? Which one and why? 

### Excercise 9
Make a large list of books. Find a way so that we can ask for all SciFi books and from an author.
Which Behavorial design pattern would we use?
What is the connection with streams?

### Excercise 10
Create a class BookRepository that accepts new books. Whenever a book has been added or removed from the repository we want to do 3 things. 
1. Print a text in the console
2. Save the repository to disk (fake this by doing a sout saved to disk)
3. Send an email (fake this by doing a sout email send)

This could be extended in the near future.

Which Behavorial pattern would we use?

### Excercise 11
Calculate the rental rate for the next movies:
* Regular: 1 euro
* New : 5 euro
* Trending : 3 euro
* Classics : 0.5 euro

You can do this with 2 different Behavorial design patterns. Try them both!
Which one do you think is the better one? Why?