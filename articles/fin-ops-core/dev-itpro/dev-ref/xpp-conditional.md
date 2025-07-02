---
title: X++ conditional statements
description: Learn about conditional statements in X++, including outlines and examples of if, if..else, and switch statements.
author: pvillads
ms.author: pvillads
ms.topic: article
ms.date: 05/17/2025
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
---

# X++ conditional statements

[!include [banner](../includes/banner.md)]

This article describes the conditional statements in X++. The conditional statements are **if**, **if**...**else**, and **switch**. The ternary operator (**?:**) provides a value based on the provided expression. You use conditional statements to specify whether a statement is executed (with the **if** statement), or which is executed (with the **if**..**else**). Different conditional statements offer advantages in different situations.

## if and if...else statements

The **if** statement evaluates a conditional expression, and then executes a statement if the conditional expression is evaluated as **true**. You can use the **else** clause to provide an alternative statement that's executed if the condition is evaluated as **false**. The syntax for an **if**...**else** statement is:

**if (** *expression* **)** 
    *statement* 
**\[else** 
    *statement* 
**\]**

In this syntax, both occurrences of *statement* can be **compound statements** (zero or more statements enclosed in braces). The *expression* in the parentheses (that is, the conditional expression) can be any valid expression that is interpreted as **true** or **false**. Values of all types can be interpreted as boolean values: All numbers except 0 (zero) are **true** and all nonempty strings are **true**. You can nest **if** statements. However, if the nesting of **if** statements becomes too deep, you may consider using a **switch** statement instead to enhance legibility.

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

The **switch** statement is a multibranch language construct that has the same behavior as nested **if** statements. The expression after the **switch** keyword is evaluated and checked against each case value. The case values must be constants so they can be evaluated at compile-time. 

- If a case constant matches the **switch** expression, the **case** statement is executed. 
- If the case contains a **break** statement, the program then jumps out of the switch. 
- If the case doesn't contain a **break** statement, the program continues and executes the next **case** statements. 
- If no matches are found, the **default** statement is executed. 
- If there are no matches and no **default** statement, none of the statements inside the **switch** statement are executed. 

Here is the syntax for a **switch** statement:

**switch** **(** *expression* **)** **{** **{ case }** **\[default:** *statement* **\]** **}**

The syntax for a **case** block is:

**case** *expression* **{ ,** *expression* **} :**
    *statement*

In general, you should avoid situations where you don't use the **break** statement to exit each case, since it's easy to misread such code.

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

If you don't use the break statement, the program flow in the switch statement continues into the next case. Code segments A and B have the same behavior. 

This flow isn't recommended.

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

The ternary operator (**?:**) is a conditional expression that is resolved to one of two values. Here's the syntax for the ternary operator:

*expression1* **?** *expression2* **:** *expression3*

In this syntax, *expression1* is interpreted as a boolean value of **true** or **false**. If *expression1* is **true**, the whole ternary statement returns *expression2*. Otherwise, the statement returns *expression3*. Both *expression2* and *expression3* must have the same type.

### Examples of the ternary operator (?:)

The following code example returns one of two strings based on a Boolean return value from a method call. The Boolean expression indicates whether the CustTable table has a row with a RecId field value of 1. If this Boolean expression is true (meaning RecId != 0), found is assigned to result. Otherwise, the alternative not found is assigned to result.

```xpp
result = (custTable::find("1").RecId) ? "found" : "not found";
```

You can nest expressions with the ternary operator. The following example assigns one of three values to **level** based on the value of **x**.

```xpp
int x = 1001;
str level = x <= 1000 ? "A" : (x <= 2000 ? "B" : "C");
info(level);
// Output is "B".
```


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
