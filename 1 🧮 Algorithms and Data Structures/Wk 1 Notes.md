## Data Types / Operators

### Privative Data Types
![[Pasted image 20230116203121.png]]



Comparison in Java is ==

Short circuit features

use **final** to declare constants

final int DAYHOURS=24;

**BODMAS** order of operations

Java will round integer division

```pseudocode
7/4 (assigned to a 'real' variable) = 1.0 
```

### Special assignment operators

-   **m+=3** same as m=m+3
-   **m*=2** same as m=m*2
-   **++** increment
-   **--** decrement

### Boolean Operations

-   Logical AND **&&**
-   Logical OR **||**
-   Logical NOT **!**

Add L to end of longs eg:
```java
long chinaPopulation = 1426000000000L; 
```

explanation here [Fixing the “java: integer number too large” Error Links to an external site.](https://www.baeldung.com/java-integer-number-too-large-error "Link")

## Conditionals

### If / Else / Else if
```java
if (expression) {
  // Code to run if expression is true
}
```

```java
if (expression) {  
  // Code to run if expression is true  
} else if (expression) {  
  // Code to run if previous expression is false and current condition is true  
} else if (expression) {  
  // Code to run if previous expression is false and current condition is true  
} else {  
  // Code to run if all previous expressions are false  
}
```


### Switch / Case
```java
switch(expression) {
  case x:
    // code block
    break;
  case y:
    // code block
    break;
  default:
    // code block
}
```

## Iteration
### While
```java
int num = 0;
while (num < 20) {
  num = num + 1;
}
System.out.println(num) // Prints: 20
```


### Do While

Always executes once
```java
do {
 System.out.println("2 is equal to 4!");
} while (2 == 4);
// Prints: 2 is equal to 4!
```


### For / Next
```java
for (declare; condition ; action) {
  // code block to be executed
}
```
