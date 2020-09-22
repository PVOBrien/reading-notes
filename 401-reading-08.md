# OO (Object-Oriented) Design

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

Liskov Substitution Principle

