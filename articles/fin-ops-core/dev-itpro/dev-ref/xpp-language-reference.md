---
title: X++ language reference
description: This article provides programming guidance for X++.
author: josaw1
ms.date: 08/27/2021
audience: Developer
ms.reviewer: josaw
ms.search.region: Global
ms.author: josaw
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
ms.collection: get-started
---

# X++ language reference

[!include [banner](../includes/banner.md)]

X++ is an object-oriented, application-aware, and data-aware programming language used in enterprise resource planning (ERP) programming and in database applications. It provides system classes for a broad range of system programming areas, highlighted in the following table.

| X++ language feature | Description |
|-----|-----|
| Classes              | In addition to system classes, there are also application classes for managing many types of business processes. Reflection on classes is supported. |
| Tables               | X++ programmers can access the relational tables. X++ includes keywords that match most of the keywords in standard SQL. Reflection on tables is supported. |
| User interface       | Manipulation of user interface items, such as forms and reports.|
| Best practice checks | X++ code is checked for syntax errors during compile time. The compile process also performs best practice checks. Violations of best practices can generate compiler messages.|
| Garbage collection   | The X++ runtime execution engines have automatic mechanisms to discard objects that are no longer referenced, so that memory space can be reused. |
| Interoperability     | Interoperability between classes written in X++ and in C\# (or other .NET Framework languages) is supported.                                      |
| File manipulation    | File input and output are supported, including XML building and parsing. |
| Collections          | Dynamic arrays are supported and the X++ includes several collection objects.|

## X++ compiles to Microsoft .NET CIL (Common Intermediate Language)

X++ source code is compiled to Microsoft .NET CIL (Common Intermediate Language). CIL is what the .NET compilers for C\# and Visual Basic generate. The advantages of compiling to CIL include:

+ Your code runs much faster than in previous versions (AX2012 and earlier).
+ It's easier to write application logic in other managed languages and integrated that logic into your X++ app.
+ Your X++ apps can efficiently reference classes that are available in other .NET assembly DLL files.
+ The CIL can be operated on by the many .NET tools.

The standard compilation unit is the same as for other .NET language. If any method in a model element (for example, a class, form, or query) fails to compile, the whole compilation fails.

If you are upgrading code from previous versions (AX2012 and earlier), note that the CIL helper methods such as `Global::runClassMethodIL` have been removed, because they're no longer relevant.

For more information, see [What is "managed code"?](/dotnet/standard/managed-code).

### The Ignore list

Assemblies are generated from successful compilations and the runtime system can't load incomplete assemblies. There are scenarios when porting legacy applications where it's beneficial to get things running in a staged fashion and where parts of the application need to be tested before everything is ported. While this is useful for this very limited scenario, it shouldn't be used once the application is ready for production, since you would be hiding problems that will occur at runtime, after the system has been deployed. To ignore parts of your X++ code, you can specify a method in an XML by selecting, "Edit Best Practice Suppressions," from the context menu on the project. This will open an XML document where the exclusions are maintained.

## Concepts

The X++ language programming reference is divided into these sections:

+ [Variables and data types](xpp-variables-data-types.md)
+ [Statements, loops, and exception handling](xpp-conditional.md)
+ [Operators](xpp-operators.md)
+ [Classes and methods](xpp-classes-methods.md)
+ [Data selection and manipulation](xpp-data/xpp-data-home-page.md)
+ [Macros](xpp-macros.md)
+ [Attribute classes](xpp-attribute-classes.md)

## Additional resources

+ [X++ Syntax](xpp-syntax.md)
+ [X++ and C# Comparison](xpp-cs-comparison.md)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
