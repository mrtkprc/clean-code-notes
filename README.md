# clean-code-notes

![](./images/wtf.png "Clean Code Cover")

# Clean Code: 

## Bad Code

I know of one company that, in the late 80s, wrote a killer app. It was very popular, and lots of professionals bought and used it. But then the release cycles began to stretch. Bugs were not repaired from one release to the next. Load times grew and crashes increased. I remember the day I shut the product down in frustration and never used it again. The company went out of business a short time after that.

Two decades later I met one of the early employees of that company and asked him what had happened. The answer confirmed my fears. They had rushed the product to market and had made a huge mess in the code. As they added more and more features, the code got worse and worse until they simply could not manage it any longer. It was the bad code that brought the company down.


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





