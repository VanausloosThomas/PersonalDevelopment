# Lambda's

A lambda expression represents an anonymous function. It comprises of a set of parameters, a lambda operator (->) and a function body.

Since it represents an anonymous function, a lambda can be used to implement a method. A callback method is a method that takes a method as a parameter.
The function parameter is usually passed, using an interface with only one method.


### Abstract class example:
```java
public class Text{
    private String sentence;

    public void printFilteredWords(WordFilterInterface filter){
        for (String word: sentence.split(" ")){
            if (filter.isValid(word)){
                System.out.println(word);
            }
        }
    }
}
```
```java
public interface WordFilterInterface {
    boolean isValid(String word);
}
```
The moment we want to use `printFilteredWords()` (the callback method) we need to implement the interfaces' funftion. 
We can use an abstract class for this implementation. An abstract class is a class without name.

```java
public static void main(String[] args){

    Text text = new Text("Hello this is an example sentence");
    
    //The callback function with implementation of the interfaces' method
    text.printFilteredWords(new WordFilter(){
        public boolean isValid(String word){
            return word.contains("e");
        }
    })
}

```
At the beginning of this page we said that lambdas represent anonymous functions ( functions with no name). We will now see what a lambda is and how it can replace the anonymous class inside the callback-methods.

### Lambda

A lambda expression consists of three things:

	1. A set of parameters
	2. A lambda operator (->)
	3. A function body
#### The parameters:
* A lambda expression can receive zero, one or more parameters!

```java
//The following always returns 42
() -> 42;
```
* The type  can be explicetly declared of it can be infered from the context

```java
//explicitly declared type
(char c) -> c == 'y';

//infered from context
n -> n*5;
```
* In the case of multiple parameters they are enclosed in paratheses and 
seperated by a comma

```java
//Explicitly declared
(x,y) -> x + y;

// Inferred from context
(int a, int b) -> a * a + b * b;
```
* If no parameters are used we use an empty set of parantheses

```java
//No parameter, always returns 42
() -> 42;
```
* If there is only one single parameter without type, it is not necessary to use parentheses.

```java
// Given a number n the following expression returns a boolean indication if it is odd 
n-> n%2 != 0;
```

#### The lambda operator
Between the parameters and the body there should always be the lambda operator to show that we are using a lambda expression. The lambda operator consists of `-` and `>` combined  like this: `->`. 

#### The body
* The body of the lamda expression is like the body of a normal function, it contains the expressions.
* As with the parameters, the body of the expression can contain zero, one or more expressions.
*  If there is only one expression in the body, curly brackets `{}` are NOT mandatory. The return type will automaticly be the same as that of the expresion in the body.
*  If there is more then one statement inside the body, they must be enclosed by curly brackets (like the body of a normal function). Also here, the return type will automaticly be the same as the type of value returned within the code block.

#### The callbackmethod with a lambda expression

We remember that a callback-method was method that gets a function passed as a parameter. Mostly by the use of an interface ( we will cann this interface a functional interface, hence its annotation `@FunctionalInterface`) with only one method in it.

In the example above we used an anonymous class to implement the interfaces' method. With what we know now, we can alter the example above to use a lambda exrpression instead of that anonymous class. The lambda expression will implement the functional interfaces' method.

##### The example with the anonymous class:
```java
public class Text{
    private String sentence;

    public void printFilteredWords(WordFilterInterface filter){
        for (String word: sentence.split(" ")){
            if (filter.isValid(word)){
                System.out.println(word);
            }
        }
    }
}
```
```java
@FunctionalInterface 						//This annotation is not mandatory
public interface WordFilterInterface {
    boolean isValid(String word);
}
```
So here we use the anonymous class `new WordFilter(){..implementation of the method..}` to implement the method of the functional interface `WordFilter`.

```java
public static void main(String[] args){

    Text text = new Text("Hello this is an example sentence");
    
    //The callback function with implementation of the interfaces' method
    // Using an anonymous class
    text.printFilteredWords(new WordFilter(){
    	// The method that needs implementing
        public boolean isValid(String word){
            return word.contains("e");
        }
    })
}

```
Now we will use a lambda expression to implement the same method:

```java
public static void main(String[] args){

    Text text = new Text("Hello this is an example sentence");
    
    //The callback function with implementation of the interfaces' method
    // Using a lambda expression
    text.printFilteredWords((String s) -> s.contains("e"));
 }

```
We see this is a very short and clear way to implement out method on the fly.

### Summary
* A lambda expression can be used anywhere a normal method can be used but since it represents an anonyous function, no name for a method needs to be given.
* The return type of the lambda expression is automaticcly set to the return type of its body. There is no need to setting it ourselves!
* A great way of using lambda expressions is within a callback-method. This is however not its only use! As already stated, a lambda expression can be used anywhere a normal method can be used!
 
