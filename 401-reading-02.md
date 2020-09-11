# Java Imports

# Different types of loops in Java

The standard _for_ loop is just like in JavaScript

``` java
for (initialization; Boolean-expression; step) {
  statement;
  }
```
nothing fancy, nothing exciting. But! You can label them by prepending the _for_ loop with <label>: to allow for code control in relation to that specific labeled code.

There is also the "enhanced" _for_ loop

``` java
for(Type item : items) {
  statement;
  }
```
in which you first declare the type within the item that will be looped over, then you name the item, and then specify the item that will be iterated over. So it feels very similar to the .forEach() method in JavaScript, but I'm sensing that theoretically, you could loop over a string, or different types of primitives, and not just arrays, I think?

_Iterable.forEach()_ oh hey look. It's a forEach() method, here to save a few lines of code and keystrokes!
