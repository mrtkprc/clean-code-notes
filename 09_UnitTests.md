# 9-) Unit Tests

>### Many programmers have missed some of the more subtle abd important points of writing good tests.

## ***TDD(Test Driven Development) asks to write unit tests first before we write production code***

## Three Laws of TDD

-   ## **First Law:** You may not write production code until you have written failing unit test. 

-   ## **Second Law:** You may not write more of unit tests than is suffucient to fail, and not compiling is failing.

-   ## **Third Law:** You may not write more production code than is sufficient to pass currently failing test.

### These three laws lock you into a cycle that is perphaps thiry seconds long.

## **If we work this way, we will write dozens of tests every day, hundreds of tests every month, and thousands of tests every year.** 

>### **If we work this way, these tests will cover virtually all of our production code.**

#

### The problem is that tests much change as the production code evolves. The dirtier the tests, the harder they are to change. 
#
# ***If you don't keep your tests clean, you will lose them. And without them, you lose the very thing that keeps your production code flexible***

## Clean Tets

What makes a clean test?

-   Readability
-   Readability
-   Readability

> Readability is perhaps even more important in unit tests than it is in production code.

> Test code must be still be simple, succinct and expressive, but it need not be efficient as production code.

## **One assert per Test:** 
Not applicable because a lot of codes exist. However, Those tests come to a single conclusion that is quick and easy to understand.

## **Single Concept per Test:**
Perhaps better rule is that we want to test a single concept in each test function.

> Best rule is that you should minimize the number of assert per concept and test just are concept per test function.

## Clean Test Rules (F.I.R.S.T):

-   F: Fast
-   I: Independent
-   R: Repeatable
-   S: Self-validating
-   T: Timely

