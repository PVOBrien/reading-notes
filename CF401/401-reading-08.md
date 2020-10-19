# [OO (Object-Oriented) Design](https://www.digitalocean.com/community/conceptual_articles/s-o-l-i-d-the-first-five-principles-of-object-oriented-design)

## S.O.L.I.D. Principles

1. Single-responsibility
2. Open-closed
3. Liskov Substitution
4. Interface Segregation
5. Dependency Inversion

SOLID. By following these principles, code can be best suited for today's coding paradigms and workflows - pure code, ready for refactoring, and able to fit into agile or adaptive software development.

SRP - Single Responsilibity Principle: any one class, has one reason to be, and one thing (or object?) to change.

Open-closed Principle

> Objects or entities should be open for extension, but closed for modification.

So classes should be able to "do" actions, but not do the grunt work to be able to enable that action to run. That is other objects' responsibility to be able to __interface__ (!) with other classes. If an object isn't -able, than that is on _that_ object, not the interface.

Liskov Substitution Principle : if it's a subclass, it should be able to stand in for any instance of it's parent class (but not vice versa).

Interface Segregation Principle

>A client should never be forced to implement an interface that it doesn’t use or clients shouldn’t be forced to depend on methods they do not use.

Don't implement or extend to classes that don't need them. Make your interfaces modular enough so as to be specific.

Dependency Inversion Principle

> Entities must depend on abstractions not on concretions. It states that the high level module must not depend on the low level module, but they should depend on abstractions.

If I'm parsing this correctly, it status that nothing of the object can be directly connected to something that will break; that anything that interlinks with, there should be another "gear"/"glue"/"connector" - likely an __interface__ - that can be checked for Exceptions/errors and then work on reconnecting that link/connector.

## [S.O.L.I.D. I.R.L.](https://dzone.com/articles/the-solid-principles-in-real-life)

Single Responsibility Principle - cars for land travel. boats for water. carboats are rare because they have twice the opportunity to fail, and then their breakdown is felt twice as hard. Hence: car. boat.

Open/Closed Principle - your smartphone. It's core functionality works out of the box. Then you add apps. Same with interfaces/inheritance. Take the core of something, leave it in place, add to it for the use cases that arise for unique cases. But don't go stuffing everything into the primary class/interface if it means bunches of other classes all of a sudden got firehosed with _way_ more methods than is necessary.

Liskov Substitution Principle - Start with everything that every child should have in subclasses. If that thing can't reasonably contain all that is in the parent... then likely that shouldn't be the subclass' parent.

Interface Segregation Principle - keep your interfaces lean, light, and readable. Make more interfaces if you need, don't make more _in_ your interface.

Dependency Inversion - the more basic and fundamental/generic an implementation can be in your interface, the better to allow more ways to... _interface_.
