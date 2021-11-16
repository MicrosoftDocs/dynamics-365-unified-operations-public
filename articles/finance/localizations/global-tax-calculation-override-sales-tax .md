---
# required metadata

title: Override sales tax option
description: This topic provides information about the Override sales tax option.
author: epodkolz
ms.date: 11/16/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region:
# ms.search.industry: 
ms.author: epodkolz
ms.search.validFrom:
ms.dyn365.ops.version: AX 10.0.24
---

# Override sales tax option

[!include [banner](../includes/banner.md)]

[!include [banner](../includes/preview-banner.md)]

This topic provides information about the Override sales tax option.

When using the Tax calculation service, the Sales tax group and Item sales tax group on the document line are determined based on the applicability rules configured in the Tax feature setup and these field are not editable. You can update the tax groups that the Tax calculation service determined, without having to reconfigure the Tax feature. For example, you might have to update the tax groups because the rule is incorrectly set up, or some exception to the rule is required. By setting the **Override sales tax** option to **Yes** on the line details page for a document line, you can select the required sales tax group and item sales tax group.

![Override sales tax option set to Yes on the line details page for a document line](media/Pict1%20Override%20sales%20tax%20parameter.jpg)

The **Sales tax group** and **Item sales tax group** fields list only tax groups where the **Source** field is set to **Tax calculation service**. This value indicates that the tax groups were synchronized from the Tax feature setup in RCS.

![Source field set to Tax calculation service for an item sales tax group on the Item sales tax groups page](media/Pict2%20Source%20field%20in%20Item%20sales%20tax%20group.jpg)

The tax codes are calculated based on the intersection of the tax codes that are defined on the **Tax group** and **Item tax group** tabs in the Tax feature setup in RCS.

> [!NOTE]
> If the **Sales tax group** or **Item sales tax group** field is left blank, and the **Override sales tax** option is set to **Yes**, the line won't be sent to the Tax calculation service for processing.


This option is added to the Customer and Vendor master data on the _Invoice and delivery_ FastTab. It is defaulted to the Sales order, Purchase order, Free text invoice header, and further to the line level of the respective document.

## Update order lines

An option to bulk update lines if the **Override sales tax** is changed on the header level is added to the **Update order lines** parameters pages for Sales order, Sales quotation, and Purchase order.
For example, if the option is set to _Prompt_, then, when the **Override sales tax** is changed on the header of the document, the dialog appears and lets the user to select whether the document lines should be updated as well.

> [!NOTE]
> Header level and line level charges inherit the **Override sales tax** option from the header or line of the document respectively.
> Current limitation:
> When updating override sales tax checkbox on a header or line level the respective charges do not inherit this checkbox in case the charges were already created.
