---
# required metadata

title: API, class, and table reference | Microsoft Docs
description: This topic describes where to find API documentation in Visual Studio and on the wiki.
author: RobinARH
manager: AnnBe
ms.date: 2016-03-09 00:09:13
ms.topic: 
ms.prod: 
ms.service: 
ms.technology: 

# optional metadata

# keywords: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: 61
ms.suite: Released- Dynamics AX 7.0.0
# ms.tgt_pltfrm: 
ms.custom: 63853
ms.assetid: 169750cb-8bf8-4e58-9c41-0491d8cafdbd
ms.region: Global
# ms.industry: 
ms.author: robinr

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
[X++ compile-time functions](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-reference/x-compile-time-functions)

## X++ runtime functions
[X++ run-time functions](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-reference/x-string-run-time-functions):

-   [X++ container run-time functions](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-reference/x-container-run-time-functions)
-   [X++ business run-time functions](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-reference/x-business-run-time-functions)
-   [X++ conversion run-time functions](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-reference/x-conversion-run-time-functions)
-   [X++ date run-time functions](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-reference/x-date-run-time-functions)
-   [X++ math run-time functions](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-reference/x-math-run-time-functions)
-   [X++ reflection run-time functions](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-reference/x-reflection-run-time-functions)
-   [X++ session run-time functions](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-reference/x-session-run-time-functions)
-   [X++ string run-time functions](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-reference/x-string-run-time-functions)

## System tables
[System tables](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-reference/system-tables)

## System classes
-   [A classes](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-reference/a-classes)
-   [B classes](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-reference/b-classes)
-   [C classes](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-reference/c-classes)
-   [D classes](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-reference/d-classes)
-   [E classes](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-reference/e-classes)
-   [F classes: FieldBinding to FormBuildAnimateControl](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-reference/fieldbinding-classes)
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
-   [G classes](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-reference/g-classes)
-   [H classes](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-reference/h-classes)
-   [I classes](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-reference/i-classes)
-   [J classes](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-reference/j-classes)
-   [K classes](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-reference/k-classes)
-   [L classes](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-reference/l-classes)
-   [M classes](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-reference/m-classes)
-   [N classes](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-reference/n-classes)
-   [O classes](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-reference/o-classes)
-   [P classes](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-reference/p-classes)
-   [Q classes](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-reference/q-classes)
-   [R classes](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-reference/r-classes)
-   [S classes](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-reference/s-classes)
-   [T classes](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-reference/t-classes)
-   [U classes](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-reference/u-classes)
-   [V classes](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-reference/v-classes)
-   [W classes](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-reference/w-classes)
-   [X classes](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-reference/x-classes)

## Additional resources
-   Additional help is available as task guides inside Dynamics 365 for Operations. To access task guides, click the Help button on any page.
-   For information about Microsoft Dynamics 365 for Operations training, see [Microsoft eLearning](https://mbspartner.microsoft.com/AX/LearningPlans) (requires a CustomerSource account).


