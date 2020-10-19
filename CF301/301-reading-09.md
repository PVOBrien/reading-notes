## Refactoring

### [Functional Programming](https://medium.com/the-renaissance-developer/concepts-of-functional-programming-in-javascript-6bc84220d2aa)

Functional programming is not a _type_ of programming per se, but more of a philosophy or goal of coding. It is a goal to have "pure" code, that always returns the same result with the same inputs (also called deterministic code), and doesn't have side effects to other parts of the code. Stable, consistent, and predictable. The article also makes a point that all numbers within a function, should be called into the function (that does not live solely within that that function).

It goes on to make additional cases for enuring that data is not mutated. It can be modified for purposes, but always returns to it's original state, so it can be accessed by other functions safely, that those other functions can be invoked and run, securely knowing what is going in and what will come out.

Higher Order Functions. They:
  take one or more functions as arguments, or
  returns a function as its result.
  
Higher order functions are something else, that I can hardly reckon with at the moment. This also draws in the notion of functions as first class entities, that can also be passed into functions, and be returned as a result of a function. Really interesting possibilities, if some switch causes one function to be used instead of another for some purpose I definitely had not thought of that before.

It also talks about making functions "declarative", which seem to be to make functions much more human-friendly readable, and can be read from left to right and see exactly what it is doing; that it is less "code" and more "sentence".

## [Refactoring JavaScript for Performance and Readability](https://dev.to/healeycodes/refactoring-javascript-for-performance-and-readability-with-examples-1hec)

This article makes a case for balancing efficiency with readability, and finding the happy middle ground. It made the interesting claim that at times it is better to have one function do multiple things. Which might obfuscate what a function does, _but_ if many things need to happen off of one event, why break it up on account of "better code"?

The most interesting and relevant piece was about "caching" variables, such that if you have to do a great number of loops in loops, than take a line to declare a variable of what is interesting so you can make it actually readable. After going just once or twice in, seeing that line and being able to read it is just like taking a deep breath. The other bit was to shorten up code that would exit a function early, like an "if THING == "EXISTS" check, then it might be ok to "inline" it, take up a one less line, and it's still very legible, and easy to know what it does.
