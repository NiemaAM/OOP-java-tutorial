[![Java](https://img.shields.io/badge/Java-21-red.svg)](https://www.java.com)

# Learn Java & OOP
Full Java OOP tutorial!

# OOP core concepts:
## 1. What is a class?
A class is a Blueprint or template that defines properties and behaviors.

example: `Animal` is a class, it has a `name` and a `race` and it can `eat()` and `sleep()`.
```bash
+----------------------------+
|           Animal           |  <-- Class name
+----------------------------+
| + name: String             |  <-- Attributes (properties)
| + race: String             |
+----------------------------+
| + eat():void               |  <-- Methods (behaviors)
| + sleep():void             |
+----------------------------+
```
### Components of a class:
- *Class Attributes (properties):*
  - Can be:
    * `static`: not an instance of the class (global variable).
    * `final`: constant variable.
  - Must have *visibility*:
    * *`public`:* accessible for all classes.
    * *default (nothing):* accessible in the same package.
    * *`private`:* accessible within the declared class.
    * *`protected`:* accessible in the same package and subclasses.
  - Must have a *datatype*:
    * *Primitive:* Specifies the size and type of variable - `boolean` (1 bit), `byte` (1byte), `short` & `char` (2byte), `int` & `float` (4byte), `long` & `double` (8byte).
    * *Reference:* Pointer & Reference that hold the address to the object.
  - Have a *name*: Always start with a lowercase letter and then capitalize the first letter of every subsequent word, for constants (final) use uppercase with underscore.

- *Class contructor:* A special method used to initialize objects.
    * A class can have many constructors with different parameters (overloading).

- *Class Methods (behaviors):*
    * Must have a *visibility:* A method can be public, package, private or protected.
    * Must have a *return type:* `void` (returns nothing) or returns a value (can be an `int`, `double`, `boolean`, `String`, `Object`...).
    * Have a *name:* Methods should be verbs, in mixed case with the first letter lowercase, with the first letter of each internal word capitalized.
    * May have *parameters:* The values that will be passed to the method.
    * May have *local variables:* An auxiliary temporary variable that exists only while a particular method or a block of statements.
    * Have a *body:* The logic of the method.

```java
public class Animal {
    // Class Attributes (properties)
    public String name;
    public String race;
    // Class default constructor
    public Animal(){}
    // Class contructor
    public Animal(String name){
        name = this.name;
    }
    public Animal(String name, String race){
        name = this.name; // `this.name` refere to the method parameter `name`
        race = this.name; // `this.race` refere to the method parameter `race`
    }
    // Class Methods (behaviors)
    public void eat() {
        System.out.println("Miam Miam!");
    }
    public void sleep() {
        System.out.println("ZZzz...");
    }
}
```

## 2. Encapsulation:
Putting attributes & behaviors (methods) of the same kind in one class.

example:
The `Animal` class encapsulates attributes (`name`, `race`) and methods (`eat()`, `sleep()`) together within one class.
```bash
+----------------------------+
|           Animal           |
+----------------------------+
| + name: String             |  <-- Attributes (public)
| + race: String             |
+----------------------------+
| + eat():void               |  <-- Methods (public)
| + sleep():void             |
+----------------------------+
```

## 3. Coherence: 
Intra module relationships within a class.

example: In the `Animal` class, the `name` and `race` attributes and the methods `eat()`, `sleep()` and `makeSound()` are all related and belong to the same class module, showing strong intra-module cohesion.
```bash
+--------------------------------+
|             Animal             |
+--------------------------------+
| + name: String                 |
| + race: String                 |
+--------------------------------+
| + eat():void                   |
| + sleep():void                 |
+--------------------------------+
```

## 3. Information hiding: 
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
```java
public class Animal {
    // Class Attributes
    private String name;
    private String race;
    // Class constructors
    public Animal(){}
    public Animal(String name){
        name = this.name;
    }
    public Animal(String name, String race){
        name = this.name;
        race = this.name;
    }
    // Class Methods
    public void eat() {
        System.out.println("Miam Miam!");
    }
    public void sleep() {
        System.out.println("ZZzz...");
    }
    // Class Getters
    public String getName() {
        return name;
    }
    public String getRace() {
        return race;
    }
    // Class Setters
    public void setName(String newName) {
        name = newName;
    }
    public void setName(String newRace){
        race = newRace;
    }
}
```

## 4. Inheritance:
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
+--------------------------------+ <──────────────── +--------------------+
| + eat():void                   |                   | + bark():void      |
| + sleep():void                 |                   +--------------------+
| + getName():String             |
| + setName(newName:String):void |
+--------------------------------+
```
```java
public class Dog extends Animal {
    // Class constructor
    public Dog(String name, String race){
      super(name,race); // call the Animal super class constructor
    }
    public void bark() {
        System.out.println("WOUF!");
    }
}
```

## 5. Polymorphism:
Many classes related to each other by inheritance.
- *Overriding:* Two methods have the same name and same parameters.

example: Both `Dog` and `Cat` classes override the `makeSound()` method, but each class implements it differently. The type of object determines which version of the method is called.
```bash
+--------------------------------+
|             Animal             |                   +--------------------+
+--------------------------------+                   |        Dog         |
| - name: String                 | <──────────────── +--------------------+
| - race: String                 |                   | + makeSound():void | <---- makeSound print "WOUF!"
+--------------------------------+                   +--------------------+
| + eat():void                   |                   +--------------------+
| + sleep():void                 |                   |        Cat         |
| + makeSound():void             | <──────────────── +--------------------+
| + getName():String             |                   | + makeSound():void | <---- makeSound print "MEOW!"
| + setName(newName:String):void |                   +--------------------+
+--------------------------------+
```
```java
public class Animal {
    public void makeSound() {
        System.out.println("Say something...");
    }
}
```
```java
public class Dog extends Animal {
    @Override
    public void makeSound() {
        System.out.println("WOUF!");
    }
}
```
```java
public class Cat extends Animal {
    @Override
    public void makeSound() {
        System.out.println("MEOW!");
    }
}
```
## 6. Abstraction: 
Hiding certain details by:
- *creating abstract classes:* A class that cannot be instantiated and may have both abstract (unimplemented) and concrete (implemented) methods.

exmaple: The `Animal` class is abstract with an abstract method `makeSound()`. The `Dog` class implements this method.
```bash
+--------------------------------+                   +--------------------+
|             Animal             |                   |        Dog         |
+--------------------------------+                   +--------------------+
| + eat():void                   | <---------------- | + makeSound():void | <-- Concrete implementation
| + sleep():void                 |                   +--------------------+
| + makeSound():void             | <-- Abstract method
+--------------------------------+
```
```java
abstract class Animal {
    // Concrete (implemented) methods
    public void eat() {
        System.out.println("Miam Miam!");
    }
    public void sleep() {
        System.out.println("ZZzz...");
    }
    // Abstract (unimplemented) method
    public abstract void makeSound();
}
```
```java
public class Dog extends Animal {
    // Concrete implementation
    public void makeSound() {
        System.out.println("WOUF!");
    }
}
```
- *creating interfaces:* An interface is a contract that defines a set of abstract methods without providing any implementation.

exmaple: `Animal` is an interface with tree methods: `makeSound()`, `eat()` and `sleep()`.
```bash
+--------------------------------+                   +--------------------+
|        interface: Animal       |                   |        Dog         | <-- Dog implement Animale interface
+--------------------------------+                   +--------------------+
| + eat():void                   | <---------------- | + eat():void       | <-- Concrete implementations
| + sleep():void                 |                   | + steep():void     |
| + makeSound():void             |                   | + makeSound():void |
+--------------------------------+                   +--------------------+
```
```java
interface Animal {
    // Abstract (unimplemented) method
    public void eat();
    public void sleep();
    public abstract void makeSound();
}
```
```java
public class Dog implements Animal {
    // Concrete implementation
    public void eat() {
        System.out.println("Miam Miam!");
    }
    public void sleep() {
        System.out.println("ZZzz...");
    }
    public void makeSound() {
        System.out.println("WOUF!");
    }
}
```
## 7. Coupling:
Inter module relationships between classes (one class depends on the other).

example: `Animal` and `Food` are coupled, meaning that `Animal` depends on `Food` for some behavior or data, in that case `Animal` `eat(something:Food)`, creating a relationship between them.
```bash
+--------------------------------+
|             Animal             |
+--------------------------------+
| - name: String                 |                   +--------------------+
| - race: String                 |                   |        Food        |
+--------------------------------+ _________________ +--------------------+
| + eat(something:Food):void     |                   | + type: String     |
| + sleep():void                 |                   | + qantity: int     |
| + makeSound():void             |                   +--------------------+
+--------------------------------+
```
```java
public class Food {
    public String type;
    public int quantity;
    // Class Getters
    public String getType() {
        return type;
    }
    public int getQuantity() {
        return quantity;
    }
}
```
```java
public class Animal {
    public void eat(Food something) {
        System.out.println("Miam Miam! *eats "+something.getType()+"*");
    }
}
```

## 9. Overloading: 
Two or more methods in the same class have the same name but different parameters (signature).

exmaple: The `Addition` class has several `add()` methods with different parameters (`int` and `double`), which allows different combinations of input.
```bash
+------------------------------+
|           Addition           |
+------------------------------+
| + add(int, int):int          |
| + add(double, double):double |
| + add(int, int, int):int     |
+------------------------------+
```
```java
public class Addition {
    public int add(int nbr1, int nbr2) {
        return nbr1 + nbr2;
    }
    public double add(double nbr1, double nbr2) {
        return nbr1 + nbr2;
    }
    public int add(int nbr1, int nbr2, int nbr3) {
        return nbr1 + nbr2 + nbr3;
    }
}
```

## 8. Shadowing: 
Variable declared within a specific scope has the same name as a variable declared in an outer scope.

example: The *InnerScope* method `add()` has a `value` variable that shadows the `value` variable declared in the *OuterScope* class `Addition`, meaning the InnerScope version takes precedence within its scope.
```java
public class Addition {
    int value = 5;  // Class-level variable
    public int add(int nbr1, int nbr2) {
        int value = nbr1 + nbr2;  // Method variable, shadows the class-level variable
        return value;
    }
}
```
