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



\_\_

