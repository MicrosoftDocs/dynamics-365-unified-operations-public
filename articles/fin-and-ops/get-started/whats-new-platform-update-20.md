---
# required metadata

title: What's new or changed in Dynamics 365 for Finance and Operations platform update 20 (September 2018)
description: This topic describes features that are either new or changed in Dynamics 365 for Finance and Operation platform update 20. This version was released in September 2018.
author: tonyafehr
manager: AnnBe
ms.date: 09/18/18
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: tfehr
ms.search.scope:  Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: a765a61c-52a3-45c5-b578-68b9249c592a
ms.search.region: Global
# ms.search.industry: 
ms.author: tfehr
ms.search.validFrom: 2017-09-30 
ms.dyn365.ops.version: Platform update 16, Platform update 17, Platform update 18, Platform update 19, Platform 20

---
# What's new or changed in Dynamics 365 for Finance and Operations platform update 20 (September 2018)

[!include [banner](../includes/banner.md)]

This topic describes features that are either new or changed in Dynamics 365 for Finance and Operations platform update 20. This version was released in September 2018 has a build number of XXXXX.

> [!NOTE]
> This platform release is cumulative. It contains new or changed features from Platform update 16, Platform update 17, Platform update 18, Platform update 19, and Platform update 20, as well as all earlier updates. 

> This update is currently available for targeted customers and will be available to all users in the future. For more information about standard and targeted releases, see the [Standard and targeted platform releases](https://docs.microsoft.com/en-us/dynamics365/unified-operations/fin-and-ops/get-started/public-preview-releases) topic.

### Announcing the Dynamics 365 October '18 release notes
Wondering about upcoming and recently released capabilities in any of our business apps or platform? 

[Check out the October '18 release notes](https://go.microsoft.com/fwlink/?linkid=870424). We've captured all the details, end to end, top to bottom, in a single document that you can use for planning. 

### Platform update 20 bug fixes
For information about the bug fixes included in Platform update 20, log in to Lifecycle Services (LCS) and view this [KB article](https://go.microsoft.com/fwlink/?linkid=875608).


## Performance improvement in the Visual Studio development environment
This update includes fixes that improve your experience while using the X++ code editor and metadata properties
window. This includes:
-  When hovering the mouse pointer over a label ID in the X++ code editor, Visual Studio used to “freeze” in
some cases. This bug has been resolved.
-  Opening the X++ code editor is faster, especially when working with large files. We have optimized the
process of loading referenced assemblies.
-  Opening the EDT property lookup from the properties window is significantly faster. In some cases, time was
reduced from 8 seconds to 0.03 seconds.

## Performance improvements in the web client that may affect test automation code
With this update, data that is bound to controls that are not visible to the end user will not be sent over from the
server until the control becomes visible. If you use test automation that uses form adaptors or the SysTest framework,
you may need to make changes to your test code. For more details, refer to the [Performance improvements that may
affect test automation code blog post] (https://community.dynamics.com/365/financeandoperations/b/newdynamicsax/archive/2018/05/08/performance-improvements-that-may-break-automated-test-code).

## Change form patterns to custom using form extensions
With this update, you can change a form's pattern to custom by using a form extension. This allows for more
flexibility in the structure of the form that you are extending. However, the basic structure should remain the same so
that form updates in the future don't conflict with your customizations.

## Adding and removing columns in a grid is easier
Some of the most typical changes that a user makes to a grid are adding, removing, resizing, and reordering
columns. In this update, we’ve made adding and removing columns easier by promoting the **Add columns** and **Hide this column** actions directly into the grid column header context menus. 

