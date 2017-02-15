---
# required metadata

title: X++ statements, loops, and exception handling
description: This topic describes statements, loops, and exception handling in X++.
author: annbe
manager: AnnBe
ms.date: 2016-08-27 00 - 35 - 31
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
# ms.reviewer: 61
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 150213
ms.assetid: 3383a311-fcab-4b83-9f17-dfb7e74d5695
ms.search.region: Global
# ms.search.industry: 
ms.author: annbe
ms.dyn365.intro: Feb-16
ms.dyn365.version: AX 7.0.0

---

# X++ statements, loops, and exception handling

This topic describes statements, loops, and exception handling in X++.

Comments
--------

It is good practice to add comments to your code. This makes a program easier to read and understand. Comments are ignored when the program is compiled. You can use "//" and "/\* … \*/" style comments, although it is best practice to use "//"-style comments, even for multi-line comments.

    // This is an example of a comment.
    /* Here is another example of a comment. */

## Print statements
You use the **print** statement to display text or selected results in a temporary window. The messages are displayed in a window that appears when the first **print** statement is executed. The **print** statement can be a convenient alternative to the **Global::info** method during testing. The **info** method displays text in the **Infolog** window. The following table compares the **print** statement against the **Global::info** method.

| Feature            | **Print** statement                                                                                                                            | **Info** method                                                    |
|--------------------|------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------|
| Ease of invocation | The **Print** statement automatically converts various data types to strings. It can convert multiple data types in one invocation.            | The **Info** method requires that the input parameter be a string. |
| Copy to clipboard  | The **Print** window contents cannot be copied to the clipboard. You cannot give the **Print** window focus.                                   | **Infolog** contents are easily copied to the clipboard.           |
| Scope of lifetime  | The **Print** window closes when the X++ application ends, and the window might close before you have time to read it.                         | The **Infolog** window persists for the whole client session.      |
| Size and location  | The **Print** window can be a specific size, and in a specific location on the screen.                                                         | The **Infolog** window is sized and placed by the system.          |
| Common usage       | The **Print** statement is used for convenience during testing. It can help you debug small problems without needing to run a formal debugger. | The **Info** method is appropriate for use in production.          |

### Print statement code example

    // This example demonstrates the print statement automatically converting any
    // date type to a string. 
    static void PrintJob2(Args _args)
    {
        str s1 = "Hello";
        int n2 = 42;
        utcDateTime udt3 = DateTimeUtil::utcNow();
        Dialog dlog4 = new Dialog();
        print "The print statement automatically converts data types to strings.";
        print s1, " -- ", n2, " -- ", udt3, " -- ", dlog4;
        Global::info("User clicked 'Yes' to continue to this call to info.");
        info(int2Str(n2)); // int2Str converter is needed.
    }
     
    /***  Output to the Print window:
    The print statement automatically converts data types to strings.
    Hello -- 42 -- 10/3/2011 09:18:10 pm -- 1
    ***/

    /***  Output to Infolog window:
    Message (02:18:10 pm)
    User clicked 'Yes' to continue to this call to info.
    ***/

## TODO comments
The compiler recognizes the string **TODO** when it occurs at the start of a comment. The **TODO** string prompts the compiler to report the rest of the comment text on in the **Task List** window of Visual Studio. To open the **Task List** window, select **View** and then select **Task Window**. The **Task Window **reports the line number in the code where the **TODO** comment can be found. The rules for using **TODO** in comments are as follows:

-   The **TODO** string can appear in either the **//** or the **/\* \*/** style of comment.
-   The **TODO** string must be the very first non-white space string in the comment. White space is considered to be a carriage return, a line feed, a tab, or a space.
-   No white space is required between the start of the comment and the **TODO**.
-   The **TODO** string is case insensitive. However, the convention is to write **TODO** in all uppercase letters, instead of **ToDo** or another variation.
-   The **TODO** string can have any characters appended to it, but the convention is to either append a colon, or for a white space to follow.
-   The rest of the comment after the **TODO** string is reported as the task description. If the comment is longer than 200 characters, it might display truncated in the **Tasks** tab.
-   The **TODO** task description can be spread over multiple lines when the **/\* \*/** comment style is used.

### TODO code examples

The following table shows examples of using **TODO** in the **//** or the **/\* \*/** style of comment.

    // An example of using TODO in the // style of comment.
    public boolean isLate()
    {
        // TODO: Finish this stub. 
        return true;
    }

    // An example of using TODO in the /* */ style of comment.
    public boolean isLate()
    {
        /* TODO Finish this stub */
        return true;
    }

## Using clauses
You use **using** clauses so that you do not have to provide the fully-qualified name of a type. The **using** clause must precede the class which it applies, and it is required in every source file you want it to apply to. Typically, all **using** clauses are placed at the beginning of the source file. It's also possible to provide aliases that introduce a short name for a fully qualified name. Aliases can denote namespaces or classes. The following example shows a using clause, a namespace alias, and a class alias.

     
    using System;
    using IONS=System.IO; // Namespace alias
    using Alist=System.Collections.ArrayList; // Class alias

    public class MyClass2
    {
        public static void Main(Args a)
        {
            Int32 I; // Alternative to System.Int32
            Alist al; // Using a class alias

            al = new Alist();
            str s;

            al.Add(1);

            s = IONS.Path::ChangeExtension(@"c:\tmp\test.xml", ".txt");
        }
    }

## Conditional statements
The conditional statements are **if**, **if ... else**, **switch**, and the **ternary operator (?)**. You use conditional statements to specify whether a block of code is executed or not. Different conditional statements offer advantages depending on the details of the situation.

## if and if...else statements
The **if** statement evaluates a conditional expression and executes a statement or set of statements if the conditional expression evaluates to **true**. You can provide an alternative statement or set of statements that are executed if the condition is false by using the **else** clause. The syntax for an if... else statement is **if** **(** *expression* **)** *statement* **\[** **else** *statement* **\]** . Both statements can be compound statements. The expression in the parentheses (the conditional expression) can be any valid expression that evaluates to **true** or **false**. All numbers different from zero are **true;** all non-empty strings are also **true**. You can nest **if** statements, but if the nesting of **if** statements becomes too deep, consider using a **switch** statement instead.

### if and if... else code examples

    // if statement
    if(a > 4)
    {
       print a;
    }
     
    // if... else statement 
    if(a > 4)
    {
       print a;
    }
    else
    {
       print "a is less than or equal to 4";
    }

## switch statement
The **switch** statement is a multi-branch language construct. This is in contrast to the **if** statement where you have to nest **if** statements to create the same effect. The conditional expression of the **switch** is evaluated and checked against each case value. The case values must be constants that can be evaluated by the compiler. If a case constant matches the switch expression, the case statement is executed. If the case also contains a **break** statement, the program then jumps out of the switch. If there is no **break** statement, the program continues executing the next set of case statements. If no matches are found, the **default** statement is executed. If there are no matches and no default, none of the statements inside the **switch** are executed. The syntax for a switch statement is: Switch statement = **switch** **(**  *expression* **) { { case } \[ default:**  *statement*  **\] }** The syntax for a case is: case **= case**  *expression*  **{ ,**  *expression*  **} :**  *statement* Each of the previous s*tatement* lines can be replaced with a block of statements by enclosing the block in **{...}** braces.

### Switch statement code examples

    // When the break keyword is used within a switch statement, the execution of 
    // the case branch terminates, and the statement following the 
    // switch is executed as shown in the following example.
    // If the Debtor account number is 1000, the program executes 
    // "do something", and then continues execution after the switch statement.
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
     
    // Switch statement example to make the execution drop 
    // through case branches by omitting a break statement. 
    // If x is 10, b is assigned to a, and d is assigned to c, the break 
    // statement is omitted after the case 10: statement. If x is 11, d 
    // is assigned to c. If x is 12, f is assigned to e.
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
     
    // If you do not use the break statement, the program flow in the switch
    // statement continues into the next case. Code segments A and B
    // have the same behavior. 
    // Code segment A (break omitted)
    case 13:
    case 17:
    case 21:
    case 500:
        print "g";
        break;
    // Code segment B (the values are comma-delimited)
    case 13, 17, 21, 500;
        print "g";
        break;

    // Break statement example within a while loop. When used within
    // a loop, the loop is terminated and execution continues
    // from the statement following the loop. This works for do... while
    // and for loops as well. 
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

## Ternary operator (?)
The **ternary operator** (**?**) is a conditional statement that resolves to one of two expressions. The result can be assigned to a variable. In comparison, an **if** statement provides conditional branching of program flow but cannot be assigned to a variable. The syntax for the ternary operator is *expression1* **?** *expression2* **:** *expression3* *expression1* must return a value of **true** or **false.** If *expression1* is **true**, the whole ternary statement returns *expression2*; otherwise it returns *expression3*. *expression2* and *expression3* must have the same type.

### Ternary code examples

    // Returns one of two strings based on a Boolean return value from a method call. 
    // The Boolean expression indicated whether the CustTable table has a row
    // with a RecId field value of 1. If this Boolean expression is true 
    // (meaning RecId != 0), found is assigned to result. 
    // Otherwise, the alternative not found is assigned to result.
    result = (custTable::find("1").RecId) ? "found" : "not found";
     
    // An example of a nested ternary statement. 
    // If z is not greater than 1000, the expression is equal to the third 
    // expression and low is printed. If AccountNum is greater than 1000, the second 
    // expression is evaluated, and this also contains a ternary operator. If AccountNum 
    // is greater than 1000 and less than 2000, In interval is printed. If AccountNum is 
    // greater than 1000 and greater than or equal to 2000, Above 2000 is printed.str z = "5";

    print( (z > "1000") ?
             ( (z < "2000") ? "In interval" : "Above 2000")
             : "low");
    ); 

## Loop statements
There are three loop statements,  **for**, **while**, and **do...while.** A loop repeats its statement until the condition set for the loop is **false.** Within the loop statements, you can use **break** and **continue** statements.

## for loop
The **for** loop repeatedly executes one or more statements, as long as the conditional expression is **true**. The statement is executed as many times as the condition is met. The body of the **for** loop may be executed zero or more times according to the results of the condition test. A **for** loop differs from other loops because of the following additions because the initial value to a control variable can be assigned and because there is a statement for incrementing or decrementing the variable. These additions make it especially useful for traversing lists, containers, and arrays because they have a fixed number of elements. You can also apply a statement to each element and increment your way through the elements, setting the condition to test for the last element. The syntax for a **for** statement is: **for** ( initialization ; test ; increment ) { *statement* } *Statement* can be a block of statements.

### for loop code examples

    // An example where all items are printed in 
    // a fixed array called ra with 100 reals. 
    int ra[10];

    int i; // Control variable.
    for (i=1; i<=100; i+=1)
    {
        print ra[i];
    }

## while loop
A **while** loop repeatedly executes one or more statements, as long as the condition expression is **true**. The statements are executed from zero to many times, depending on how many times the condition is met. The syntax for a **while** loop is: **while** **(** *expression* **)** *statement* *Statement* can be replaced by a block of statements.

### while loop code example

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

## do...while loop
The **do...while** loop is similar to the while loop, but differs in that the condition follows the statements to be executed. The statements are always executed at least once, as the condition is tested after the statements are executed. The **do...while** loop is well-suited for tasks that always must be done at least once, such as getting parameters for a report. The syntax for a **do...while** loop is: **do {** *statement* **} while (** *expression* **) ;** *Statement* can be a block of statements.

### do...while loop code example

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
The **continue** statement causes execution to move directly to the next iteration of a **for**, **while,** or **do...while** loop. For **do** or **while**, the test is executed immediately. In a **for** statement, the increment step is executed. The **break** statement is used within a loop to terminate a loop. Execution moves directly to the first statement following the loop.

### continue statement code example

    // An example of a continue statement. 
    // If Iarray[i] <= 0, the remaining statements in the loop are not executed, 
    // and i is incremented before the if statement is tried again.
    int i;
    int Iarray[100];
    for (i=1; i<100; i++)
    {
        if (Iarray[i] <= 0)
        continue;
        // Some statements.
    }

## using statement
The **using** statement ensure that objects that implement **IDisposable** are disposed of correctly. When you use an **IDisposable** object, you should declare and instantiate it in a **using** statement. The **using** statement calls the **Dispose** method on the object in the correct way, even if an exception occurs while you are calling methods on the object. You could achieve the same result by putting the object inside a try block, and then explicitly calling **Dispose** in a finally block. The **using** statement simplifies the syntax and disposes of the object correctly. The syntax for a **using** statement is **using** ( *expression* ) { *statement* }. *Statement* can be a block of statements. Expression declares and instantiates an object that implements IDisposable. The following example creates and uses a **StreamReader** object.

    static void AnotherMethod()
    {
        str textFromFile;

        using (System.IO.StreamReader sr = new System.IO.StreamReader("c:\\test.txt"))
        {
            textFromFile = sr.ReadToEnd();
        }
    }

## Exception handling with throw, try...catch, finally, and retry
You handle errors by using the **throw,** **try...catch**, **finally** and **retry** statements to generate and handle exceptions. An **exception** is a regulated jump away from the sequence of program execution. The instruction at which program execution resumes is determined by **try**...**catch** blocks and the type of exception that is thrown. An exception is represented by a value of the **enum** named **Exception**. A frequently thrown exception is **Exception::error** enumeration value. It is common practice to write diagnostic information to the **Infolog** before throwing the exception, and the **Global::error** method is often the best way to do that. For example, your method might receive an input parameter value that is invalid. Your method can **throw** an exception to immediately transfer control to a **catch** code block that contains logic to handle this particular error situation. You do not necessarily need to know the location of the **catch** block that will receive control when the exception is thrown.

## throw statement
You use the **throw** keyword to throw an **Exception** enum value. For example, the following statement throws an error exception:

    throw Exception::error;

Instead of throwing an enum value, it is a best practice to use the **Global::error** method output as the operand for **throw**:

    throw Global::error("The parameter value is invalid.");

The **Global::error** method can automatically convert a label into the corresponding text. This helps you to write code that can be more easily localized.

    throw Global::error("@SYS98765");

The static methods on the **Global** class can be called without the **Global::** prefix. For example, the **Global::error** method can be called simply as

    error("My message.");

## try, catch, finally, and retry statements
When an exception is thrown, it is first processed through the **catch** list of the innermost **try** block. If a **catch** block is found that handles the kind of exception that is being thrown, program control jumps to that **catch** block. If the **catch** list has no block that specifies the particular exception, the system passes the exception to the catch list of the next innermost try block. The **catch** statements are processed in the same sequence that they appear in the code. It is common to have the first **catch** statement handle the **Exception::Error** enumeration value. One strategy is to have the last **catch** statement leave the exception type unspecified. This means it handles all exceptions that are not handled by a previous **catch.** This strategy is appropriate for the outermost **try...catch** blocks. **try...catch** statements can include an optional **finally** clause. The semantics are the same as they are in C\#. The statements in the finally clause are executed when control leaves the try block, either normally or through an exception. The **retry** statement can be written only in a **catch** block. The **retry** statement causes control to jump up to the first line of code in the associated **try** block. The **retry** statement is used when the cause of the exception can be fixed by the code in the **catch** block. The **retry** statement gives the code in the **try** block another chance to succeed. The **retry** statement erases messages that were written to the **Infolog** since program control entered the try block. **Note:** You must prevent your use of **retry** from causing an infinite loop. The best practice is to include a variable in the **try** block that you can test to see if you are in a loop.

    try 
    { 
        // Code here.
    }
    catch (Exception::Numeric) 
    { 
        info("Caught a Numeric exception."); 
    }
    catch 
    { 
        info("Caught an exception."); 
    }
    finally
    {
        // Executed no matter how the try block exits.
    }

### The system exception handler

If no **catch** statement handles the exception, it is handled by the **system exception handler**. The system exception handler does not write to the **Infolog**. This means that an unhandled exception can be hard to diagnose. We recommended that you do all the following to provide effective exception handling:

-   Have a **try** block that contains all your statements in the outermost frame on the call stack.
-   Have an unqualified **catch** block at the end of your outermost **catch** list.
-   Avoid throwing an **Exception** enum value directly.
-   **Throw** the enum value that is returned from one of the **Global::error** method, the **Global::warning** method, or the **Global::info** method on the **Global** class. You have the option of omitting the implicit **Global::** prefix).
-   When you **catch** an exception that has not been displayed in the **Infolog**, call the **Global::info** function to display it.

**Exception::CLRError**, **Exception::UpdateConflictNotRecovered**, and system kernel exceptions are examples of exceptions that are not automatically displayed in the **Infolog**.

### Exceptions and CLR interop

You can call .NET Framework classes and methods that reside in assemblies that are managed by the common language runtime (CLR). When a .NET Framework **System.Exception** instance is thrown, your code can **catch** it by referencing **Exception::CLRError**. Your code can obtain a reference to the **System.Exception** instance by calling the **CLRInterop::getLastException** method.

### Ensure exceptions are displayed

Exceptions of type **Exception::CLRError** are not displayed in the **Infolog**. These exceptions are not issued by a call to a method such as **Global::error**. In your catch block, your code can call **Global::error** to report the specific exception.

## Global class methods
This section describes some **Global** class methods in more detail. These class methods include the **Global::error** method, the **Global::info** method, and the **Global::exceptionTextFallThrough** method.

### Global::error method

The error method is declared as follows:

    server client static Exception error
        (SysInfoLogStr txt,
        URL helpURL = '',
        SysInfoAction _sysInfoAction = null)

The return type is the **Exception::Error** enum value. The **error** method does not throw an exception. It only provides an enum value that could be used in a **throw** statement. The **throw** statement throws the exception. Only the first parameter is required. The parameters are described in the following list:

-   The **SysInfoLogStr** txt is a **str** of the message text. This can also be a label reference, such as **strFmt("@SYS12345", strThingName)**.
-   The **URL** helpUrl is a reference to the location of a Help topic in the Application Explorer. For example:**"KernDoc:\\\\\\\\Functions\\\\substr"**This parameter value is ignored if \_sysInfoAction is supplied.
-   The **SysInfoAction** \_sysInfoAction is an instance of a class that extends the **SysInfoAction** class. The method overrides we recommend for the child class are the **description** method, the **run** method, the **pack** method, and the **unpack** method.

### Global::info method

The **Global::info** method is routinely used to display text in the **Infolog**. It is often written in programs as **info("My message.");**. Even though the **info** method returns an **Exception::Info** enumeration value it would be rare to want to throw an **Exception::Info** because nothing unexpected has occurred.

### Global::exceptionTextFallThrough method

Occasionally you want to do nothing inside your **catch** block. The X++ compiler issues a warning when you have an empty **catch** block. You should avoid this warning by calling the **Global::exceptionTextFallThrough** method in the **catch** block. The method does nothing, but it satisfies the compiler.

## Exceptions inside transactions
If an exception is thrown inside a transaction, the transaction is automatically aborted (a **ttsAbort** operation occurs). This applies both for exceptions thrown manually and for exceptions thrown by the system. When an exception is thrown inside a **ttsBegin** - **ttsCommit** transaction block, no **catch** statement inside that transaction block can process the exception. Instead, the innermost **catch** statements that are outside the transaction block are the first **catch** statements to be tested.

## Exceptionhandling code examples
### Display exceptions in the Infolog

This code example displays exceptions in the Infolog.

    // This example shows that a direct throw of Exception::Error does not
    // display a message in the Infolog. This is why we recommend the 
    // Global::error method. 
    static void TryCatchThrowError1Job(Args _args)
    {
    /***
      The 'throw' does not directly add a message to the Infolog.
      The exception is caught.
    ***/
        
        try
        {
            info("In the 'try' block. (j1)");
            throw Exception::Error;
        }
        catch (Exception::Error)
        {
            info("Caught 'Exception::Error'.");
        }
    /**********  Actual Infolog output
    Message (03:43:45 pm)
    In the 'try' block. (j1)
    Caught 'Exception::Error'.
    **********/
    }

### error method to write exception information to the Infolog

This code example uses the **error** method to write exception information to the Infolog.

    // This example shows that the use of the Global::error method 
    // is a reliable way to display exceptions in the Infolog. 
    static void TryCatchGlobalError2Job(Args _args)
    {
        /***
        The 'Global::error()' does directly add a message to the Infolog.
        The exception is caught.
        ***/
        try
        {
            info("In the 'try' block. (j2)");
            throw Global::error("Written to the Infolog.");
        }
        catch (Exception::Error)
        {
            info("Caught 'Exception::Error'.");
        }
    /***  Infolog output
    Message (03:51:44 pm)
    In the 'try' block. (j2)
    Written to the Infolog.
    Caught 'Exception::Error'.
    ***/
    }

### Handle a CLRError

This code example handles a **CLRError.**

    // This example shows that a CLRError exception is not displayed 
    // in the Infolog unless you catch the exception and manually
    // call the info method. The use of the CLRInterop::getLastException
    // method is also demonstrated. 
    static void TryCatchCauseCLRError3Job(Args _args)
    {
        /***
        The 'netString.Substring(-2)' causes a CLRError,
        but it does not directly add a message to the Infolog.
        The exception is caught.
        ***/
        System.String netString = "Net string.";
        System.Exception netExcepn;
        try
        {
            info("In the 'try' block. (j3)");
            netString.Substring(-2); // Causes CLR Exception.
        }
        catch (Exception::Error)
        {
            info("Caught 'Exception::Error'.");
        }
        catch (Exception::CLRError)
        {
            info("Caught 'Exception::CLRError'.");
            netExcepn = CLRInterop::getLastException();
            info(netExcepn.ToString());
        }
    /**********  Actual Infolog output (truncated for display)
    Message (03:55:10 pm)
    In the 'try' block. (j3)
    Caught 'Exception::CLRError'.
    System.Reflection.TargetInvocationException: Exception has been thrown by the target of an invocation. ---> 
        System.ArgumentOutOfRangeException: StartIndex cannot be less than zero.
    Parameter name: startIndex
       at System.String.InternalSubStringWithChecks(Int32 startIndex, Int32 length, Boolean fAlwaysCopy)
       at System.String.Substring(Int32 startIndex)
       at ClrBridgeImpl.InvokeClrInstanceMethod(ClrBridgeImpl* , ObjectWrapper* objectWrapper, Char* pszMethodName, 
       Int32 argsLength, ObjectWrapper** arguments, Boolean* argsAreByRef, Boolean* isException)
    **********/
    }

### Use the retry statement

This code example uses the **retry** statement.

    // This example shows how to use the retry statement. The print
    // statements are included becuase retry causes earlier Infolog 
    // messages to be erased. 
    static void TryCatchRetry4Job(Args _args)
    {
        /***
        Demonstration of 'retry'. The Infolog output is partially erased
        by 'retry', but the Print window is fully displayed.
        ***/
        Exception excepnEnum;
        int nCounter = 0;
        try
        {
            info("        .");
            print("        .");
            info("In the 'try' block, [" + int2str(nCounter) + "]. (j4)");
            print("In the 'try' block, [" + int2str(nCounter) + "]. (j4)");
            nCounter++;
            if (nCounter >= 3) // Prevent infinite loop.
            {
                info("---- Will now throw a warning, which is not caught.");
                print("---- Will now throw a warning, which is not caught.");
                throw Global::warning("This warning will not be caught. [" + int2str(nCounter) + "]");
            }
            else
            {
                info("Did not throw a warning this loop. [" + int2str(nCounter) + "]");
                print("Did not throw a warning this loop. [" + int2str(nCounter) + "]");
            }
            excepnEnum = Global::error("This error message is written to the Infolog.");
            throw excepnEnum;
        }
        catch (Exception::Error)
        {
            info("Caught 'Exception::Error'.");
            print("Caught 'Exception::Error'.");
            retry;
        }
        info("End of job.");
        print("End of job.");
    /**********  Actual Infolog output
    Message (04:33:56 pm)
            .
    In the 'try' block, [2]. (j4)
    ---- Will now throw a warning, which is not caught.
    This warning will not be caught. [3]
    **********/
    }

### Throw an exception inside a transaction

This code example throws an exception in a transaction block.

    // This examples uses three levels of try nesting to illustrate
    // where an exception is caught when the exception is thrown inside
    // a ttsBegin-ttsCommit transaction block. 
    static void TryCatchTransaction5Job(Args _args)
    {
        /***
        Shows an exception that is thrown inside a ttsBegin - ttsCommit
        transaction block cannot be caught inside that block.
        ***/
        try
        {
            try
            {
                ttsbegin;
                try
                {
                    throw error("Throwing exception inside transaction.");
                }
                catch (Exception::Error)
                {
                    info("Catch_1: Unexpected, caught in 'catch' inside the transaction block.");
                }
                ttscommit;
            }
            catch (Exception::Error)
            {
                info("Catch_2: Expected, caught in the innermost 'catch' that is outside of the transaction block.");
            }
        }
        catch (Exception::Error)
        {
            info("Catch_3: Unexpected, caught in 'catch' far outside the transaction block.");
        }
        info("End of job.");
    /**********  Actual Infolog output
    Message (04:12:34 pm)
    Throwing exception inside transaction.
    Catch_2: Expected, caught in the innermost 'catch' that is outside of the transaction block.
    End of job.
    **********/
    }

### Use Global::error with a SysInfoAction parameter

When your code throws an exception, your code can write messages to the **Infolog** window. You can make those **Infolog** messages more helpful by using the **SysInfoAction** class. In the following example, a **SysInfoAction** parameter is passed in to the **Global::error** method. The **error** method writes the message to the **Infolog**. When the user double-clicks the **Infolog** message, the **SysInfoAction.run** method is run. You can write code in the **run** method that helps to diagnose or fix the problem that caused the exception. The object that is passed in to the **Global::error** method is constructed from a class that you write that extends **SysInfoAction**. The following code sample is shown in two parts. The first part shows a job that calls the **Global::error** method, and then throws the returned value. An instance of the **SysInfoAction\_PrintWindow\_Demo** class is passed into the **error** method. The second part shows the **SysInfoAction\_PrintWindow\_Demo** class.

#### Part 1: Call Global::error

    static void Job_SysInfoAction(Args _args)
    {
        try
        {
            throw Global::error
                ("Click me to make the Print window display."
                ,""
                ,new SysInfoAction_PrintWindow_Demo()
                );
        }
        catch
        {
            warning("Issuing a warning from the catch block.");
        }
    }

#### Part 2: The SysInfoAction\_PrintWindow\_Demo class

    public class SysInfoAction_PrintWindow_Demo extends SysInfoAction
    {
        str m_sGreeting; // In classDeclaration.
        public str description()
        {
            return "Starts the Print Window for demonstration.";
        }

        public void run()
        {
            print("This appears in the Print window.");
            print(m_sGreeting);
        
            /*********** Actual Infolog output
            Message (03:19:28 pm)
            Click me to make the Print window display.
            Issuing a warning from the catch block.
            ***************/
        }

        public container pack()
        {
            return ["Packed greeting."]; // Literal container.
        }

        public boolean unpack(container packedClass, Object object = null)
        {
            [m_sGreeting] = packedClass;
            return true;
        }
    }

## List of exceptions
The exception literals shown in the following table are the values of the **Exception** enumeration.

| Exception literal                     | Description                                                                                                                                                                             |
|---------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Break**                             | Indicates that the user has pressed BREAK or CTRL+C.                                                                                                                                    |
| **CLRError**                          | Indicates that an error has occurred during the use of the common language runtime (CLR) functionality.                                                                                 |
| **CodeAccessSecurity**                | Indicates that an error has occurred during the use of the **CodeAccessPermission.demand** method.                                                                                      |
| **DDEerror**                          | Indicates that an error occurred in the use of the **DDE** system class.                                                                                                                |
| **Deadlock**                          | Indicates that there is a database deadlock because several transactions are waiting for each other.                                                                                    |
| **DuplicateKeyException**             | Indicates that an error has occurred in a transaction that is using Optimistic Concurrency Control. The transaction can be retried (use a **retry** statement in the **catch** block).  |
| **DuplicateKeyExceptionNotRecovered** | Indicates that an error has occurred in a transaction that is using Optimistic Concurrency Control. The code will not be retried. This exception cannot be caught inside a transaction. |
| **Error**                             | Indicates that a fatal error has occurred. The transaction has been stopped.                                                                                                            |
| **Info**                              | Holds a message for the user.Do not **throw** an **info** exception.                                                                                                                    |
| **Internal**                          | Indicates an internal error in the development system.                                                                                                                                  |
| **Numeric**                           | Indicates that an error has occurred during the use of the **str2int**, **str2int64**, or **str2num** functions.                                                                        |
| **Sequence**                          |                                                                                                                                                                                         |
| **UpdateConflict**                    | Indicates that an error has occurred in a transaction that is using Optimistic Concurrency Control. The transaction can be retried (use a **retry** statement in the **catch** block).  |
| **UpdateConflictNotRecovered**        | Indicates that an error has occurred in a transaction that is using Optimistic Concurrency Control. The code will not be retried. This exception cannot be caught within a transaction. |
| **Warning**                           | Indicates that something exceptional has happened. The user might have to take action, but the event is not fatal. Do not throw a **warning** exception.                                |

## changeSite, pause, and window statements
The **changeSite**, **pause**, and **window** keywords are no longer a part of the X++ language. Using these keywords will cause compilation errors.

