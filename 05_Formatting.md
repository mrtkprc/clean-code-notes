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
