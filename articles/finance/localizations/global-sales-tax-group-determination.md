---
# required metadata

title: Sales tax applicability and sales tax group determination logic
description: This topic explains the sales tax applicability and sales tax group determination logic in the tax feature setup.
author: epodkolz
ms.date: 
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
ms.dyn365.ops.version: AX 10.0.21
---

# Sales tax applicability and sales tax group determination logic

This topic explains the sales tax applicability and sales tax group determination logic in the tax feature setup.

## Matching logic

Before the 10.0.21 update, the Tax calculation service was using a straightforward logic to find a tax applicability rule in the tax applicability matrix:

 - Start from the 1st row of the matrix.
 - Check row by row until a matching condition is found.
 - Stop the search.

Starting from the 10.0.21 update, the applicability logic tries to match the condition that hits most input fields. Each field with a value has a ‘weight’ the equals 10. A condition with a higher total weight gets a higher priority.
The following example demonstrates how the matching logic works:

 - The **Tax group applicability** is configured as follows:

| Business Process | Currency | Item Code | Tax Group | “Weight” |
|------------------|----------|-----------|-----------|----------|
| **Purchase** | EUR || TG_A | 20 |
| **Purchase** | EUR | D0001 | TG_B | 30 |

 - The 1st line has two input fields that are set, thus its weight is 20; the 2nd line has three fields set, thus its weight is 30. 
 - When sales tax is calculated for a purchase order that has the EUR currency and the D0001 item on it, the Tax calculation service will use the condition with a higher weight, which is the second line in the above table. 

> [!NOTE]
> Starting from the 10.0.21 update, the Line number is not visible, and the Move up and Move down buttons are no longer available on the applicability rule tabs. After saving a setup and re-opening the page, the lines will be re-ordered according to their weights.

If two lines have the same weight, the line with a smaller line number (not visible in the UI but still available in the table) will be used. The functionality that will allow user to adjust the line number is under consideration.

## Sales tax group and Item sale tax group determination logic

The sales tax group and item sale tax group determination logic has been updated as well. Before the 10.0.21 update, the **Sales tax group** and **Item sales tax group** fields were not editable, and Tax calculation was determining them based on the condition that was met for the **Tax code applicability rule**. 
Starting from the 10.0.21 update, when a document line (that is, an SO, PO, or Vendor invoice line) is created, **Sales tax group** and **Item sales tax group** are populated with the values from the customer/vendor/item/category master data. Then, when tax is calculated, the fields are updated according to the conditions configured in the Tax feature setup on the **Tax group applicability** and **Item tax group applicability** tabs in RCS.
If no applicability rule is configured for Tax group or Item tax group in the Tax feature setup in RCS, the Tax calculation service uses the default ones from the customer/vendor/item/category master data in Dynamics 365 Finance.

> [!NOTE]
> The sales tax group and item sales tax group must be created and maintained in RCS. 

You can update the tax groups determined by the Tax calculation service without re-configuring the Tax feature if needed. For instance, the rule is set up incorrectly or some exception from the rule is required. By enabling the **Override sales tax** option on the document line, you can select the required **Sales tax group** and **Item sales tax group**.

![Pict1 Override sales tax parameter](https://user-images.githubusercontent.com/27483882/126536049-0d173107-b7a9-4045-82c7-2e3c267f34ca.jpg)

The **Sales tax group** and **Item sales tax group** drop-down lists contain only tax groups that have the **Tax calculation service** value in the **Source** field. It means that they were synchronized from the Tax feature setup in RCS.

![Pict2 Source field in Item sales tax group](https://user-images.githubusercontent.com/27483882/126536162-ab1a7900-3160-43cf-b09d-ff2372e7a6f8.jpg)

The tax codes will be calculated based on the intersection of the tax codes that are defined in the **Tax group** and **Item tax group** tabs in the Tax feature setup in RCS.

> [!NOTE]
> If either the **Sales tax group** or **Item sales tax group** field is left blank, and the **Override sales tax** parameter is set to **Yes**, the line will not be sent to the Tax calculation service for processing.



