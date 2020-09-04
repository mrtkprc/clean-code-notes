### [Return to Home](README.md)

# 17-) Smells And Heuristics

### ***This chapter presents general overview concepts in explained the book.***

## Comments

>- ### Comments should be reserved for technical notes about the code and design.

>- ### Comments get old quickly

>- ### Comments should say things that the code cannot say for itself.

>- ### Commented out code is an abomination

## General

> # **The Pricinple of Least Surprise:** Any function or class should implement the behaviours that another programmer could reasonably expect.


>- ### Dont rely on your intution. Look for every boundry condition.

>- ### Turning off certain compiler warnings may help you get the build to succeed, ***but at the risk of endless debugging sessions.***

>- ### Don't repeat yourself.(DRY)

>- ### Local variables should be declared just above their first usage.

>- ### If you do something a certain way, do all similar thing in the same way.

>- ### General enums should not be contained within more specific classes.

>- ### Don't use selector arguments for functions such as boolean argument.

>- ### Function names should say what they do.

```
    // 5 is day, month, year ?
    Data newDate = date.add(5)

```

>- ### Prefer polymorphism to if/else or switch/case

>- ### Avoid Negative Conditionals

>- ### Functions do one thing.

```
public void pay(){

    for(Employee e : employees){
        if(e.isPayday()){
            Money pay = e.calculationPay();
            e.deliveryPay(pay);
        }
    }
}

```
This code does three things.

>- It loops over all employees.
>- Checks to see whether each employee out to be paid
>- Then pays the employee.

**This code would be better written as**

```
public void pay(){
    for(Employee e : employees){
        payIfNecessary(e);
    }
}

private void payIfNecessary(e){
    if(e.isPayday()){
        calculateAndDeliveryPay(e);
    }
}
private void calculateAndDeliveryPay(Employee e){
    Money pay = e.calculatePay();
    e.deliveryPay(pay);
}
```

>- ### Names should be describe side-effects.

```
public ObjectOutputStream getOos() throws IOException{
    if(m_oos == null){
        m_oos = new ObjectOutputStream(...);
    }

    return m_oos;
}
```

## Function name could be createOrReturnOos();

>- ### Exhaustively Test Near Bugs.

#### When you find a bug in function, it is wise to do an exhaustive test of that function. You'll probably find that bug was not alone.



