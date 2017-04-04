---
# required metadata

title: Programming language support
description: This topic reviews the changes made to the compiler for Microsoft Dynamics 365 for Operations.
author: pvillads
manager: AnnBe
ms.date: 04/04/2017
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
ms.custom: 26781
ms.assetid: 056d4064-e365-487c-a606-e2fadfe28242
ms.search.region: Global
# ms.search.industry: 
ms.author: pvillads
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Programming language support

This topic reviews the changes made to the compiler for Microsoft Dynamics 365 for Operations.

For Microsoft Dynamics 365 for Operations, the X++ compiler has been rewritten. No backward-incompatible changes have been introduced to X++ except where required by structural changes to the product. A few language enhancements have been added. A new X++ best practice tool has also been implemented, which allows the addition of user-defined custom rules.

## No more pcode, everything is in .NET Framework CIL
Through Microsoft Dynamics AX 2012, X++ source code was compiled into p-code, which was understood by the interpreter at run time. Optionally, you could then compile the p-code into Microsoft .NET CIL (Common Intermediate Language). CIL is what the .NET compilers for C\# and Visual Basic generate. However, X++ CIL code was usable only in limited cases, mainly for code executed in services and batch jobs. The new X++ compiler generates CIL only. There is no more p-code. The following tools that worked with p-code are now obsolete and have been removed from Dynamics AX and replaced by .NET tools:

-   The X++ compiler that generated p-code.
-   The special compiler that input p-code and generated .NET CIL.
-   The run time interpreter of p-code including its deterministic garbage collector.
-   The Dynamics AX Debugger.
-   The Dynamics AX Code Profiler, which helped find performance bottlenecks.
-   The AX .NET Business Connector for external applications that interoperated with Dynamics AX.

There are important benefits to X++ code running exclusively as .NET CIL, including:

-   CIL runs much faster in most scenarios. In cases where there are many method calls, and a lot of algorithmic content (as opposed to database access), you can expect significant performance improvements.
    -   It's easier to write application logic in other managed languages.
    -   There's no longer any need for the AX .NET Business Connector or managed proxies, because the assemblies can be consumed directly.
    -   The preferred way of consuming business logic externally is by using services.
-   CIL can efficiently reference classes that are available in other .NET assembly DLL files, without the run time reflection-based overhead that burdened the p-code interpreter.
-   CIL can be operated on by the many .NET tools.

## Unit of compilation
Previous versions of Microsoft Dynamics AX could compile X++ at the level of an individual method. Thus if a compilation of a class found an error in one method of the class, the methods that did compile correctly were still runnable. In the standard compilation unit now is the same as for other .NET languages such as C\#. If any method in a model element (class, form, query etc.) fails to compile, the whole compilation fails.

## Enhancements to X++
X++ is now a first-class citizen in the .NET world. Therefore we are adding to X++ several constructs that are available in C\# and other mainstream .NET languages. The changes are generally non-intrusive. In fact, very few changes have been made to the syntax and semantics of existing X++ code. Most of these additions are in the following list:

-   The `finally` keyword is now available to follow the `try` and `catch` keywords. The semantics are identical to the semantics in C\#. The statements provided in the finally clause are executed irrespective of whether the try block threw any exceptions.
-   The `using` keyword has been added as shorthand for referencing .NET namespaces. The following code example illustrates two ways of utilizing the using keyword to reference namespaces:

        using SysColl = System.Collections;  // SysColl is an alias for the whole namespace.
        using           System.CodeDom;      // Contains the class named CodeComment.

        public class MyClass2
        {
            static SysColl.ArrayList arrayList = new SysColl.ArrayList(); // Initialized on declaration.
            CodeComment codeComment          = new CodeComment("I am a comment.");

            // More X++ code here.
        }

-   You can now initialize a class's field in the field's declaration statement. This is illustrated twice in the previous code example.
-   You can declare variables in smaller scopes, not just at the start of methods.
-   The `var` keyword is available as a shortcut that allows the compiler to infer the type of the declared variable.
-   A class's fields can now be static. In previous versions, only instance fields were allowed.
-   A class can now have one static constructor. In previous versions, only instance constructors were available. The following X++ code example shows the syntax for a static constructor, through the new keyword typenew.

        .    public class MyClass4
            {
                static utcdatetime utcInitialized3;  // Static variable member.
                static void typenew()                // Static constructor member. 'typenew' is a new keyword.
                {
                utcInitialized3 = DateTimeUtil::utcNow(); // Static variable referenced without class name.
                }
            }

-   An attribute decoration, such as on a class or a method, can now omit the suffix of the attribute name if the suffix is `Attribute`. So the X++ joins the C\# in allowing `[MyFavorite]` instead of requiring `[MyFavoriteAttribute]`.
-   A delegate can now be defined in a table, form, or query, and not just in a class.
-   Attributes are now applied to the handlers of delegates and methods, to map the handlers to those targets.
-   Classes can now be nested in X++ source code. Nested classes are available only inside forms (such as a class that extends FormRun) to represent controls, data sources, or data fields.

## Backwardincompatible changes to X++
There are a few changes to X++ that require corresponding changes in legacy custom X++ source code. Most of these changes are in the following list:

-   The following keywords are no longer part of the X++ language, and their use causes compilation errors:
    -   `changeSite`
    -   `pause`
    -   `window`
-   In legacy X++, it was possible to designate a method to run either on the client or the server. This is no longer possible. All compiled X++ code is executed as .NET CIL on the server. There is no longer any X++ code that is evaluated at the client site or in the browser, therefore, the two keywords, *client* and *server*, are now ignored. Their use doesn't cause a compile error, but they should not be used in any new X++ code.
-   In Microsoft Dynamics AX 2012, there were a few areas where X++ behaved differently when compiled to p-code versus CIL. In Dynamics 365 for Operations, all these areas behave as they did in CIL in Microsoft Dynamics AX 2012. The significant behavioral differences between X++ p-code versus X+ as CIL were as follows:
    -   In CIL, the `real `data type is represented as `System.Decimal`. This means the range and precision for each `real` is different than it was under p-code. This change was already in effect in Microsoft Dynamics AX 2012 when .NET CIL was run.
    -   An assignment of one entire array to another was performed in value in p-code mode, but it's performed by reference in CIL mode.
    -   CIL helper methods such as `Global::runClassMethodIL` have been removed, since they're no longer relevant.
-   There is no concept of a job, in the sense of **AOT** &gt; **Jobs** &gt; **MyJob**. To quickly and easily run an X++ method, you can still add in a `static Main` method to a class, and then set the class as the startup object form for the project in Microsoft Visual Studio. When the project is run, the `Main` method will be run.


See also
--------

[Dynamics AX LINQ Provider for use in C#](linq-provider-c.md)

[Technical Concepts Guide](developer-home-page.md)

