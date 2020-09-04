### [Return to Home](README.md)

# 6-) Objects And Data Structures

## Procedural code makes it easy to add new functions without changing the existing data structures.

## **Object Oriented code make it easy to add new classes without changing existing functions**

> ### The worst option is to blithely add getters and setters

## Law of Demeter

The Law of Demeter says that a method ***f*** of a class ***C*** should only call the methods of these:

>- ***C***
>- An object created by ***f***
>- An object passed as argument to ***f***
>- An object held in an instance variable of C

### The method should not invoke methods on objects that are returned by any of the allowed functions. ***In other words, talk to friends, not to strangers.***

## Train Wrecks

```
String outputDir = ctxt.getOptions().getScratchDir().getAbsolutePath();
```

### **Data Transfer Objects:** The quintessential form of a data structure is a class with public variables and no functions. 

