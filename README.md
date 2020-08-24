# clean-code-notes

![](./images/wtf.png "Clean Code Cover")

# 1-) Clean Code: 

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

# 2-) Meaningful Names:

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


# 3-) Functions

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

## Use Descriptive Names

>- Don't be afraid to make a name long. 
>- Long description name is better than a long descriptive comments.

## Function Arguments

The ideal number of arguments for a function is zero. 

### **Three arguments should be avoided where possible**

> More than three arguments requires very special justification and **there shouldn't be used anyway**

### If a function is going to transform its input argument, transformation should appear as return value.

### Passing a boolean into a function is a truly terrible practice.

> The parts we ignore are where bugs will hide.

## Have No Side Effects

```
public class UserValidator {
    private Cryptographer cryptographer;
    public boolean checkPassword(String username, String password){
        User user = UserGatewat.findByName(username);

        if(user != User.NULL){
            String codedPhrase = user.getPhraseEncodedByPassword();
            String phrase = cryptographer.decrypt(codedPhrase, password);
            
            if("Valid Password").equals(phrase){
                ***Session.initialize();***(Side Effect here)
                return true;
            }
        }
        return false;
    }
}

=> The function name doesn't imply that it initializes the sesion.

```

## Output Arguments

Arguments are most naturally interpreted as inputs to a function. 

``appendFooter(s);``

>- Does this function append s as the footer to something?

or

>- Does it append some footer to s?

## Anything that forces you to check the function signature is equivalent to a double-take.

## Command Query Seperation 

``public boolean set(String attribute, String value)``

```
if(set("username","unclebob")) {
    //...
}
```
Imagine this from point of view of the reader. **What does it mean?**

>- Is it asking whether the username attribute was previously set to "unclebob"?

or

>* Is it asking whether the "username" attribute was successfully set to "unclebob"?

We could try to resolve this by renaming the set function to ``setAndCheckIfExists``, but that doesn't much help readibility of the if statement.
***The real solution is to seperate the command from the query so that ambiguity cannot occur***

```
if(attributeExists("username")){
    setAttribute("username","unclebob");
}
```

### Function should either do something or answering something, ***but not both***

## Prefer Exceptions to Returning Error Codes

> # Duplication may be the root of all evil in software. Many principles and practices have been created the purposes of controlling or eliminating it.


## Functions are verbs while classes are nouns.

# 4-) Comments

 ***Brain W. Kernighan and P.J. Plaugher says:***
> Don't comment bad code - rewrite it. 

### Every time you express yourself in code, you should pat yourself on the back.

### Every time you write a comment, you should grimace and feel the failure of your ability of expression.


### **Code changes and evolves. Chunks of it move from here to there. Those chunks bifurcate and reproduced and come together againt to form chimeras (Ateş Püsküren Canavar in Turkish)**

![](./images/charisard.jpg "Clean Code Cover")

### Inaccurate comments are far worse than no comments at all. 

### Truth can only found in one place: ***the code*** 

## Explain yourself in code.

```
//Check to see if the employee is eligible for full benefit
if(employee.flags && HOURLY_FLAG && employee.age > 65)
{
    //do sth
}

or

if(employee.isEligibleForFullBenefits())
```

Which one is better ?

## Good Comments

>- Legal comments
>- Informative comments
>- Explanation of Intent
```
public int compareTo(Object o){
    if(o instanceof WikiPagePath){
        //...
    }
    return 1 // we are greater because we are the right type.
}
```

>- Clarification

```
public void testCompareTo() {
    //...

    assertTrue(a.compareTo(a) == 0) // a == a
    assertTrue(a.compareTo(b) != 0) // a != b
}
```

>- Todo comments
>- Amplification

```
String listItemContent = match.group(1).trim();
/*
the trim is real important. It removes the starting spaces that could cause item to be recognized as another list.
*/
new ListItemWidget(this, listItemContent, this.level + 1);
return buildList(text.substring(match.end()));

```

## Bad Comments

>- Mumbling
>- Redundant Comments
```
/*
Utility method that returns when this.closed is true. Throws an exception if the timeout is reached.
*/
public synchorinized void waitForClose(final long timeoutMillis){

}
```
>- Journal Comments
>- Noise comments

``protected AnnualDateRule()``

No, really? Or how about this:

``` 
// The day of the month
private int dayOfMonth 
```

>- Scary Noise

![](./images/scary_noise.jpg "Scary Noise")

```
//The name
private string name;

//The version
private string version;

//...
```
>- Commented-Out Code

Others who see commented-out code won't have the courage to delete it. They will think it is there for a reason and is too important to delete.

## Short functions don't need much description. A well-chosen name for a small function that does one thing is usually better than a comment header.

# 5-) Formatting

Code formatting is important. It is too important to ignore and it is too important to treat **religiously**.

We would like a source file to be like a newspaper article. 
>- The name should be simple but explanatory.
>- The name, by itself, should be sufficient to tell us whether we are in the right module or not.
>- The topmost part of the source file should provide the high-level concepts and algorithms.
>- Detail should increase as we move downward.

## Concepts that are closely related should be kept vertically close to each other.

### This is frustrating because you are trying to understand what the system does, but you are spending your time and mental energy on trying to locate and remember where the pieces are. 

![](./images/detective.jpg "Detective")

## **Variable Declarations:** Variables should be declared as close to their usage as possible. 

### If one function calls another, they should be vertically close, and caller should be above callee, if at all possible.

## Readers will be able to trust that function definitions will follow shortly after their use.

