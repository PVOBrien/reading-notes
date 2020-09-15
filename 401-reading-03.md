# Maps, primitives, File I/O

## [Java Primitives versus Objects](https://www.baeldung.com/java-primitives-vs-objects)

There is autoboxing, and unboxing of primitives (which are immutable, so they can'/won't change) and final (meaning they are un-inheritable).

> Integer j = 1;          // autoboxing

> int i = new Integer(1); // unboxing

And I can't tell from the reading if one is more memory-conscious than the other. But it goes on to show that "primitive types are faster than those for wrapper classes". Which makes sense, as there is less code and content if it's just the primitive, instead of having to go through the wrapper (usually an array, correct?) to then get to the primitive.

But I'm still uncertain if autoboxing or unboxing is the better method to ensure the best use of memory, and mentions that using primitive types in java "generics" is currently not available (I don't know what generics are atm). And all primitives have a default value of 0, null, false, or whatever is the lowest/least/"only just exists" state for that primitive.

## [Exceptions](https://docs.oracle.com/javase/tutorial/essential/exceptions/index.html)

What happens when there's an exception in your code? You try to catch it! Lest it crash your otherwise smoothly running code. 
