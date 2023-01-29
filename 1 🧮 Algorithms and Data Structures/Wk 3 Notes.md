# Inheritance

JI2S p235-250
JI2S p257-264

-   What are superclasses/subclasses?
-   What does a subclass inherit from a super class?
-   What is sub class specialisation?
-   What is method overriding?
-   Are method overriding and method overloading the same?
-   Can we assign a subclass object to a superclass type?


Inheritance - **"is a kind of"** 

ChequeAccount inherits Account.

## Superclasses & Subclasses

![[Pasted image 20230117134929.png]]

```java
public class ChequeAccount extends Account
```

![[Pasted image 20230117135144.png]]

### Manual Overriding

```java
**_// ChequeAccount's toString method_**  
public String toString()  
{  
    return super.toString() + " ODL : " + odl;  
}
```
Calls the super class toString() and adds the attribs pertinent to the subclass

```java
// Account's  toString method
public String toString()
{
     return  " Balance : " + balance;
}
```

Sub class can can super class method but super class cannot call sub class method.

Inheritance Diagram - Direction of arrow is important

![[Pasted image 20230118010103.png]]

## 3.2 Abstract Classes


```java
public abstract class Employee
```

This class acts as the basis for FullTimeEmployee and PartTimeEmployee - which includes all employees - no employee is a basic Employee.

### Abstract Method

```java
public abstract String GetStatus();
```

This guarantees that every class created from Employee has to have a GetStatus method (has to override the superclass method GetStatus).

### JavaFX

_heavyweight_ - make use of system resources
_lightweight_ - does not rely on system components

![[Pasted image 20230119090542.png]]

![[Pasted image 20230119090723.png]]

start() is an abstract method of JavaFX application so you have to write one

When run from command line - doesn't need main method
For IDE it does so this format.

```java
public static void main(String[] args) { 
	launch(args); 
	}
```

`launch` is a **static method** of JavaFX Application.


#### Event Handling

```java
smileButton.setOnAction(e -> mouth.setLength(-180));
```

`setOnAction` - _convenience method_ 
**Lambda Expression** - allow sending of code into a method as an argument

## Packages

### Reading

-   What is a package?

**Package** is a _named collection of related classes_
Package name corresponds to _name of directory_ in which classes reside

-   What is the purpose of the **import** keyword?
-   Can an **import** statement contain more than one *?
-   What is the purpose of the **package** statement?
-   With regard to visibility control, how do you specify package scope for an attribute, method or a class?
-   What is the consequence for the package scope?
-   What is String args[] in “static void main (String args[])” for?
-   How to create an (executable) jar file using Eclipse?

### Scope

```java
package student;

public class Student

{

// the student's full name

private String name; // CLASS SCOPE

// the student ID

String id; // PACKAGE SC



```