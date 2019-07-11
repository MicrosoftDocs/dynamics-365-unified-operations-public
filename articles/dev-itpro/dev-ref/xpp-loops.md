---
# required metadata

title: X++ loop statements
description: This topic describes loop statements in X++.
author: RobinARH
manager: AnnBe
ms.date: 06/17/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: robinr
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.custom: 150213
ms.assetid: 16b30ff1-bb31-4f9d-8105-c73abd2455f6
ms.search.region: Global
# ms.search.industry: 
ms.author: robinr
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Loop statements: for, while, and do...while

[!include [banner](../includes/banner.md)]

This topic describes loop statements in X++. There are three loop statements: **for**, **while**, and **do**...**while**. A loop repeats its statement until the condition that is set for the loop is **false**. Within the loop statements, you can use **break** and **continue** statements.

## for loops

The **for** loop repeatedly executes one or more statements for as long as the conditional expression is **true**. The statement is executed as many times as the condition is met. The body of the **for** loop might be executed zero or more times, depending on the results of the condition test. A **for** loop differs from other loops because an initial value can be assigned to a control variable, and because there is a statement for incrementing or decrementing the variable. These additions make a **for** loop especially useful for traversing lists, containers, and arrays, because they have a fixed number of elements. You can also apply a statement to each element and increment your way through the elements, setting the condition to test for the last element. Here is the syntax for a **for** statement:

**for (** *initialization* **;** *test* **;** *increment* **) {** *statement* **}**

*tatement* can be a block of statements.

### Example of a for loop

    // An example where all items are printed in 
    // a fixed array called ra with 100 reals. 
    int ra[100];
    int i; // Control variable.
    for (i=1; i<=100; i+=1)
    {
        print ra[i];
    }

## while loops

A **while** loop repeatedly executes one or more statements for as long as the conditional expression is **true**. The statements are executed as many times as the condition is met (zero to many). Here is the syntax for a **while** loop:

**while (** *expression* **)** *statement*

In this syntax, *statement* can be replaced by a block of statements.

### Example of a while loop

    // This example demonstrates a while loop that traverses 
    // a container, cont, and prints out the contents of the container.
    public static void Iteration()
    {
        container cont;
        int no = 1;
        while (no <= conlen(cont))
        {
            print conpeek(cont,no);
            no = no + 1;
        }
    }

## do...while loops

The **do**...**while** loop is similar to the **while** loop, but the condition appears after the statements that must be executed. The statements are always executed at least one time, because the condition is tested after the statements are executed. The **do**...**while** loop is well-suited to tasks that must always be done at least one time, such as getting parameters for a report. Here is the syntax for a **do**...**while** loop:

**do {** *statement* **} while (** *expression* **) ;**

*tatement* can be a block of statements.

### Example of a do...while loop

    // An example of a do...while loop designed to find 
    // the smallest power of 10 that is larger than _Value.
    int FindPower(real _Value)
    {
        int ex=-1;
        real curVal;
        ;
        do
        {
            ex += 1;
            curVal = power(10, ex);
        }
        while (_Value>curVal);
        return ex;
    }

## continue and break statements

The **continue** statement causes execution to move directly to the next iteration of a **for**, **while**, or **do**...**while** loop. For **do** or **while**, the test is executed immediately. For a **for** statement, the increment step is executed. The **break** statement within a loop is used to terminate that loop. Execution then moves to the first statement after the loop.

### Example of a continue statement

    // An example of a continue statement. 
    // If Iarray[i] <= 0, the remaining statements in the loop are not executed, 
    // and i is incremented before the if statement is tried again.
    int i;
    int Iarray[100];
    for (i=1; i<=100; i++)
    {
        if (Iarray[i] <= 0)
        continue;
        // Some statements.
    }
    
### Example of a break statement


Break statement example within a while loop. When used within a loop, the loop is terminated and execution continues from the statement following the loop. This works for do... while and for loops as well. 

```X++
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
