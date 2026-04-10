---
title: X++ exception handling
description: Learn about exception handling in X++, which are regulated jumps away from sequence of program executions. These include throw statements andg global class methods.
author: pvillads
ms.author: pvillads
ms.topic: language-reference
ms.date: 03/31/2026
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
---

# X++ exception handling

[!include [banner](../includes/banner.md)]

This article describes exception handling in X++. Handle errors by using the **throw**, **try**...**catch**, **finally**, and **retry** statements to generate and handle exceptions.

An *exception* is a regulated jump away from the sequence of program execution. The `try...catch` blocks and the type of exception that is thrown determine the instruction where program execution resumes. An exception is represented by a value of the **Exception** enumeration, or an instance of .NET's `System.Exception` class or a class derived from it. One exception that you often throw is the **Exception::error** enum value. A common practice is to write diagnostic information to the Infolog before throwing the exception.

The **Global::error** method is often the best way to write diagnostic information to the Infolog. For example, your method might receive an input parameter value that isn't valid. In this case, the method can throw an exception to immediately transfer control to a **catch** code block that contains logic for handling this error situation. You don't necessarily have to know the location of the **catch** block that receives control when the exception is thrown.

## throw statements

Use the **throw** keyword to throw an **Exception** enum value. For example, the following statement throws an error exception.

```xpp
throw Exception::error;
```

Instead of throwing an enum value, use the output of the **Global::error** method as the operand for **throw**.

```xpp
throw Global::error('The parameter value is invalid.');
```

The **Global::error** method can automatically convert a label into the corresponding text. This functionality helps you write code that can be localized more easily.

```xpp
throw Global::error("@SYS98765");
```

You can call the static methods on the **Global** class without the **Global::** prefix. For example, you can call the **Global::error** method like this.

```xpp
error('My message.');
```

Use the **throw** keyword to throw .NET exceptions as well as the values of the enumerated Exception type.

```xpp
throw new System.InvalidOperationException("This function is not allowed");
```

Use the **throw** keyword by itself inside a catch block. In this case, **throw** behaves like the **rethrow** statement in C\#. The original exception, exception message, and its context such as call stack are rethrown and available to any catch statements in calling code.

```xpp
try
{
    throw Exception::error;
}
catch
{
    // locally handle exception
    // then rethrow for caller
    throw;
}
```

## try, catch, finally, and retry statements

When an exception occurs, the system first processes it through the **catch** list of the innermost **try** block. If the system finds a **catch** block that handles the kind of exception that occurred, program control jumps to that **catch** block. If the **catch** list has no block that specifies the exception, the system passes the exception to the **catch** list of the next-innermost **try** block. The system processes the **catch** statements in the same sequence as they appear in the code.

It's a common practice to have the first **catch** statement handle the **Exception::Error** enum value. One strategy is to have the last **catch** statement leave the exception type unspecified. In this case, the last **catch** statement handles all exceptions that aren't handled by any earlier **catch** statement. This strategy is appropriate for the outermost **try**...**catch** blocks.

You can include an optional *finally* clause in **try**...**catch** statements. The semantics of a **finally** clause are the same as they are in C\#. The system executes the statements in the **finally** clause when control leaves the **try** block, either normally or through an exception.

The **retry** statement can appear only in a **catch** block. The **retry** statement causes control to jump up to the first line of code in the associated **try** block. Use the **retry** statement when the cause of the exception can be fixed by the code in the **catch** block. The **retry** statement gives the code in the **try** block another opportunity to succeed. The **retry** statement erases all messages that have been written to the Infolog since program control entered the **try** block.

> [!NOTE]
> You must make sure that your **retry** statements don't cause an infinite loop. As a best practice, the **try** block should include a variable that you can test to find out whether you're in a loop.

```xpp
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
```

### The system exception handler

If no **catch** statement handles the exception, the system exception handler handles it. The system exception handler doesn't write to the Infolog. Therefore, unhandled exceptions can be hard to diagnose. Follow all these guidelines to provide effective exception handling:

+ Have a **try** block that contains all your statements in the outermost frame on the call stack.
+ Have an unqualified **catch** block at the end of your outermost **catch** list.
+ Avoid throwing an **Exception** enum value directly.
+ Throw the enum value that one of the following methods on the **Global** class returns: **Global::error**, **Global::warning**, or **Global::info**. (You can omit the implicit **Global::** prefix).
+ When you catch an exception that the Infolog doesn't show, call the **Global::info** function to show it.

**Exception::CLRError**, **Exception::UpdateConflictNotRecovered**, and system kernel exceptions are examples of exceptions that the Infolog doesn't automatically show.

### Exceptions and CLR interop

You can call Microsoft .NET Framework classes and methods that reside in assemblies that the common language runtime (CLR) manages. When your code throws a .NET Framework **System.Exception** instance, you can catch it by declaring a variable of type **System.Exception** to catch any .NET exception, or you can catch a specific .NET exception type by using one of its derived classes, as shown in the following example.

```xpp
System.ArgumentException ex;
try
{
    throw new System.ArgumentException("Invalid argument specified");
}
catch(ex) // Will catch the System.ArgumentException, given the type of ex.
{
    error(ex.Message);
}
```

You can catch .NET exceptions by referencing **Exception::CLRError**. Your code can get a reference to the **System.Exception** instance by calling the **CLRInterop::getLastException** method.

```xpp
try
{
    // call to .NET code which throws exception
}
catch(Exception::CLRError)
{
    System.Exception ex = CLRInterop::getLastException();
    error(ex.Message);
}
```

### Ensuring that exceptions are shown

The Infolog doesn't show exceptions of the **Exception::CLRError** type, because these exceptions aren't generated by a call to a method such as **Global::error**. In your **catch** block, your code can call **Global::error** to report the specific exception.

## Global class methods

This section describes some **Global** class methods in more detail. These class methods include **Global::error**, **Global::info**, and **Global::exceptionTextFallThrough**.

### Global::error method

The following code shows how the **error** method is declared.

```xpp
static Exception error
    (SysInfoLogStr txt,
    URL helpURL = '',
    SysInfoAction _sysInfoAction = null)
```

The return type is the **Exception::Error** enum value. The **error** method doesn't throw an exception. It just provides an enum value that you can use in a **throw** statement. The **throw** statement throws the exception. Here are descriptions of the parameters for the **error** method. Only the first parameter is required.

+ **SysInfoLogStr** txt is a **str** of the message text. It can also be a label reference, such as **strFmt("@SYS12345", strThingName)**.
+ The **URL** helpUrl is a reference to the location of a Help article in Application Explorer, such as **"KernDoc:\\\\\\\\Functions\\\\substr"**. The parameter value is ignored if \_sysInfoAction is supplied.
+ The **SysInfoAction** is an instance of a class that extends the **SysInfoAction** class. The method overrides that we recommend for the child class are the **description** method, the **run** method, the **pack** method, and the **unpack** method.

### Global::info method

Use the **Global::info** method to show text in the Infolog. In programs, write it as **info("My message.");**. Although the **info** method returns an **Exception::Info** enum value, you rarely want to throw **Exception::Info**, because nothing unexpected occurred.

### Global::exceptionTextFallThrough method

Occasionally, you want to do nothing inside your **catch** block. However, the X++ compiler generates a warning if you have an empty **catch** block. To avoid this warning, call the **Global::exceptionTextFallThrough** method in the **catch** block. The method does nothing, but it satisfies the compiler and explicitly states the intention.

## Exceptions inside transactions

If an exception is thrown inside a transaction, the transaction is automatically canceled (that is, a **ttsAbort** operation occurs). This behavior applies for both exceptions that are thrown manually and exceptions that the system throws. When an exception is thrown inside a **ttsBegin**-**ttsCommit** transaction block, no **catch** statement inside that transaction block can process the exception, (unless it is a **UpdateConflict** or a **DuplicateKeyException**). Instead, the innermost **catch** statements that are outside the transaction block are the first **catch** statements that are tested.

To catch **UpdateConflict** or **DuplicateKeyException** inside a transaction, explicitly specify the exception in the catch statement like this, `catch (Exception::DuplicateKeyException)`. A general **catch-all** statement `catch{}` can't catch **UpdateConflict** or **DuplicateKeyException** inside a transaction.

The finally clause is executed even in transaction scope.

## Exceptions and `using` statements

Exception scope doesn't impact the semantics of `using` statements. The `using` statement:

```xpp
using (var athing = new SomethingDisposable())
{
    // Do work.
}
```

Is semantically identical to:

```xpp
var athing = new SomethingDisposable();
try
{
    // Do work.
}
finally
{
    if (athing != null)
        athing.Dispose();
}
```

## Examples of exception handling

### Showing exceptions in the Infolog

The following code example shows exceptions in the Infolog.

```xpp
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
```

### Using the error method to write exception information to the Infolog

The following code example uses the **error** method to write exception information to the Infolog.

```xpp
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
```

### Handling a CLRError

The following code example handles a **CLRError** exception.

```xpp
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
```

### Using a retry statement

The following code example uses a **retry** statement.

```xpp
// This example shows how to use the retry statement. The print
// statements are included because retry causes earlier Infolog
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
```

### Throwing an exception inside a transaction

The following code example throws an exception in a transaction block.

```xpp
// This examples uses three levels of try nesting to illustrate
// where an exception is caught when the exception is thrown inside
// a ttsBegin ... ttsCommit transaction block.
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
```

### Using Global::error with a SysInfoAction parameter

When your code throws an exception, it can write messages to the Infolog. You can make those Infolog messages more helpful by using the **SysInfoAction** class.

In the following example, you pass a **SysInfoAction** parameter to the **Global::error** method. The **error** method writes the message to the Infolog. When the user double-clicks the Infolog message, the **SysInfoAction.run** method runs.

In the **run** method, you can write code that helps diagnose or fix the issue that caused the exception. The object that you pass to the **Global::error** method is constructed from a class that you write that extends **SysInfoAction**.

The following code sample is shown in two parts.

+ The first part shows a job that calls the **Global::error** method and then throws the returned value. You pass an instance of the **SysInfoAction\_PrintWindow\_Demo** class to the **error** method.
+ The second part shows the **SysInfoAction\_PrintWindow\_Demo** class.

#### Part 1: Calling Global::error

```xpp
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
```

#### Part 2: The SysInfoAction\_PrintWindow\_Demo class

```xpp
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
```

## List of exceptions

The following table shows the exception literals that are the values of the **Exception** enumeration.

| Exception literal                 | Description    |
|-----------------------------------|---------------------------------------------------|
| Break                             | The user pressed Break or Ctrl+C. |
| CLRError                          | An error occurred while the CLR functionality was being used. |
| CodeAccessSecurity                | An error occurred while the **CodeAccessPermission.demand** method was being used. |
| DDEerror                          | An error occurred while the **DDE** system class was being used. |
| Deadlock                          | A database deadlock occurred, because several transactions are waiting for each other. |
| DuplicateKeyException             | An error occurred in a transaction that is using Optimistic Concurrency Control. The transaction can be retried (use a **retry** statement in the **catch** block). |
| DuplicateKeyExceptionNotRecovered | An error occurred in a transaction that is using Optimistic Concurrency Control. The code won't be retried. This exception can't be caught inside a transaction.    |
| Error                             | A fatal error occurred. The transaction has been stopped. |
| Info                              | This exception literal holds a message for the user. Don't throw an **info** exception. |
| Internal                          | An internal error occurred in the development system. |
| Numeric                           | An error occurred while the **str2int**, **str2int64**, or **str2num** function was being used. |
| Sequence                          | |
| UpdateConflict                    | An error occurred in a transaction that is using Optimistic Concurrency Control. The transaction can be retried (use a **retry** statement in the **catch** block). |
| UpdateConflictNotRecovered        | An error occurred in a transaction that is using Optimistic Concurrency Control. The code won't be retried. This exception can't be caught within a transaction.    |
| Warning                           | An exceptional event has occurred. Although the user might have to take action, the event isn't fatal. Don't throw a **warning** exception. |
| [SQL connection error X++ exception](sql-connection-error.md) | An error occurred when during the query execution. The transaction will be canceled. This exception can't be caught within a transaction. |
| Timeout       | SQL query execution timed out. The exception can’t be caught within a transaction. The exception can be retried by using a retry statement in the catch block. |

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
