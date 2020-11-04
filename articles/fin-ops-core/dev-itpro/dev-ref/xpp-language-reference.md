---
# required metadata

title: X++ language reference
description: This topic provides programming guidance for X++.
author: RobinARH
manager: AnnBe
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: rhaertle
# ms.tgt_pltfrm: 
ms.custom:
ms.search.region: Global
# ms.search.industry: 
ms.author: rhaertle
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

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
| File manipulation    | File input and output is supported, including XML building and parsing. |
| Collections          | Dynamic arrays are supported and the X++ includes several collection objects.|

The X++ language programming guide is divided into these sections: 

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


