
# Introduction: What is OOP?
OOP stands for Object-Oriented Programming.

* **Procedural programming** is about writing procedures or methods that perform operations on the data.
* **Object-oriented programming** is about creating objects that contain both data and methods.

> **Source:**
> 
> [![W3Schools](https://img.shields.io/badge/W3Schools-04AA6D?logo=w3schools&logoColor=fff)](https://www.w3schools.com/java/java_oop.asp)

# Part 1: OOP core concepts
> [!TIP]
> [![Click Here to Run The Code!](https://img.shields.io/badge/Run%20The%20Code%20Here!-%234CAF50.svg?logo=openjdk&style=for-the-badge&logoColor=white)](https://nam.neetocode.com/niema-alaoui-mdaghri/01JCJX4PA8YQ2RNA4VVYECQ9XZ)

###### Table of contents
<!--ts-->
   * [1. What is a class?](#1-what-is-a-class)
      * [Components of a class](#components-of-a-class)
        * [Class Attributes](#class-attributes-properties)
        * [Class Constructor](#class-constructor)
        * [Class Methods](#class-methods-behaviors)
   * [🧰 2. Encapsulation](#-2-encapsulation)
   * [🌐 3. Coherence](#-3-coherence)
   * [👁️ 4. Information hiding](#%EF%B8%8F-4-information-hiding)
   * [👨‍👦 5. Inheritance](#-5-inheritance)
   * [👨‍👦‍👦 6. Polymorphism](#-6-polymorphism)
   * [🗔 7. Abstraction](#-7-abstraction)
   * [🔗 8. Coupling](#-8-coupling)
   * [🗍 9. Overloading](#-9-overloading)
   * [🗇 10. Shadowing](#-10-shadowing)
   * [🏃 11. The Main Class](#-11-the-main-class)
<!--te-->

## 1. What is a class?
A class is a Blueprint or template that defines properties and behaviors.
### **Components of a class**
#### **Class Attributes (properties):**
  - Can be:
    - ⚡ `static`: not an instance of the class (global variable).
    - 🛑 `final`: constant variable.
  - Must have **visibility**:
    - 🌍 **`public`**: accessible for all classes.
    - 🔒 **default (nothing)**: accessible in the same package.
    - 🔑 **`private`**: accessible within the declared class.
    - 🛡️ **`protected`**: accessible in the same package and subclasses.
  - Must have a **datatype**:
    - 🧬 **Primitive:** Specifies the size and type of variable:
      - `boolean` (1 bit), `byte` (1 byte), `short` & `char` (2 bytes), `int` & `float` (4 bytes), `long` & `double` (8 bytes).
    - 🔗 **Reference:** A pointer that holds the address to the object.
  - Have a **name**: 
    - ✨ Always start with a lowercase letter and then capitalize the first letter of every subsequent word. 
    - 💡 For constants (final), use **uppercase** with **underscore** (e.g., `MAX_SIZE`).

#### **Class Constructor:**
  -  🛠️ A special method used to initialize objects.
  - A class can have many constructors with different parameters (overloading).

#### **Class Methods (behaviors):**
  - Must have a **visibility**: A method can be `public`, `package`, `private`, or `protected`.
  - Must have a **return type**: 
    - `void` (returns nothing) or returns a value (e.g., `int`, `double`, `boolean`, `String`, `Object`...).
  - Have a **name**: 
    - 📝 Methods should be **verbs** in mixed case with the first letter lowercase, and capitalize the first letter of each subsequent word (e.g., `calculateTotal`).
  - May have **parameters**: The values passed to the method.
  - May have **local variables**: Temporary variables that exist only while a method or block runs.
  - Have a **body**: 🧠 The logic of the method.

> **Example:**
>
> `Animal` is a class, it has a `name` and a `race` and it can `eat()` and `sleep()`.

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
```java
class Animal {
    // Class Attributes
    public String name;
    public String race;

    // Class Constructors
    public Animal() {} // default constructor

    public Animal(String name) {
        this.name = name; // 'this.name' refer to the instance variable
    }

    public Animal(String name, String race) {
        this.name = name; // 'this.name' refer to the instance variable
        this.race = race; // 'this.race' refer to the instance variable
    }

    // Class Methods
    public void eat() {
        System.out.println("Miam Miam!");
    }

    public void sleep() {
        System.out.println("ZZzz...");
    }
}
```

## 🧰 2. Encapsulation:
Putting attributes & behaviors (methods) of the same kind in one class.

> **Example:**
>
> The `Animal` class encapsulates attributes (`name`, `race`) and methods (`eat()`, `sleep()`) together within one class.
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

## 🌐 3. Coherence: 
Intra module relationships within a class.

> **Example:**
>
> In the `Animal` class, the `name` and `race` attributes and the methods `eat()`, `sleep()` and `makeSound()` are all related and belong to the same class module, showing strong intra-module cohesion.
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

## 👁️ 4. Information hiding: 
Hide sensitive information from the user by:
- declare class variables/attributes as private.
- provide public getters and setters to access the data.

> **Example:**
>
> The `name` attribute is private, and it can only be accessed or modified using the public `getName()` and `setName()` methods.
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
class Animal {
    // Class Attributes
    private String name;
    private String race;

    // Class Constructors
    public Animal() {}

    public Animal(String name) {
        this.name = name; // 'this.name' refer to the instance variable
    }

    public Animal(String name, String race) {
        this.name = name; // 'this.name' refer to the instance variable
        this.race = race; // 'this.race' refer to the instance variable
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
        this.name = newName;
    }

    public void setRace(String newRace) {
        this.race = newRace;
    }
}
```

## 👨‍👦 5. Inheritance:
Inheriting attributes and methods from one class to another.
- *superclass (parent):* the class being inherited from.
- *subclass (child):* the class that inherits from another class.

> **Example:**
>
> The `Dog` class inherits from the `Animal` class, so it gets the `eat()` and `sleep()` methods, and it can also add its own methods, like `bark()`.
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
class Dog extends Animal {
    // Class constructor
    public Dog(String name, String race){
      super(name,race); // call the Animal super class constructor
    }
    public void bark() {
        System.out.println("WOUF!");
    }
}
```

## 👨‍👦‍👦 6. Polymorphism:
Many classes related to each other by inheritance.
- *Overriding:* Two methods have the same name and same parameters.

> **Example:**
>
> Both `Dog` and `Cat` classes override the `makeSound()` method, but each class implements it differently. The type of object determines which version of the method is called.
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
class Animal {
    public void makeSound() {
        System.out.println("Say something...");
    }
}
```
```java
class Dog extends Animal {
    // Class constructor
    public Dog(String name, String race){
      super(name,race); // call the Animal super class constructor
    }
    @Override
    public void makeSound() {
        System.out.println(super.getName() + " the " + super.getRace() + ": WOUF!");
    }
}
```
```java
class Cat extends Animal {
    // Class constructor
    public Cat(String name, String race){
      super(name,race); // call the Animal super class constructor
    }
    @Override
    public void makeSound() {
        System.out.println(super.getName() + " the " + super.getRace() + ": MEOW!");
    }
}
```
## 🗔 7. Abstraction: 
Hiding certain details by:
- *creating abstract classes:* A class that cannot be instantiated and may have both abstract (unimplemented) and concrete (implemented) methods.

> **Example:**
>
> The `Animal` class is abstract with an abstract method `makeSound()`. The `Dog` class implements this method.
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

> **Example:**
>
> `Animal` is an interface with tree methods: `makeSound()`, `eat()` and `sleep()`.
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
## 🔗 8. Coupling:
Inter module relationships between classes (one class depends on the other).

> **Example:**
>
> `Animal` and `Food` are coupled, meaning that `Animal` depends on `Food` for some behavior or data, in that case `Animal` `eat(something:Food)`, creating a relationship between them.
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
class Food {
    private String type;
    private int quantity;
    // Class constructor
    public Food(String type, int quantity){
      this.type = type;
      this.quantity = quantity;
    }
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
        System.out.println(name + " the " + race + ": Miam Miam! *eats "+something.getQuantity()+" "+something.getType()+"*");
    }
}
```

## 🗍 9. Overloading: 
Two or more methods in the same class have the same name but different parameters (signature).

> **Example:**
>
> The `Addition` class has several `add()` methods with different parameters (`int` and `double`), which allows different combinations of input.
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
class Addition {
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

## 🗇 10. Shadowing: 
Variable declared within a specific scope has the same name as a variable declared in an outer scope.

> **Example:**
>
> The *InnerScope* method `add()` has a `value` variable that shadows the `value` variable declared in the *OuterScope* class `Addition`, meaning the InnerScope version takes precedence within its scope.
```java
class Addition {
    public int value = 5;  // Class-level variable
    public int add(int nbr1, int nbr2) {
        int value = nbr1 + nbr2;  // Method variable, shadows the class-level variable
        return value;
    }
}
```

## 🏃 11. the Main Class:
The `Main` class typically contains the entry point to a Java program, the `main()` method. This is where the program starts executing.

> **Example:**
>
> The `Main` class demonstrates how to create instances of an `Addition` classe, call methods `add()`, and access attribute `value`.
```java
public class Main {
    public static void main(String[] args) {
      Addition addition = new Addition();
      System.out.println(addition.add(1,2));
      System.out.println(addition.value);
      System.out.println(addition.add(1.5,2.5));
      System.out.println(addition.add(1,2,3));
    }
}

```
