### [Return to Home](README.md)

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