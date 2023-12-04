# UML Sequence Diagram

## Introduction

**What is Sequence Diagram -- by ChatGPT**

A Sequence Diagram is a type of interaction diagram that is part of the Unified Modeling Language (UML). Sequence diagrams are extensively used to represent interactions among objects. They primarily illustrate the order in which messages pass between objects, which can be synchronous or asynchronous.

A sequence diagram consists of the following main components:

- **Objects**: These are usually arranged horizontally at the top of the diagram and are represented by vertical dashed lines. The name of the object is generally written above or below the horizontal line.
- **Lifelines**: These represent the time during which an object exists. This is a vertical dashed line extending downwards from the object.
- **Activation bars**: These represent the period during which an object is performing an action. It is a rectangle drawn on the lifeline.
- **Messages**: These represent communication between objects and are represented by horizontal lines with arrows. The arrow points towards the object that receives the message.
- **Return Messages**: These represent the result of a method/action and are typically represented by dashed lines with arrows.

The main usage of sequence diagrams is to help teams understand how objects within a system interact to perform a specific business process or use case.



Two-dimensional diagram 

Horizontal axis: involved interaction partners

Vertical axis: chronological order of the interaction

Interaction = sequence of event specifications



Interaction partners are depicted as lifelines

**Head of the lifeline:**

Rectangle that contains the expression **roleName:Class**



**Body of the lifeline:** 

Vertical, usually dashed line

Represents the lifetime of the object associated with it



**Execution specification:**

Continuous bar

Used to visualize when an interaction partner executes some behavior



![截屏2023-12-04 下午8.50.14的副本](https://raw.githubusercontent.com/Rookie-Frank/Picture/main/%E6%88%AA%E5%B1%8F2023-12-04%20%E4%B8%8B%E5%8D%888.50.14%E7%9A%84%E5%89%AF%E6%9C%AC.png)



##Message

**Synchronous message**

Sender waits until it has received a response message before continuing

![image-20231204212608209](https://raw.githubusercontent.com/Rookie-Frank/Picture/main/image-20231204212608209.png)



**Asynchronous message**

Sender continues without waiting for a response message

![image-20231204212826063](https://raw.githubusercontent.com/Rookie-Frank/Picture/main/image-20231204212826063.png)



**Response message**

May be omitted if content and location are obvious

![image-20231204212921817](https://raw.githubusercontent.com/Rookie-Frank/Picture/main/image-20231204212921817.png)



**Object creation**

Dashed arrow

Arrowhead points to the head of the lifeline of the object to be created

Keyword **new**

![image-20231204213742464](https://raw.githubusercontent.com/Rookie-Frank/Picture/main/image-20231204213742464.png)



**Object destruction**

Object is deleted

Large cross (×) at the end of the lifeline

![image-20231204213805100](https://raw.githubusercontent.com/Rookie-Frank/Picture/main/image-20231204213805100.png)



## Combined Fragments



**alt** **Fragment**

To model alternative sequences

Similar to switch statement in Java

Guards are used to select the one path to be executed

Guards

Modeled in square brackets

default: true

predefined: [else]

Multiple operands

Guards have to be disjoint to avoid indeterministic behavior



**opt** **Fragment**

To model an optional sequence

Actual execution at runtime is dependent on the guard

Exactly one operand

Similar to **if** statement without **else** branch

equivalent to **alt** fragment with two operands, one of which is empty



![image-20231204214440744](https://raw.githubusercontent.com/Rookie-Frank/Picture/main/image-20231204214440744.png)



**loop** **Fragment**

To express that a sequence is to be executed repeatedly

Exactly one operand

Keyword loop followed by the minimal/maximal number of iterations (**min..max**) or (**min,max**)

default: (*) .. no upper limit

Guard 

Evaluated as soon as the minimum number of iterations has taken place

Checked for each iteration within the (min,max) limits

If the guard evaluates to false, the execution of the loop is terminated



**break** **Fragment**

Simple form of exception handling

Exactly one operand with a guard

If the guard is true:

Interactions within this operand are executed

Remaining operations of the surrounding fragment are omitted

Interaction continues in the next higher level fragment

Different behavior than **opt** fragment



![image-20231205030444256](https://raw.githubusercontent.com/Rookie-Frank/Picture/main/image-20231205030444256.png)





## Example

**Description**

•1: The ATM customer actor inserts the ATM card into the Card reader. The card input is read by the Card Reader Interface object

•1.1: The Card Reader Interface object sends the Card Input Data, containing Card ID and Expiration Date to the entity object ATM Card.

•1.2: Card Reader Interface sends the Card Inserted event to ATM Control

•1.3: ATM Control sends the Get PIN event to Customer Interface

•1.4: Customer Interface displays the Pin Prompt to the ATM Customer actor

•2: ATM Customer inputs the PIN number to the Customer Interface object.

•2.1: Customer Interface requests Card Data from ATM Card.

•2.2: ATM Card provides the Card Data to the Customer Interface.

•2.3: Customer Interface sends the Customer Info, containing Card ID, PIN, and Expiration Date, to the ATM Transaction entity object

•2.4: Customer Interface sends the PIN Entered (Customer Info) event to ATM Control. 

•2.5: ATM control sends a Validate PIN (Customer Info) request to the Bank Server

•2.6: Bank Server validates the PIN and sends a Valid PIN response to ATM Control

•2.7: ATM Control sends the Display Menu event to the Customer Interface

•2.7a: ATM Control sends an Update status message to the ATM Transaction

•2.8: Customer Interface displays a menu showing the Withdraw, Query, and Transfer options to the ATM Customer actor



![image-20231205040347626](https://raw.githubusercontent.com/Rookie-Frank/Picture/main/image-20231205040347626.png)











