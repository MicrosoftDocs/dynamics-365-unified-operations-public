---
title: Comments, using, and print statements
description: Learn about comments, using, and print statements in X++, including examples and descriptions for each statement type.
author: josaw1
ms.author: josaw
ms.topic: article
ms.date: 08/27/2021
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
ms.devlang: xpp
---

# Comments, using, and print statements

[!include [banner](../includes/banner.md)]

This article describes statements in X++.

## Comments

It's a good practice to add comments to your code. Comments make a program easier to read and understand. Comments are ignored when the program is compiled. Your comments can use either the **//** style or the **/\*** style. However, a best practice is to use the **//** style for comments, and even for multiline comments.

```xpp
// This is an example of a comment.
/* Here is another example of a comment. */
```

## print statements

You use the **print** statement to output text through **System.Diagnostics.WriteLine** to the Visual Studio **Output** window. During testing, the **print** statement is an alternative to the **Global::info** method, which shows text in the **Infolog** window. The following table compares the **print** statement and the **info** method.

| Feature   | print statement    | info method  |
|-----------|--------------------|--------------|
| Ease of invocation                        | The **print** statement automatically converts various data types into strings. It can convert multiple data types in one invocation.       | The **info** method requires that the input parameter be a string.     |
| Ability to copy contents to the clipboard | Text is easily copied from the **Output** window to the clipboard.            | Text is easily copied from the **Infolog** window to the clipboard. |
| Typical usage                             | The **print** statement is used for convenience during testing. It can help you debug small issues without having to run a formal debugger. | The **info** method is appropriate for use in production.     |

### Example of a print statement

The following code example demonstrates the print statement automatically converting any date type to a string. You do not need to prefix **info** with **Global::** when you call it.

```xpp
str hello = "Hello";
int fortytwo = 42;
utcDateTime now = DateTimeUtil::utcNow();
Dialog dialog = new Dialog();

print "The print statement automatically converts data types to strings.";
print hello, " -- ", fortytwo, " -- ", now, " -- ", dialog;
// Output to the Print window:
// The print statement automatically converts data types to strings.
// Hello -- 42 -- 10/3/2011 09:18:10 pm -- 1

// int2Str converter is needed when using info().
info("Hello");
info(int2Str(fortytwo));

// Output to Infolog window:
// Hello
// 42
```

## TODO comments

The compiler recognizes the string **TODO** when it occurs at the start of a comment. The **TODO** string prompts the compiler to report the rest of the comment text in the **Task List** window in Microsoft Visual Studio. To open the **Task List** window, select **View**, and then select **Task Window**. The **Task Window** reports the line number where the **TODO** comment can be found in the code.

Here are the rules for using **TODO** in comments:

- The **TODO** string can appear in a comment that uses either the **//** style or the **/\*** style.
- The **TODO** string must be the very first non–white space string in the comment. A carriage return, a line feed, a tab, and a space are all considered white space.
- No white space is required between the start of the comment and the **TODO**.
- The **TODO** string is case-insensitive. However, the convention is to type **TODO** in all uppercase letters, instead of **ToDo** or another variation.
- The **TODO** string can have any characters appended to it. However, the convention is either to append a colon to the **TODO** string or to follow it with a white space.
- The rest of the comment after the **TODO** string is reported as the task description. If the comment is longer than 200 characters, it might appear truncated on the **Tasks** tab.
- The **TODO** task description can be spread over multiple lines when the **/\*** comment style is used.

### Examples of TODO comments

The following examples show **TODO** comments.

```xpp
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
```

## Unsupported statements: pause and window

The **pause** and **window** keywords are no longer a part of the X++ language. These keywords will cause compilation errors if you use them.

## Ignored statements: server and client

In previous versions (AX2012 and earlier), you could designate a method to run on either the client or the server. This is no longer possible, because all X++ code is executed as .NET CIL on the server. The keywords `client` and `server` are ignored. Their use doesn't cause a compile error, but they should not be used in any new X++ code.

## using clauses

You use **using** clauses so that you don't have to provide the fully qualified name of a type. The **using** clause must precede the class that it applies, and it's required in every source file that you want it to apply to. Typically, all **using** clauses are put at the beginning of the source file. You can also provide aliases that introduce a short name for a fully qualified name. Aliases can denote namespaces or classes.

The following example shows a **using** clause, a namespace alias, and a class alias.

```xpp
using System;
using IONS=System.IO; // Namespace alias
using Alist=System.Collections.ArrayList; // Class alias

class UsingClass
{
    public static void test()
    {
        Int32 I;                  // Alternative to System.Int32
        Alist al = new Alist();   // Using a class alias
        al.Add(1);
        str s = IONS.Path::ChangeExtension(@"c:\tmp\test.xml", ".txt"); // Using a namespace alias
    }
}
```

## using statements

The **using** statement helps guarantee that objects that implement **IDisposable** are disposed of correctly. When you use an **IDisposable** object, you should declare and instantiate it in a **using** statement. The **using** statement calls the **Dispose** method on the object in the correct way, even if an exception occurs while you're calling methods on the object. You can achieve the same result by putting the object inside a **try** block and then explicitly calling **Dispose** in a **finally** block. The **using** statement simplifies the syntax and disposes of the object correctly. Here is the syntax for a **using** statement:

**using (** *expression* **) {** *statement* **}**

In this syntax, *statement* can be a block of statements, and *expression* declares and instantiates an object that implements **IDisposable**. The following example creates and uses a **StreamReader** object.

```xpp
static void AnotherMethod()
{
    str textFromFile;
    using (System.IO.StreamReader sr = new System.IO.StreamReader("c:\\test.txt"))
    {
        textFromFile = sr.ReadToEnd();
    }
}
```

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
