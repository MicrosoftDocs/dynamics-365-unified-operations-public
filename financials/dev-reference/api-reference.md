---
# required metadata

title: API, class, and table reference
description: This topic describes where to find API documentation in Visual Studio and on the wiki.
author: RobinARH
manager: AnnBe
ms.date: 2016-03-09 00 - 09 - 13
ms.topic: 
ms.prod: 
ms.service: 
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
ms.assetid: 60ef1e50-575d-42a2-85c4-1b12b489653f
ms.search.region: Global
# ms.search.industry: 
ms.author: robinr
ms.dyn365.ops.intro: Feb-16
ms.dyn365.ops.version: AX 7.0.0

---

# API, class, and table reference

This topic describes where to find API documentation in Visual Studio and on the wiki.

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
### System API, class, and table documentation is on the Help wiki

Documentation for the classes and functions that are listed under **System Documentation** in Application Explorer is available on the Help wiki.

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
-   [F classes: FormBuildButtonControl to FormBuildFastTabSummarySeparator](http://ax.help.dynamics.com/en/wiki/FormBuildButtonControl-classes/)
-   [F classes: FormBuildFilterPaneControl to FormBuildRealControl](http://ax.help.dynamics.com/en/wiki/FormBuildFilterPaneControl-classes/)
-   [F classes: FormBuildReferenceControl to FormButtonSeparatorControl](http://ax.help.dynamics.com/en/wiki/FormBuildReferenceControl-classes/)
-   [F classes: FormChangeTracker to FormControlEventArgs](http://ax.help.dynamics.com/en/wiki/FormChangeTracker-classes/)
-   [F classes: FormDataObject to FormFastTabHeaderControl](http://ax.help.dynamics.com/en/wiki/FormDataObject-classes/)
-   [F classes: FormFastTabSummarySeparator to FormGridControl](http://ax.help.dynamics.com/en/wiki/FormFastTabSummarySeparator-classes/)
-   [F classes: FormGroupControl to FormIntControl](http://ax.help.dynamics.com/en/wiki/FormGroupControl-classes/)
-   [F classes: FormListBoxControl to FormNotifyEventArgs](http://ax.help.dynamics.com/en/wiki/FormListBoxControl-classes/)
-   [F classes: FormObject to FormRealControl](http://ax.help.dynamics.com/en/wiki/FormObject-classes/)
-   [F classes: FormReferenceControl to FormStringControl](http://ax.help.dynamics.com/en/wiki/FormReferenceControl-classes/)
-   [F classes: FormTabControl to FormWindowControl](http://ax.help.dynamics.com/en/wiki/FormTabControl-classes/)
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

## Additional resources
-   Additional help is available as task guides inside Dynamics 365 for Operations. To access task guides, click the Help button on any page.
-   For information about Microsoft Dynamics 365 for Operations training, see [Microsoft eLearning](https://mbspartner.microsoft.com/AX/LearningPlans) (requires a CustomerSource account).


