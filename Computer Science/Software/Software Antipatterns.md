During the writing of software it is common to employ software patterns as to increase the quality of code. Inverse to this idea are software antipatterns where commonly used processes or structures result in code performing worse due to incorrect implementation or application of abstraction. These antipatterns usually have alternative methods that can easily solve the problem. Antipatterns can be found by observing symptoms of the bad code, commonly called **code** or **design smell**.

In general the common thread of all code smells and anti-patterns is that they make the code:
- **Rigid/Fragile** meaning it is hard to change without breaking other things.
- **Immobile** which results in it being unable to be reused in other sections.
- **Viscous** which means that designers are coding in a way that preserves the environment rather than attempting to improve it.

# Common Antipatterns
Antipatterns can be categorised as to illustrate the different problems that can be found within the code.

## Magic Numbers
**Problem:** constant numbers that commonly appear in code repeatedly without being bound to a variable. This is caused the need for constants in code that can't be fed through as an argument. The result of this causes values which may appear multiple times within the code that when changed require changes to all other constants of the same value.

**Fix:** binding values to variables fixes this issue allowing for the values to be reused.

## God Class
**Problem**: a god class or object occurs when there is a primary main class which handles most of the logic of the program. This is usually found within [[Object Orientated Programming#UML Class Diagrams|UML diagrams]] that have a primary class which is associated with every class. Additional classes for a god class usually only handle data. God classes are usually caused when people lack proper understanding of abstracting their code. A god class removes many of the advantages of [[Object Orientated Programming|OOP]] and results in a code base which isn't reusable

**Fix:** god classes can be fixed by splitting the class into different segments to handle individual logical sections.

## Dead Code
**Problem:** unused segments of code that aren't used by any functions or classes due to being obsolete. This problem is common in programs that are updated or changed. They cause the codebase to become bloated and may result in decreased efficiency. Dead code can also include commented out code.

**Fix:** deletion of old and unneeded files is the easiest fix. If not refactoring methods can be used as to remove unnecessary parameters, and classes.

## Continuous Obsolescence
**Problem:** continuous obsolescence happens when frameworks or programming languages update during production of code. This leads to the program to be disjointed due to it having outdated technology or techniques bundled with current code. This problem is more unintentional and is caused by choosing the wrong framework or language,

**Fix:** either use technology that is slow to change, or use technology created by the developer instead. This can remove the middle man and ensure the technology isn't outdated.

## Functional Decomposition/No OOP
**Problem:** functional decomposition happens when no OOP is used in a system that requires can abstraction. This is the result of non-OOP programmers attempting to program in a procedural way when an abstraction is required.

**Fix:** to fix this problem simply design a system that can be applied to the problem.

## Poltergeist
**Problem:** poltergeists are classes with limited responsibilities that only exist to perform a basic task such as instantiation. These classes prove an antipattern as they are added complexity upon the model that only are used for a limited amount of time. This clutters the overall design of the program.

**Fix:** poltergeist can be refactored out by implementing the features within the class that the poltergeist originally controlled.

## Golden Hammer
**Problem:** a golden hammer is a solution that is used for many different problems rather than an individual solution. This results in the solution being sub-optimal and a catch-all. Golden hammers happen due to an unwillingness to learn or create new solutions. Despite these issues, golden hammers can be useful when hacking together a product.

**Fix:** exploration of new techniques to solve different problems is the simplest fix.

## Cut & Paste Programming
**Problem:** cut and paste programming occurs when code is commonly copied from outside sources. This results in plagiarism but also undocumented and faulty code. This problem is common for individuals who lack understanding of the problem.

**Fix:** the solution is to prevent copied code from entering the code base. To refactor the issue find places where the code is less reusable and implement a better solution.

# Code Smell
Code smell isn't an antipattern but rather evidence of underlying issues.

## Bloaters
Bloaters are code, methods or classes that increase to a size that makes them hard to work with. This usually occurs due to increases in the specifications of a program.

#### Long Methods/Classes
**Problem:** long methods/classes are segments of code that are too long in line length. They are usually caused by overreliance on a single functional component without attempting to decompose it.

**Fix:** extract the methods into multiple ones, while attempt to create a new abstraction for classes.

#### Primitive Obsession
**Problem:** overreliance on primitive data types instead of creating new types or classes to represent field. Further cases include using array indices when dictionaries or objects should be used. This is common in smaller projects however can lead to confusion when scaled up due to the lack of flexibility and understandability.

**Fix:** replace primitive fields with objects or type declarations that restrict the data.

#### Long Parameter List
**Problem:** more than three or four parameters for a single method is usually bad practice as it creates more confusion as the amount of parameters increase. This problem is usually caused by combining methods together or attempting to separate methods or classes into more reusable forms.

**Fix:** a common fix is to use objects to represent the parameters. Alternatively parameters can be replaced with function calls in cases where the function can be split up.

## Object-Orientation Abuse
Object orientated programming is commonly used incorrectly, this takes a variety of common forms.

#### Switch Statements
**Problem:** Having a complex switch, or if statement usually indicates incorrect use of OOP, as OOP usually avoids switch statements.

**Fix:** this problem is commonly fixed by using polymorphism instead of conditionals.

#### Temporary Fields
**Problem:** temporary fields are ones that usually are empty unless under certain circumstances.

**Fix:** temporary fields are usually fixed through the use of new classes or extensions. If not integrating conditionals to check temporary fields for existence.
