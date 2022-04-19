---
title: X++ conditional statements
description: This topic describes conditional statements in X++.
author: RobinARH
ms.date: 06/17/2019
audience: Developer
ms.reviewer: tfehr
ms.search.region: Global
ms.author: tfehr
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
---

# X++ conditional statements

[!include [banner](../includes/banner.md)]

This topic describes conditional statements in X++. The conditional statements are **if**, **if**...**else**, **switch**, and the ternary operator (**?**). You use conditional statements to specify whether a block of code is executed. Different conditional statements offer advantages in different situations.

## if and if...else statements

The **if** statement evaluates a conditional expression, and then executes a statement or a set of statements if the conditional expression is evaluated as **true**. You can use the **else** clause to provide an alternative statement or set of statements that is executed if the condition is evaluated as **false**. The syntax for an **if**...**else** statement is:

**if (** *expression* **)** 
    *statement* 
**\[else** 
    *statement* 
**\]**

In this syntax, both occurrences of *statement* can be compound statements (statements enclosed in braces). The *expression* in the parentheses (the conditional expression) can be any valid expression that is evaluated as **true** or **false**. All numbers except 0 (zero) are **true**. All non-empty strings are **true**. You can nest **if** statements. However, if the nesting of **if** statements becomes too deep, you should consider using a **switch** statement instead.

### Examples of if and if...else statements

```xpp
// if statement
if (a > 4)
{
   info("a is greater than 4");
}

// if... else statement 
if (a > 4)
{
   info("a is greater than 4");
}
else
{
   info("a is less than or equal to 4");
}
```

## switch statements

The **switch** statement is a multibranch language construct that has the same behavior as nested **if**. The expression of the **switch** statement is evaluated and checked against each case value. The case values must be constants that the compiler can evaluate. 

- If a case constant matches the **switch** expression, the **case** statement is executed. 
- If the case contains a **break** statement, the program then jumps out of the switch. 
- If the case doesn't contain a **break** statement, the program continues and executes the next **case** statements. 
- If no matches are found, the **default** statement is executed. 
- If there are no matches and no **default** statement, none of the statements inside the **switch** statement are executed. 

Here is the syntax for a **switch** statement:

**switch** **(** *expression* **)** **{** **{ case }** **\[default:** *statement* **\]** **}**

The syntax for a **case** statement is:

**case** *expression* **{ ,** *expression* **} :**
    *statement*

In the syntax for both a **switch** statement and a **case** statement, every occurrence of *statement* can be replaced with a block of statements by enclosing the block in braces ({}).

### Examples of switch statements

When you include the **break** keyword in a switch statement, the execution of the case branch terminates, and the statement following the switch is executed. As shown in the following example, if the Debtor account number is 1000, the program executes "do something", and then continues execution after the switch statement.

```xpp
switch (Debtor.AccountNo)
{
    case "1000":
        // do something
        break;
    case "2000":
        // do something else
        break;
    default:
        // default statement
        break;
}
```

The following code example makes the execution drop through the first case branch by omitting a break statement. If x is 10, b is assigned to a, and d is assigned to c. If x is 11, d is assigned to c. If x is 12, f is assigned to e.

```xpp
 switch (x)
 {
     case 10:
         a = b;
     case 11:
         c = d;
         break;
     case 12:
         e = f;
         break;
 }
```

If you do not use the break statement, the program flow in the switch statement continues into the next case. Code segments A and B
have the same behavior. 

```xpp
// Code segment A (break omitted)
case 13:
case 17:
case 21:
case 500:
    info("g");
    break;

// Code segment B (the values are comma-delimited)
case 13, 17, 21, 500;
    info("g");
    break;
```

## Ternary operator (?)

The ternary operator (**?**) is a conditional statement that is resolved to one of two expressions. The result can be assigned to a variable. By contrast, an **if** statement provides conditional branching of the program flow but can't be assigned to a variable. Here is the syntax for the ternary operator:

*expression1* **?** *expression2* **:** *expression3*

In this syntax, *expression1* must return a value of **true** or **false**. If *expression1* is **true**, the whole ternary statement returns *expression2*. Otherwise, the statement returns *expression3*. Both *expression2* and *expression3* must have the same type.

### Examples of the ternary operator (?)

The following code example returns one of two strings based on a Boolean return value from a method call. The Boolean expression indicates whether the CustTable table has a row with a RecId field value of 1. If this Boolean expression is true (meaning RecId != 0), found is assigned to result. Otherwise, the alternative not found is assigned to result.

```xpp
result = (custTable::find("1").RecId) ? "found" : "not found";
```

You can nest statements with the ternary operator. The following example assigns one of three values to **level** based on the value of **x**.

```xpp
int x = 1001;
str level = x <= 1000 ? "A" : (x <= 2000 ? "B" : "C");
info(level);
// Output is "B".
```


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
