### [Return to Home](README.md)

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