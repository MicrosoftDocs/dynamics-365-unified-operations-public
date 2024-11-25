---
title: X++ loop statements
description: Learn about loop statements in X++, including outlines and examples for the for, while, and do...while loop statements.
author: josaw1
ms.author: josaw
ms.topic: article
ms.date: 06/17/2019
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
ms.devlang: xpp
---

# X++ loop statements

[!include [banner](../includes/banner.md)]

This article describes loop statements in X++. 

There are three loop statements: **for**, **while**, and **do**...**while**. A loop repeats its statement until the condition that is set for the loop is **false**. Within the loop statements, you can use **break** and **continue** statements.

## for loops

The syntax of a **for** loop is:

**for (** *initialization* **;** *test* **;** *increment* **) {** *statement* **}**

The **for** loop repeatedly executes **statement** for as long as the conditional expression *test* is **true**. *statement* can be a block of statements. The body of the **for** loop (*statement*) might be executed zero or more times, depending on the results of *test*. 

A **for** loop differs from other loops because an initial value can be assigned to a control variable, and because there is a statement for incrementing or decrementing the variable. These additions make a **for** loop especially useful for traversing lists, containers, and arrays because they have a fixed number of elements. 

You can also apply a statement to each element and increment your way through the elements, setting the condition to test for the last element.

### Example of a for loop

In the following code example, the items in an array of integers are printed.

```xpp
int integers[10];
for (int i = 0; i < 10; i++)
{
    info(int2str(integers[i]));
}
// The output is a series of 0's.
```

## while loops

The syntax of a **while** loop is:

**while (** *expression* **)** *statement*

A **while** loop repeatedly executes *statement* for as long as the conditional *expression* is **true**. *statement* can be replaced by a block of statements. *statement* is executed as many times as the condition is met (zero to many). 

### Example of a while loop

The following code example demonstrates a **while** loop that traverses a container and prints out the contents of the container.

```xpp
container cont = ["one", "two", "three"];
int no = 1;
while (no <= conlen(cont))
{
    info(conPeek(cont, no));
    no++;
}
// The output is "one", "two", "three".
```

## do...while loops

The syntax of the **do...while** loop is:

**do {** *statement* **} while (** *expression* **) ;**

The **do**...**while** loop is similar to the **while** loop, but the condition appears after the *statement* that must be executed. *statement* can be a block of statements. The *statement* is always executed at least one time, because the condition is tested after *statement* is executed. The **do**...**while** loop is well-suited to tasks that must always be done at least one time, such as getting parameters for a report. 

### Example of a do...while loop

The following code example finds the smallest power of 10 that is larger than `realNumber`.

```xpp
int FindPower(real realNumber)
{
    int exponent = -1;
    real curVal;

    do
    {
        exponent++;
        curVal = power(10, exponent);
    }
    while (realNumber > curVal);

    return exponent;
}
```

## continue statement

The **continue** statement causes execution to move directly to the next iteration of a **for**, **while**, or **do**...**while** loop. For **do** or **while**, the test is executed immediately. For a **for** statement, the increment step is executed. 

### Example of a continue statement

In the following code example, if `Iarray[i] <= 0`, the remaining statements in the loop are not executed, and `i` is incremented before the **if** statement is tried again.

```xpp
int Iarray[100];
for (int i = 0; i < 100; i++)
{
    if (Iarray[i] <= 0)
    {
        Info("Will continue.");
        continue;
    }

    info("Did not continue.");
}
// The output is "Will continue." for all 100 interations.
```

## break statement

The **break** statement within a loop is used to terminate that loop. Execution then moves to the first statement after the loop.

### Example of a break statement

This example uses a **break** statement within a **while** loop. When used within a loop, the loop is terminated and execution continues from the statement following the loop. This works for **do... while** and **for** loops as well. 

```xpp
var mainMenu = SysDictMenu::newMainMenu();
var enum = mainMenu.getEnumerator();
var found = false;
while (enum.moveNext())
{
    var menuItem = enum.current();
    if (menuItem.label() == "StringOfInterest")
    {
        found = true;
        break;
    }
}
if (found) 
{
    // do something
}
```


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
