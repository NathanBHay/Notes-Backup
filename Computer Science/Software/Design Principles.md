Design principles are a way of writing better code through a structured approach.

# DRY
DRY or Don't Repeat Yourself, is a fundamental principle of programming which simply expresses the need to use functions and classes as to avoid repetition of code blocks.

# SOLID
SOLID is a series of design principles for [[Object Orientated Programming]]. Each of these design principles allow for more succinct code. SOLID stands for Single Responsibility, Open-closed, Liskov substitution, interface segregation, and dependency inversion.

## Single Responsibility Principle
Single responsibility principle states that every class should only manage one job within the program. By part this extends to the class methods where all methods should manage one aspect of the overall program. This process can be done through splitting a class up into subclasses, in the case where the class has temporary fields or methods, or by using composition to build up classes instead.

## Open-Closed Principle
Open-closed principle states that classes should be open to extension but closed for modifying the class itself. This means that an inherited class shouldn't attempt to change the parent, only extend its functionality. This practice can be done by creating parent classes that don't attempt to have methods for all the functionality the subclasses can do, rather create subclasses that have new methods.

## Liskov Substitution Principle
Liskov substitution operates on the idea that functions that use pointers or references to base classes must use derived classes. More simply every subclass should be able to be called by the parent. In practice this means using extensions that don't remove parent method implementations. This therefore, can be done through interface segregation, or refactoring of classes.

## Interface Segregation Principle
Interface segregation principle states that no code should depend on methods it doesn't use. This equates to splitting interfaces as to only declare methods that are implemented. Simply having too many interfaces is better than not enough.

## Dependency Inversion
Dependency inversion states that loosely coupling high level and low level modules should be done as to avoid a dependency chain. This can be done through interfaces, or composition that allows for classes to be smaller and more reusable. The process is especially important as direct coupling through inheritance can result in changes to sub classes effecting how the abstract class functions. To mitigate these issues it is common to use interfaces or extra classes as a way to communicate.
