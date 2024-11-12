[![Java](https://img.shields.io/badge/Java-21-red.svg)](https://www.java.com)

# Learn Java & OOP
Full Java OOP tutorial!

# OOP core concepts:
## 1. Encapsulation:
Putting attributes & behaviors (methods) of the same kind in one class.

example:
The `Animal` class encapsulates attributes (`name`, `race`) and methods (`eat()`, `sleep()`) together within one class.
```bash
+----------------------------+
|       Class: Animal        |
+----------------------------+
| + name: String             |  <-- Attributes (public)
| + race: String             |
+----------------------------+
| + eat():void               |  <-- Methods (public)
| + sleep():void             |
+----------------------------+
```
## 2. Information hiding: 
Hide sensitive information from the user by:
- declare class variables/attributes as private.
- provide public getters and setters to access the data.

example:
The `name` attribute is private, and it can only be accessed or modified using the public `getName()` and `setName()` methods.
```bash
+--------------------------------+
|         Class: Animal          |
+--------------------------------+
| - name: String                 |  <-- Attributes (private)
| - race: String                 |
+--------------------------------+
| + eat():void                   |  <-- Methods (public)
| + sleep():void                 |
| + getName():String             |  <-- Public getter (returns the name value)
| + setName(newName:String):void |  <-- Public setter (take the new name value as an attribute and update the name value)
+--------------------------------+
```
## 3. Inheritance:
Inheriting attributes and methods from one class to another.
- *superclass (parent):* the class being inherited from.
- *subclass (child):* the class that inherits from another class.

example:
The `Dog` class inherits from the `Animal` class, so it gets the `eat()` and `sleep()` methods, and it can also add its own methods, like `bark()`.
```bash
+--------------------------------+
|             Animal             |
+--------------------------------+
| - name: String                 |                   +--------------------+
| - race: String                 |                   |        Dog         |
+--------------------------------+ <---------------- +--------------------+
| + eat():void                   |                   | + bark():voi       |
| + sleep():void                 |                   +--------------------+
| + getName():String             |
| + setName(newName:String):void |
+--------------------------------+
```
## 4. Polymorphism:
Many classes related to each other by inheritance.

example:
Both `Dog` and `Cat` classes override the `makeSound()` method, but each class implements it differently. 

The type of object determines which version of the method is called.
```bash
+--------------------------------+
|             Animal             |                   +--------------------+
+--------------------------------+                   |        Dog         |
| - name: String                 | <---------------- +--------------------+
| - race: String                 |                   | + makeSound():void | <---- makeSound print "WOUF!"
+--------------------------------+                   +--------------------+
| + eat():void                   |                   +--------------------+
| + sleep():void                 |                   |        Cat         |
| + makeSound():void             | <---------------- +--------------------+
| + getName():String             |                   | + makeSound():void | <---- makeSound print "MEOW!"
| + setName(newName:String):void |                   +--------------------+
+--------------------------------+
```
## 5. Abstraction: 
Hiding certain details by:
- creating abstract classes and methods.
- creating interfaces.
```bash
+--------------------------------+
|     Abstract Class: Animal     |
+--------------------------------+
| + eat():void                   |                   +--------------------+
| + sleep():void                 |                   |        Dog         |
| + makeSound():void             | <---------------- +--------------------+
+--------------------------------+                   | + makeSound():void | <---- makeSound print "MEOW!"
                                                     +--------------------+

```
## 6. Coupling:
Inter module relationships between classes.
## 7. Coherence: 
Intra module relationships within a class.
## 8. Overriding: 
Two methods have the same name and same parameters.
## 9. Overloading: 
Two or more methods in the same class have the same name but different parameters.
## 10. Shadowing: 
Variable declared within a specific scope has the same name as a variable declared in an outer scope.
