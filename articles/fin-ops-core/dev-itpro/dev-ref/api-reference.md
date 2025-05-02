---
title: API, class, and table resources
description: Learn about where to find API documentation in Visual Studio and Microsoft Learn, including application and system classes and tables.
author: josaw1
ms.author: josaw
ms.topic: language-reference
ms.date: 07/23/2019
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
---

# API, class, and table resources

[!include [banner](../includes/banner.md)]

This article describes where to find API documentation in Visual Studio and Microsoft Learn.

## Application classes and tables

### Application class and table documentation is in Visual Studio

You can find documentation for the Application classes in Microsoft Visual Studio. Search for the class name in Application Explorer and then display the code. You can find additional metadata about the class in the **Properties** window. You can download a list of all the tables in the [Technical Reference Reports](/dynamics/s-e/global/axtechrefrep_61). For more information, see [Find information about standard data entities](../data-entities/data-entities-report.md).

### Programming with application tables and classes

Application tables are similar to application classes, but with the following differences from classes:

- Tables are persistent.
- Table fields are always public.
- A table almost always corresponds to a real object.
- The definition of a table must sometimes be erased if you later want another table to extend it.

### Design pattern of private new in application classes

All application classes are under Application Explorer &gt; Classes. Every application class has the constructor method named `new`, even if the class has no **new** node in the Application Explorer. If the class has no explicit **new** node, the implicit **new** method is public. A design pattern that is sometimes used in the application classes is to declare the explicit **new** constructor method as **private**. Then a **public static** method is added to call the **new** method. The static method can restrict or control the call the **new** method based on various conditions, if necessary.

## System classes and tables

### System API, class, and table documentation in Microsoft Learn

Documentation for the classes and functions that are listed under **System Documentation** in Application Explorer is available in [Microsoft Learn documentation](/docs/).

## X++ compile-time functions

[X++ compile-time functions](xpp-compile-time-functions.md)

## X++ run-time functions

[X++ run-time functions](xpp-string-run-time-functions.md):

- [X++ container run-time functions](xpp-container-run-time-functions.md)
- [X++ business run-time functions](xpp-business-run-time-functions.md)
- [X++ conversion run-time functions](xpp-conversion-run-time-functions.md)
- [X++ date run-time functions](xpp-date-run-time-functions.md)
- [X++ math run-time functions](xpp-math-run-time-functions.md)
- [X++ reflection run-time functions](xpp-reflection-run-time-functions.md)
- [X++ session run-time functions](xpp-session-run-time-functions.md)
- [X++ string run-time functions](xpp-string-run-time-functions.md)

## System tables

[System tables](system-tables.md)

## System classes

The reference documentation for the system classes is in the .NET API browser.

[API reference for finance and operations apps](/dotnet/api/fin-ops-api-landing)

[Microsoft.Dynamics.Ax.Xpp namespace](/dotnet/api/microsoft.dynamics.ax.xpp)

[Dynamics.AX.Application namespace](/dotnet/api/dynamics.ax.application)


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
