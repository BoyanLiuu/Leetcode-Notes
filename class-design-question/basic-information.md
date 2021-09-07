# Basic Information

## Classes: and Objects:

* Classes are the building blocks of programs built using the object-oriented methodology. Such programs consist of independent self-managing modules and their interactions.
* Object is an instance of a module, and a class is its definition





## Data Hiding:

* It refers to the concept of hiding the inner workings of a class and simply providing an interface through  which the outside world can interact with the class without knowing what’s going on inside.
* The purpose is to implement classes in such a way that the instances \(objects\) of these classes should not be able to cause any unauthorized access or change in the original contents of a class. One class does not need to know anything about the underlying algorithms of another class. However, the two can still communicate.

### Components of Data Hiding:

* Encapsulation
* Abstraction

#### Encapsulation_:_

* In OOP refers to binding the data and the methods to manipulate that data together in a single unit \(class\).
* Encapsulation is normally done to hide the state and representation of an object from outside. A class can be thought of as a capsule having methods and data members inside it. ![](../.gitbook/assets/image%20%2890%29.png) 
* As a rule of thumb, a good convention is to declare all the data members or instance variables of a class private. This will restrict direct access from the code outside that class.
* At this point, a question can be raised that if the methods and variables are encapsulated in a class then “how can they be used outside of that class”?
* Well, the answer to this is simple. One has to implement public methods to let the outside world communicate with this class. These methods can be getters, setters and any other custom methods implemented by the programmer.
* **Advantages of Encapsulation:**
  * Classes are easier to change and maintain.
  * We can specify which data member we want to keep hidden or accessible.
  * We decide which variables have read/write privileges \(increases flexibility\).

## Inheritance:

Inheritance provides a way to create a new class from an existing class. The new class is a specialized version of the existing class such that it inherits all the non-private fields \(variables\) and methods of the existing class. The existing class is used as a starting point or as a base to create the new class.

* This is IS A relationship
* Child class have all non-private members  defined in the mother class
* In java we use extends keyword
* In Java, a class can extend from only one other class at a time and a class cannot extend itself.

### Super Keyword:

* super keyword in Java is used to refer to the SuperClass members from inside the immediate Subclass. The use of super comes into play when we implement inheritance.
* When you create an Object of a SubClass type at the same time, an Object of SuperClass type is created by calling implicitly the constructor of SuperClass.
* 
![](../.gitbook/assets/image%20%2892%29.png)

* In a constructor we can include a call to super\(\) or this\(\) but not both. Also, these calls can only be used inside the constructors.

### Types of Inheritance:

* Single
  * In single inheritance, there is only a single class extending from another class

![](../.gitbook/assets/image%20%2886%29.png)

* Multi-level:
  * When a class is derived from such a class which itself is derived from another class, this type of inheritance is called Multilevel Inheritance

![](../.gitbook/assets/image%20%2889%29.png)



* Hierarchical
  * When more than one classes inherit from the same class, it is referred to as hierarchical inheritance. In hierarchical inheritance, more than one classes extend, as per the requirement of the design, from the same base class
  * 

![](../.gitbook/assets/image%20%2893%29.png)



* Multiple
  * When a class is derived from more than one base class, i.e. when a class has more than one immediate parent classes, this type of inheritance is called Multiple Inheritance.

![](../.gitbook/assets/image%20%2888%29.png)

* Hybrid
  * A type of inheritance which is a combination of Multiple and Multi-level inheritance is called hybrid inheritance.

![](../.gitbook/assets/image%20%2891%29.png)





**Note: In Java, Multiple and Hybrid inheritance are applicable using interfaces only.**

\*\*\*\*

\*\*\*\*

### **Advantages of Inheritance:**

* Re-usability
* Avoiding Duplication of Code \#
* Extensibility
* Data Hiding: The base class can decide to keep some data private so that it cannot be altered by the derived class.



## OO Analysis and Design:

The process of OO analysis and design can be described as:

1. Identifying the objects in a system;
2. Defining relationships between objects;
3. Establishing the interface of each object; and,
4. Making a design, which can be converted to executables using OO languages.

## What is UML:

Unified Modeling Language and is used to model the Object-Oriented Analysis of a software system

Benefits of using UML:

1. Helps develop a quick understanding of a software system.
2. UML modeling helps in breaking a complex system into discrete pieces that can be easily understood.
3. UML’s graphical notations can be used to communicate design decisions.
4. Since UML is independent of any specific platform or language or technology, it is easier to abstract out concepts.
5. It becomes easier to hand the system over to a new team.

 **Structural UML diagrams**

\*\*\*\*

* Class diagram
* Object diagram
* Package diagram
* Component diagram
* Composite structure diagram
* Deployment diagram
* Profile diagram

 **Behavioral UML diagrams**

* Use case diagram
* Activity diagram
* Sequence diagram
* State diagram
* Communication diagram
* Interaction overview diagram
* Timing diagram

We will focus on these :

### **Use Case Diagram** 

Used to describe a set of user scenarios, this diagram, illustrates the functionality provided by the system.

* It answers what system does from the user point of view.
* It answers What will the system do? and What will the system not do?

#### How to illustrate it?

we ****draw an oval in the middle of the diagram and put the name of the use case in the center of the oval.To show an actor \(indicating a system user\) on a use-case diagram, we draw a stick figure to the left or right of the diagram.

![](../.gitbook/assets/image%20%2894%29.png)

* **System boundary**: A system boundary defines the scope and limits of the system. It is shown as a rectangle that spans all use cases of the system.
* **Actors:** An actor is an entity who performs specific actions. These roles are the actual business roles of the users in a given system. An actor interacts with a use case of the system. For example, in a banking system, the customer is one of the actors.
* **Include:** Include relationship represents an invocation of one use case by another use case. From a coding perspective, it is like one function being called by another function.
* **Extend:** This relationship signifies that the extended use case will work exactly like the base use case, except that some new steps will be inserted in the extended use case.





### **Class Diagram**

 it shows how different entities \(people, things, and data\) relate to each other. In other words, it shows the static structures of the system

The purpose of the class diagram can be summarized as:

1. Analysis and design of the static view of an application;
2. To describe the responsibilities of a system;
3. To provide a base for component and deployment diagrams; and,
4. Forward and reverse engineering.

![](../.gitbook/assets/image%20%2896%29.png)

 **Association:** If two classes in a model need to communicate with each other, there must be a link between them. This link can be represented by an association. Associations can be represented in a class diagram by a line between these classes with an arrow indicating the navigation direction.

* By default, associations are always assumed to be bi-directional; this means that both classes are aware of each other and their relationship. In the diagram below, the association between Pilot and FlightInstance is bi-directional, as both classes know each other.

 **Multiplicity:** Multiplicity indicates how many instances of a class participate in the relationship. It is a constraint that specifies the range of permitted cardinalities between two classes. For example, in the diagram below, one FlightInstance will have two Pilots, while a Pilot can have many FlightInstances. A ranged multiplicity can be expressed as “0…\*” which means “zero to many" or as “2…4” which means “two to four”.

![](../.gitbook/assets/image%20%2895%29.png)

**Aggregation:** Aggregation is a special type of association used to model a “whole to its parts” relationship. In a basic aggregation relationship, the lifecycle of a PART class is independent of the WHOLE class’s lifecycle. In other words, aggregation implies a relationship where the child can exist independently of the parent. In the above diagram, Aircraft can exist without Airline.

**Composition:** The composition aggregation relationship is just another form of the aggregation relationship, but the child class’s instance lifecycle is dependent on the parent class’s instance lifecycle. In other words, Composition implies a relationship where the child cannot exist independent of the parent. In the above example, WeeklySchedule is composed in Flight which means when Flight lifecycle ends, WeeklySchedule automatically gets destroyed.

**Generalization:** Generalization is the mechanism for combining similar classes of objects into a single, more general class. Generalization identifies commonalities among a set of entities. In the above diagram, Crew, Pilot, and Admin, all are Person.

**Dependency:** A dependency relationship is a relationship in which one class, the client, uses or depends on another class, the supplier. In the above diagram, FlightReservation depends on Payment.

**Abstract class:** An abstract class is identified by specifying its name in _italics_. In the above diagram, both Person and Account classes are abstract classes.

![](../.gitbook/assets/image%20%2897%29.png)



### **Sequence Diagram:** 

describe interactions among classes in terms of an exchange of messages over time and are used to explore the logic of complex operations, functions or procedures.

Sequence diagrams show a detailed flow for a specific use case or even just part of a particular use case. They are almost self-explanatory; they show the calls between the different objects in their sequence and can explain, at a detailed level, different calls to various objects

A sequence diagram has two dimensions: The vertical dimension shows the sequence of messages in the chronological order that they occur; the horizontal dimension shows the object instances to which the messages are sent.

![](../.gitbook/assets/image%20%2898%29.png)

A sequence diagram is straightforward to draw. Across the top of your diagram, identify the class instances \(objects\) by putting each class instance inside a box \(see above figure\). If a class instance sends a message to another class instance, draw a line with an open arrowhead pointing to the receiving class instance and place the name of the message above the line. Optionally, for important messages, you can draw a dotted line with an arrowhead pointing back to the originating class instance; label the returned value above the dotted line.

### **Active Diagram:** 

illustrate the flow of control in a system. Activity diagrams illustrate the dynamic nature of a system by modeling the flow of control from activity to activity



 **What is the difference between Activity diagram and Sequence diagram?**

 **Activity diagram** captures the process flow. It is used for functional modeling. A functional model represents the flow of values from external inputs, through operations and internal data stores, to external outputs.

 **Sequence diagram** tracks the interaction between the objects. It is used for dynamic modeling, which is represented by tracking states, transitions between states, and the events that trigger these transitions.

