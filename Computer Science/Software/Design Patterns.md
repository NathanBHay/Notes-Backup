Design Patterns are methods of writing cleaner code and abstractions through the use of repeatable software patterns that decrease repetition and increase clarity of the code. Similar to [[Design Principles]], design patterns usually involves [[Object Orientated Programming]] as the principles behind this. Design patterns improve **technical debt** which can be seen as the tradeoffs which lead to future programming atop the code base being poorly done. Design patterns prove particularly useful during the refactoring process, where repeated code, poorly written code, and bugs should be removed. Despite these benefits correct adaptation is always important as to avoid creating more issues. Patterns are commonly classified into two types, these types are:
- **Idioms**, which are low-level patterns that are usually only relegated to a specific language, or a set of languages. They normally only change small segments of the code.
- **Architectural patterns**, which are high-level patterns that can be implemented in most languages and usually change the overall structure of the program. These patterns are then subclassified into three different types called, creational, structural, and behavioural patterns.

# Creational Patterns
Creational patterns deal with the creation of objects or types. They attempt to increase the reusability during the early stages of an objects life cycle, and as such only do one specific job.

## Factory Methods
Factory methods are functions that are called instead of a default constructor method. They are usually found either within a class to instantiate itself, or a superclass used only for creation of that object. To create a factory method call a constructor method from within the class, or within another class, and usually return the object.

Factory methods are usually used to fix issues related to:
- Limitations during the creation process that require complex logic.
- Classes that don't know the dependencies or types before hand.
- To enable developers to extend your framework.
- Increase reusability by having less calls to constructors.

This results in a tighter coupling between creator and the objects, makes the code follow [[Design Principles#Single Responsibility Principle|single responsibility]] by having a creator class, and the [[Design Principles#Open-Closed Principle|open-closed principle]] by allowing new types to be introduced. The downside is the increase in the complexity of the program.

Factory methods can be subdivided into the following categories:
- **Creation methods** which are wrappers for the constructor that change its output in some capacity.
- **Static creation methods** are shared amongst the class, and usually used to implement other patterns.
- **Simple factory methods** are a basic class that is used to create another class.
- **Factory method** is an interface that is used to create the class.
- **Abstract factory** is another design pattern that is a type of factory method.

## Abstract Factory
Abstract factories are a subtype of [[Design Patterns#Factory Methods|factory methods]] however, instead allow for the creation of objects without a specific type. These factories are usually found within a abstract class or an abstract super class of other factory methods. They are done by implementing either a constructor interface that allows for classes to be instantiated, or a super class.

Abstract factories are used in cases where:
- Classes aren't known before hand, just the abstract class at the top.
- When there are multiple factory methods that can be bundled together in a class.

Creating an abstract factory has all the benefits of factory methods with the addition of being able to combine factories that are compatible with each other. They still suffer from further complicating the code base.

## Builder
A builder is a pattern which functions to modify attributes that would usually be declared in the constructor. They allow a sequential build up of attributes within a specific object, promoting reusability of classes. A builder pattern is done by initializing variables as null, and then implementing functions that build up the attributes of the object. A **director** class is another approach where a new class is made to build the object, this helps split the code up.

Builder patterns are useful in situations where:
- Long constructor parameters, or constructor parameters that have null called.
- Create different representation of a same object.

Builders allow for greater reusability, and the construction of objects in a step-by-step capacity. It also follows the single-responsibility principle. Despite this, it does result in a more functions that could be simplified.

## Prototype
A prototype is a patterns which allows the copying of existing objects without making an object dependent on another class through extension. This can be done by creating a clone interface which defines a method that allows for the cloning of an object, without any generalisation. The method should copy all attributes into the new constructor and modify it in a specific way (overloads help here).

Prototypes are used to help cases where:
- An object needs to be decoupled from its parent.
- Reduce the number of subclasses that only differ in the way they initialize a part of the object.

This allows the cloning of objects without any coupling, gets rid of repeated use of constructor arguments, and also creates an alternative to using inheritance. Cloning objects that have circular references is difficult.

## Singleton
A singleton ensures that there is only one instance of an object existing at once. It usually involves a static factory method that assigns a static variable to an instance of a class. This therefore stops the constructor method from being accessed unless through a method which declares an instance.

Singletons are most commonly used when:
- Only a single instance of a particular class should ever exist.
- When you want global variables that exist inside a class.

This allows classes to ensure they only have a single instance, creates a global access point for the instance, and in some cases enables the instance to be only created once. That being said it violates single-responsibility, can mask cases where components know too much about each other, is hard to implement in multi-threaded environments, and is difficult to unit test.

# Structural Patterns
Structural patterns allows the creation of large object structures through a more flexible approach that enables these monolithic classes to be easy to change and modify.

# Behavioural Patterns
Behavioural patterns deal with communication between objects and classes through a variety of different algorithms that handle the responsibilities of objects.
