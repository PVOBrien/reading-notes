# Maps, primitives, File I/O

## [Java Primitives versus Objects](https://www.baeldung.com/java-primitives-vs-objects)

There is autoboxing, and unboxing of primitives (which are immutable, so they can'/won't change) and final (meaning they are un-inheritable).

> Integer j = 1;          // autoboxing

> int i = new Integer(1); // unboxing

And I can't tell from the reading if one is more memory-conscious than the other. But it goes on to show that "primitive types are faster than those for wrapper classes". Which makes sense, as there is less code and content if it's just the primitive, instead of having to go through the wrapper (usually an array, correct?) to then get to the primitive.

But I'm still uncertain if autoboxing or unboxing is the better method to ensure the best use of memory, and mentions that using primitive types in java "generics" is currently not available (I don't know what generics are atm). And all primitives have a default value of 0, null, false, or whatever is the lowest/least/"only just exists" state for that primitive.

## [Exceptions](https://docs.oracle.com/javase/tutorial/essential/exceptions/index.html)

What happens when there's an exception in your code? You try to catch it! Lest it crash your otherwise smoothly running code. 

> Definition: An exception is an event, which occurs during the execution of a program, that disrupts the normal flow of the program's instructions. <br> Quote from [here](https://docs.oracle.com/javase/tutorial/essential/exceptions/index.html).

When an exception arises and it is *caught*, it moves up through the stack looking for something to handle it. If nothing catches it, a crash is the next likely step, if it compiles at all.

1. checked exceptions. These are caught and raised by the system, at which point the coder can use it to find a way to recover from it.
2. errors. These are isses that are brought about due to outside/external details - think "no keyboard", or some relevant file was deleted that the program was expecting. Java will catch something about these, and depending on the relevancy/frequency something can be captured and a remedy created, or it can print the stack trace and exit.
3. runtime exceptions. Not expected, and not anticipated. Seems like they're most commonly created when interacting with APIs or such and the two don't communicate correctly

There is discussion about checked and unchecked exceptions, and I do not currently understand the implications and/or ramifications.

How to catch and handle exceptions is explained  in the [related Oracle documentation](https://docs.oracle.com/javase/tutorial/essential/exceptions/handling.html).

This involves _try_, _catch_, and _finally_ code blocks, wherein the exception can be corrected perhaps within the application, or by interaction with the user, or if it devolves, details can by saved in order (hopefully) to find a solution with the issue. The _finally_ block is in place to ensure everything about the exception is closed, tidied up, garbaged, etc.

## [Java File Scanner](https://docs.oracle.com/javase/tutorial/essential/io/scanning.html)

The Scanner library is used to read through .txt files, and then parse that information by various means. White space is used to seperate "tokens".
