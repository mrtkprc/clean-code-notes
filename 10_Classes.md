### [Return to Home](README.md)

# 10-) Classess

## Single Responsibility Principle

### Classes should have one resposibility - one reason to change.

### **Cohesion**

Classess should have a small number of instance variables. Each of the methods of a class should manipulate one or more of those variables. A class in which each variable is used by each method is maximally cohesive.

When cohesion is high, it means that the methods and variables of the class are co-dependent and hang together as a logical whole.

### The strategy of keeping function smal and keeping parameter lists short can sometimes lead to a proliferation of instance variables that are used by a subset of methods. 
>### Solution: Seperate to classes.

#
# Maintaining Cohesion Results in Many Small Classes

>## If we promoted those four variables to instance variables of the class, then we could extract code without passing any variables at all.

>### In ideal system, we incorporate new features by extending the system, not by making modifications to existing code.






