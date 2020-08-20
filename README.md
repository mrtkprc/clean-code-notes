# clean-code-notes

![](./images/wtf.png "Clean Code Cover")

# Clean Code: 

## Bad Code

>I know of one company that, in the late 80s, wrote a killer app. It was very popular, and lots of professionals bought and used it. But then the release cycles began to stretch. Bugs were not repaired from one release to the next. Load times grew and crashes increased. I remember the day I shut the product down in frustration and never used it again. The company went out of business a short time after that.

>Two decades later I met one of the early employees of that company and asked him what had happened. The answer confirmed my fears. They had rushed the product to market and had made a huge mess in the code. As they added more and more features, the code got worse and worse until they simply could not manage it any longer. It was the bad code that brought the company down.


## **LeBlanc's Law (Later Equals Never)**
We’ve all looked at the mess we’ve just made and then have chosen to leave it for another day. We’ve all felt the relief of seeing our messy program work and deciding that a working mess is better than nothing. We’ve all said we’d go back and clean it up later. Of course, in those days we didn’t know LeBlanc’s law: **Later Equals Never.**

### The only way to make the deadline - **the only way** to go fast- is to keep code as clean as possible at all times.

## What Is Clean Code?

> Bjarne Stroustrup: The logic should be straightforward to make it hard for bugs to hide.

> Grady Booch: Clean code never obscures the designer's intent.

> Dave Thomas: Clean code can be read and enhanced by a developer other than its original author. It has **unit and acceptance tests**.

## **Code without tests is not clean.**

# Meaningful Names:

**Choosing good names takes time but saves more than it takes.**

The name of a variable, function or class should answer all the big questions. It should tell you 
> - why it exists, 
> - what it does, 
> - how it is used.

## ***If a name requires a comment, the name does not reveal its intent***


```
public static void copyChars(char a1[], char a2[])
{
    ...
}

a1 and a2 are noninformative, they provide no clue to the author's intention.
```

## Class Names

Classes and objects should have noun or nound phrase names like ``Customer``, ``WikiPage``, ``Account`` and ``AddressParser``. A class name should not be a verb.

## Method Names

Methods should have verb or verb phrase names like ``postPayment``, ``deletePage`` or ``save``. 

When constructors are overloaded, use static factory methods with names that describe the arguments. For example,

```
Complex fulcrumPoint = Complex.FromRealNumber(23.0);
```

**is generally better than**

```
Complex fulcrumPoint = new Complex(23.0);
```

## Pick One Word per Concept

Pick one word for one abstract concept and stick with it. For instance, it's confusing to have ``fetch``, ``retrieve`` and ``get`` as equivalent of different classes. 

### **Use refactoring tools whenever you see bad code. This process might be painfull in short time; however, it will be beneficial in the future.**


## Functions

## ***The first rule of functions is that they should be small!!!***

> In 1999 I went to visit Kent Beck at his home in Ore-gon. We sat down and did some programming together. When Kent showed me the code, I was struck by how small all the functions were. Every function in this program was just two, or three, or four lines long. Each was transparently obvious. Each told a story. And each led you to the next in a compelling order. That's how short your functions should be!

>- Functions should hardly ever be 20 lines long.
>- Functions should not be 100 lines long.

## *Indent of level of a function should not be greater than one or two.*

## Do One Thing

>- Functions should do one thing. 
>- They should do it well. 
>- They should do it only.

### It is the key to keeping functions short and making sure they do ***one thing***.

## Switch statements

It's hard to make a small ``switch`` statement. It's also hard to make a ``switch`` statement that does one thing. By their nature, ``switch`` statements always do ***N*** thing. Unfortunately we can't always avoid ``switch`` statements, but we can make sure that each ``switch`` statement is burried in a low-level class and is never repeated. We do this, of course, with ***polymorphism.***

```
public Money calculatePay(Employee e) throws InvalidEmployee {
    switch(e.type){
        case COMMISSIONED:
            return calculateCommissionedPay(e);
        case HOURLY:
            return calculateHourlyPay(e);
        case SALARIED:
            return calculateSalariedPay(e);
        default:
            throw new InvalidEmployeeType(e.type);
    }
}

```
## There are several problems with this function. 
>- It's large and when employee types are added. It will grow.
>- It very clearly does more than one thing.
>- It violates the Single Responsibility Problem (SRP) there is more than one reason for it to change.
>- It violates the Open Closed Principle (OCP) because it must change whenever new types are added.

But possibly the worst problem with this function is that there are an unlimited number of other functions that will have same structure. For example, we could have:

> ``deliveryPay(Employee e, Money pay)``

## **The solution**:  Burry the switch statement in the basement of **Abstract Factory** and never let anyone see it.

> General Rule: Switch statements is that they can be tolerated if they appear only once, are used to create ***polymorphic objects*** are hidden behind an inheritance relationship so that the rest of system can't see them.





