---
# required metadata

title: Form pattern add-ins
description: The tools for Visual Studio include a number of add-ins that support pattern usage. 
author: jasongre
manager: AnnBe
ms.date: 08/17/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: robinr
ms.search.scope: AX 7.0.0, Operations, UnifiedOperations
# ms.tgt_pltfrm: 
ms.custom: 28891
ms.search.region: Global
# ms.search.industry: 
ms.author: jasongre
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Form pattern add-ins

The tools for Visual Studio include a number of add-ins that support pattern usage. 

## Form statistics add-in
The **Form statistics** add-in provides a summary of the pattern usage for forms. When you access the **Form statistics** add-in from the **Dynamics 365** menu, it displays statistics for all forms. When you access the add-in from the shortcut menu for a form that is open in the form designer, it displays statistics for that form only. 

![Form statistics report](media/form-statistics.png) 

## Forms Pattern report
The **Form Patterns** report provides pattern information about every form, including whether the form uses a top-level form pattern, is a custom form, or is not specifying a form pattern. To generate the **Form Patterns** report, start Microsoft Visual Studio, click the **DYNAMICS 365** menu, expand **Add-ins**, and then click **Run the form patterns report**. The process will take several seconds. After the report has been generated, a dialog box will provide the location of the report. Browse to the specified location, and open the file in Microsoft Excel. You can then filter the report down to the models that interest you.

For more information about Visual Studio add-ins, see [Tools add-ins for Visual Studio](../dev-tools/developer-tools-add-ins.md).
