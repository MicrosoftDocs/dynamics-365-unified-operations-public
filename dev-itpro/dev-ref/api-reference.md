---
# required metadata

title: API, class, and table reference
description: This topic describes where to find API documentation in Visual Studio and on the Microsoft docs site.
author: RobinARH
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
ms.custom: 63853
ms.assetid: 46e5e47b-2c80-44fd-a7a3-e41884da2f55
ms.search.region: Global
# ms.search.industry: 
ms.author: robinr
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# API, class, and table reference

This topic describes where to find API documentation in Visual Studio and on the Microsoft docs site.

Application classes and tables
------------------------------

### Application class and table documentation is in Visual Studio

You can find documentation for the Application classes in Microsoft Visual Studio by searching for the application programming interface (API) in Application Explorer and then displaying the code. You can find additional metadata about the API in the **Properties** window.

### Programming with application tables and classes

Application tables are being similar to application classes, but with the following differences from classes:

-   Tables are persistent.
-   Table fields are always public.
-   A table almost always corresponds to a real object.
-   The definition of a table must sometimes be erased if you later want another table to extend it.

### Design Pattern of private new in application classes

All application classes are under Application Explorer &gt; Classes. Every application class has the constructor method named `new`, even if the class has no new node in the AOT. If the class has no explicit new node, the implicit `new` method is public. A design pattern that is sometimes used in the application classes is to declare the explicit `new` constructor method as `private`. Then a `public static` method is added to call the `new` method. The static method can restrict or control the call the `new` method based on various conditions, if necessary.

## System classes and tables
### System API, class, and table documentation is on the Microsoft docs site

Documentation for the classes and functions that are listed under **System Documentation** in Application Explorer is available on the Microsoft docs site.

## X++ compiletime functions
[X++ compile-time functions](xpp-compile-time-functions.md)

## X++ runtime functions
[X++ run-time functions](xpp-string-run-time-functions.md):

-   [X++ container run-time functions](xpp-container-run-time-functions.md)
-   [X++ business run-time functions](xpp-business-run-time-functions.md)
-   [X++ conversion run-time functions](xpp-conversion-run-time-functions.md)
-   [X++ date run-time functions](xpp-date-run-time-functions.md)
-   [X++ math run-time functions](xpp-math-run-time-functions.md)
-   [X++ reflection run-time functions](xpp-reflection-run-time-functions.md)
-   [X++ session run-time functions](xpp-session-run-time-functions.md)
-   [X++ string run-time functions](xpp-string-run-time-functions.md)

## System tables
[System tables](system-tables.md)

## System classes
-   [A classes](a-classes.md)
-   [B classes](b-classes.md)
-   [C classes](c-classes.md)
-   [D classes](d-classes.md)
-   [E classes](e-classes.md)
-   [F classes: FieldBinding to FormBuildAnimateControl](fieldbinding-classes.md)
-   [F classes: FormBuildButtonControl to FormBuildFastTabSummarySeparator](FormBuildButtonControl-classes.md)
-   [F classes: FormBuildFilterPaneControl to FormBuildRealControl](FormBuildFilterPaneControl-classes.md)
-   [F classes: FormBuildReferenceControl to FormButtonSeparatorControl](FormBuildReferenceControl-classes.md)
-   [F classes: FormChangeTracker to FormControlEventArgs](FormChangeTracker-classes.md)
-   [F classes: FormDataObject to FormFastTabHeaderControl](FormDataObject-classes.md)
-   [F classes: FormFastTabSummarySeparator to FormGridControl](FormFastTabSummarySeparator-classes.md)
-   [F classes: FormGroupControl to FormIntControl](FormGroupControl-classes.md)
-   [F classes: FormListBoxControl to FormNotifyEventArgs](FormListBoxControl-classes.md)
-   [F classes: FormObject to FormRealControl](FormObject-classes.md)
-   [F classes: FormReferenceControl to FormStringControl](FormReferenceControl-classes.md)
-   [F classes: FormTabControl to FormWindowControl](FormTabControl-classes.md)
-   [G classes](g-classes.md)
-   [H classes](h-classes.md)
-   [I classes](i-classes.md)
-   [J classes](j-classes.md)
-   [K classes](k-classes.md)
-   [L classes](l-classes.md)
-   [M classes](m-classes.md)
-   [N classes](n-classes.md)
-   [O classes](o-classes.md)
-   [P classes](p-classes.md)
-   [Q classes](q-classes.md)
-   [R classes](r-classes.md)
-   [S classes](s-classes.md)
-   [T classes](t-classes.md)
-   [U classes](u-classes.md)
-   [V classes](v-classes.md)
-   [W classes](w-classes.md)
-   [X classes](x-classes.md)



