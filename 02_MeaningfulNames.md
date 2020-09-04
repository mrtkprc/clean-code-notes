### [Return to Home](README.md)

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