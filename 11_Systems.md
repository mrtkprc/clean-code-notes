### [Return to Home](README.md)

# 11-) Systems

>## Complexity kills. It sucks the life out of developers, it makes products difficult to plan, build and test.

Ray Ozzie, CTO, Microsoft Corporation

The main function builds the objects necessary for the system, then passes them to applicaiton.

We can use ***Abstract factory*** pattern to give application control of when to build the items, but keep the details of that construction separate from the application code.

### Object should not take reponsibility for instatiating dependencies itself.

