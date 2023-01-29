
## Java Methods
### Calling methods

**public** - available outside class. Interface for class.
**void** doesn't return anything

```pseudocode
return-value-type method-name(parameter-list)
{
      declarations and statements
}
```

**formal parameters** requies name and type, separated by commas
**acutal parameters** values sent to the method

### Syntax Example for user input (Scanner class)
```java
public void promptSettings()
    {
    /* Purpose: Demonstrate input techniques using Scanner
    */ 
      
      //Create a new scanner object to receive input from the keyboard
      Scanner sc=new Scanner(System.in);
      
      System.out.println("Enter a warning level (L,M,H) and press return ");
      warningLevel = sc.next().charAt(0);
    
      System.out.println("Enter Warp Factor (2 - 10) ");
      warpFactor = sc.nextInt();
    
      System.out.println("Enter Star Speed ");
      starSpeed = sc.nextDouble();
      
      System.out.println("Now inspect the object and see whether the relevant attributes have been updated ");
}
```

## Objects And Classes
### Encapsulation

**instance** - objects of type class
**attribues** - data
**methods** - actions that can manipuate attributes the **interface** of the class

**Encapsulation** - allows a buffer between the class and the outside world, controlling access to attributes of the class.

**Message Passing** - using another objects methods.

**Getters** and **setters** to implement encapsulation - sometimes called **mutators** and **accessors**

### How does a new object affect memory space?

```java
Oblong myOblong;
```

Creates a **reference** (name for a location in memory) to an object. To create memory for object class must be **instantiated** by calling the **constructor**

_Memory is freed by assigning it a **null**_

Constructor always has the same name as the class and always runs when the class is instantiated. It can run code and receive parameters:
```java
myOblong = new Oblong(7.5, 12.5);
```
can be declared and instantiated on the same line

```java
Oblong myOblong = new Oblong(7.5, 12.5);
```
**this** keyword used when referring to same class as method - can be assumed


### How many ways can you create a string object?

**String** is the only object that allows creation using the assignment operator.

```java
	String name;
```  

```java
	String name = "John";
```  

```java
	String name = new String("John")
```  

_Compare strings using **.equals** method, *==* operator can only be used with primitive data types_

_**compareTo** method returns 0 if the same, negative if earlier alphabetically, 1 if later_ **<- Useful for sorting**

_declare a separate scanner object for strings with spaces and use **Scanner.nextLine**_

### What is parameter passing by reference?

**Pass-by-Value** a clone of the original parameter is sent to the object

**Pass-by-Reference** the caller and callee operate on the same object - the _unique identifier_ of the object is sent to the method.

## Implementing Classes

### Unified Modelling Language

**Class design** is how the system would be built to meet the specifications

Class = box in three sections

**Class names** always have a capital letter

- name
- attributes
- methods

**-**length: double   <-- Private attribute
**+**getHeight(): double   <--- Public method

_**constructors** never have a return type_ - doesn't even require the _void_ keyword

Good policy to only provide write access only to attributes that need to change during the objects lifetime.

```java
private double length;
private double height;
```

**private** corresponds to the minus sign in the UML diagram

If user-defined constructor exists - **default constructor** is no longer automatically available, so needs to be defined if you want to use it:
```java
public Oblong() {
}
```

A class can have **several contructors** and are identified by the parameter list.

Attributes of one class can be objects of another class.

### _Static_ Keyword

is a **modifier** - determines the way a class, attribute or method is accessed.

Any change to a **static** attribute change all objects of that class  - a **class variable**

_example: interest rate is the same for all bank accounts, but isn't a constant it does still change_

Static methods call be called using just the **class name** - doesn't have to be the object instance name.
Use static getters and setters for static attributes.

	int number = EasyScanner.nextInt();

**QUESTION** - are objects always passed by reference and primitive always by value??

**instance methods** from an instance we create (public methods)
**Class methods** (static keyword) and can be references from the class name e.g.

```java
System.out.println("");
Math.random();
```

Setters and getters don't have to be declared as static for static attibutes.

Class methods may be useful where calss attributes don't need to be manipulates (see examples above), or checking something is valid.

Can be useful because don't need to create an instance to use them

### JOptionPane for GUI Example

```java
import javax.swing.JOptionPane;  // import class JOptionPane  
  
public class GUI_IO   
{  
   String name = "default name";  
  
  
  //Use basic showMessageDialog  
   public void basicMessage()  
   {  
      //The 'null' parameter means centre the dialog box.  
      //Notice how we can use \n to create new lines  
      JOptionPane.showMessageDialog(null, "Welcome\nto\nJava\nProgramming!" );  
   }  
     
   //Show with a Title bar and a Warning message   
   public void titleBarWarning()  
   {  
      JOptionPane.showMessageDialog(null, "Look out! - don't press that!",  
                                    "A Warning", JOptionPane.WARNING_MESSAGE );  
   }  
  
  
  //Prompt for a name using the showInputDialog method  
   public void basicPromptDisplay()  
   {  
       name = JOptionPane.showInputDialog("What is your name");  
       //Show message  
       JOptionPane.showMessageDialog(null, "Hi " + name + " how do you like these dialog boxes?",   
                                     "A Question", JOptionPane.QUESTION_MESSAGE);  
    }  
}
```
### Initialising Attributes

Java always initialised attributes:
- numerical (int, double) set to **zero**
- boolean set to **false**
- objects set to **null**
- char set to **Unicode zero**

Good practice to initialise 

	private static double interestRate = 0;

## Collections

### Array

Fixed length

```java
// Definition
double[] temperature = new double[7];

// Define and populate
double[] temperature = {9, 12.3, 19.5, 21.2}
```


### ArrayList
- Can **increase capacity** as required
- Keeps a **count** which can be returned with the _size_ method
- Maintains **order**


```java
import java.util.ArrayList; // import the ArrayList class

ArrayList<String> cars = new ArrayList<String>(); // Create an ArrayList object```  

#### Usage
```java
import java.util.ArrayList;

public class Main {
  public static void main(String[] args) {
    ArrayList<String> cars = new ArrayList<String>();
    cars.add("Volvo");
    cars.add("BMW");
    cars.add("Ford");
    cars.add("Mazda");
    System.out.println(cars);
  }
}
```

### Collection Classes
Classeses which contain collections of similar items are called **collection classes*


### Wrapper Classes and Autoboxing

JI2S p259

Primitive data types can't be used in ArrayList 

***wrapper** classes are used 

byte	Byte
short	Short
int		Integer
long	Long
float	Float
double	Double
boolean	Boolean
char	Character



### Questions from book notes
_Do you need to define a default constructor?_ No, but it is disabled if you include a user defined one  
_What is the consequence of using static attribute?_ The value is changed in all intances of the objects  
_What is the difference between a static method and an instance method?_ Static methods can be called used with the base class name  
_What is a wrapper class and how many do we have in Java?_ 8  




