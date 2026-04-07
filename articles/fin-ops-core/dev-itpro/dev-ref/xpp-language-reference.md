---
title: X++ language reference
description: Learn about programming guidance for X++, including a table that outlines descriptions for various X++ language features.
author: pvillads
ms.author: pvillads
ms.topic: language-reference
ms.date: 03/31/2026
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
ms.collection: get-started
---

# X++ language reference

[!include [banner](../includes/banner.md)]

X++ is an object-oriented, application-aware, and data-aware programming language used in enterprise resource planning (ERP) programming and in database applications. It provides system classes for a broad range of system programming areas, highlighted in the following table.

| X++ language feature | Description |
|-----|-----|
| Classes              | In addition to system classes, application classes manage many types of business processes. X++ supports reflection on classes. |
| Tables               | X++ programmers can access relational tables. X++ includes keywords that match most of the keywords in standard SQL. X++ supports reflection on tables. |
| User interface       | Manipulation of user interface items, such as forms and reports.|
| Best practice checks | The compiler checks X++ code for syntax errors. The compile process also performs best practice checks. Violations of best practices can generate compiler messages.|
| Garbage collection   | The X++ runtime execution engines have automatic mechanisms to discard objects that are no longer referenced, so that memory space can be reused. |
| Interoperability     | X++ supports interoperability between classes written in X++ and in C\# (or other .NET Framework languages).                                      |
| File manipulation    | X++ supports file input and output, including XML building and parsing. |
| Collections          | X++ supports dynamic arrays and includes several collection objects.|

## X++ compiles to Microsoft .NET CIL (Common Intermediate Language)

X++ source code compiles to Microsoft .NET CIL (Common Intermediate Language). CIL is the output of the .NET compilers for C\# and Visual Basic. The advantages of compiling to CIL include:

- Your code runs much faster than in previous versions (AX2012 and earlier).
- It's easier to write application logic in other managed languages and integrate that logic into your X++ app.
- Your X++ apps can efficiently reference classes that are available in other .NET assembly DLL files.
- Many .NET tools can operate on the CIL.

The standard compilation unit is the same as for other .NET languages. If any method in a model element (for example, a class, form, or query) fails to compile, the whole compilation fails.

If you're upgrading code from previous versions (AX2012 and earlier), note that CIL helper methods such as `Global::runClassMethodIL` are removed because they're no longer relevant.

For more information, see [What is "managed code"?](/dotnet/standard/managed-code).

### The ignore list

Assemblies are generated from successful compilations, and the runtime system can't load incomplete assemblies. When porting legacy applications, you might encounter scenarios where it's beneficial to get things running in a staged fashion. You might need to test parts of the application before everything is ported. While this approach is useful for this very limited scenario, it shouldn't be used once the application is ready for production, since it hides problems that occur at runtime, after the system is deployed. To ignore parts of your X++ code, specify a method in an XML by selecting **Edit Best Practice Suppressions** from the context menu on the project. This action opens an XML document where you maintain the exclusions.

## Concepts

The X++ language programming reference is divided into these sections:

- [Variables and data types](xpp-variables-data-types.md)
- [Statements, loops, and exception handling](xpp-conditional.md)
- [Operators](xpp-operators.md)
- [Classes and methods](xpp-classes-methods.md)
- [Data selection and manipulation](xpp-data/xpp-data-home-page.md)
- [Macros](xpp-macros.md)
- [Attribute classes](xpp-attribute-classes.md)

## Additional resources

- [X++ Syntax](xpp-syntax.md)
- [X++ and C# Comparison](xpp-cs-comparison.md)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
