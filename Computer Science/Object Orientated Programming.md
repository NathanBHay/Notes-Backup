Object orientated programming is a paradigm which operates under the concept of **objects** which are dynamically kept pieces of data. These objects have **methods** which are functions that interact with the object.

**Classes** are a blueprint which are used to build objects. They define what it stores, its methods, and internal variables. Classes are **initialized** or **instantiated** to create an object. Many languages keep an initialization method which is called upon creation of the class.

OOP functions on the idea of **encapsulation** which is the grouping of features together within an object. The decision of what to include is called an **abstraction**. To make an efficient abstraction it is common to use **information hiding** as to keep access of elements within an abstraction safe from outside processes.

# Access Modifiers
A large part of OOP are **access modifiers**. These descriptors are able to modify what can access and edit variables and methods. In general these access modifiers include:
- **Private** which can only be accessed by the class.
- **Protected** which can be accessed by the class and subclasses.
- **Public** which can be accessed by anything.

**Non-access modifiers** are modifiers which are able to either share or make values immutable. Ones of these found within some languages is **static**. Static is a shared instance between all objects of the class. Another common method is **final** which makes the value immutable. This can be combined with static to make a constant.

## Associations/Dependency
Associations demonstrate a strong relationship between multiple classes . Put simply this means that the class knows about another class. An **aggregation** is a type of association where the second class can exist independently of the value. **Composition** is a type of association where the second class can't exist independently.

Dependencies are less tightly coupled  however changes to the dependency will modify the execution of the code in the dependence class. Simply this means that one class has an attribute type of another class.

# Inheritance
**Inheritance** also called **generalisation** is a mechanism that enables classes to be based off other classes. This **child** or **derived** class inherits attributes from its **parent** or **base** class. A child class can override methods created by its **ancestors**. **Abstract methods** are used when a method doesn't do anything, as it will be defined later by subclasses.

Classes have generic functions which can be modified by classes.

# Interfaces
Interfaces also called a **realisation** is a mechanism of declaring a set of methods that can be implemented by a class. When interfaces call upon each other this is actually inheritance.

## Fluent Interfaces
Within object orientated programming functions are commonly chained as to produce a result. To combat this many methods within an object return an instance of the object as to allow for easier flow.

## Enumeration
Enumerations are a way of creating special characters that can be compared fast.

# Diagrams
Object orientated programming is heavily aided by the use of diagrams. The most commonly used diagrams are class diagrams, which demonstrate the relations between classes, and interfaces, and sequence diagrams which depict the lifecycle of multiple classes.

## UML Class Diagrams
UML class diagrams segment their data into three separate sections. These are *Name*, *Attributes*, and *Operations*. There are two types of UML diagrams, these are structural, and behavioral. **Structural** diagrams are used to describe the static structure of the system. While **behavioral** are used to describe the relations between a system and its functionality.

Diagrams that have lines between them are used to depict shared values or constructor calls. These have labels that are used to represent the amount of association between each class. With the `1..*` used to represent a one to many amount.

**Interface** and **enumerations** are represented with a tag at the top of the class which notes it as an `<<interface>>` or `<<enumeration>>`.

## Sequence Diagram
A sequence diagram is a form of diagram that expressed more overtly the life cycle of a segment of objects and code. This is done through a thick line segment called an **activation bar** that has lines going out of it to demonstrate the functions that effect each others life cycles. This allows the functions to demonstrate their callback operations through a return message. Guard cases can be drawn onto the diagram to illustrate cases comprehensive cases. Creation of an object can be labelled with the `<<create>>` syntax while destruction can be labeled with an `X`.

Communication diagrams are similar to sequence diagrams however only contain lines without activation bars. This makes the diagram quicker to make but less explicit in its return messages.

