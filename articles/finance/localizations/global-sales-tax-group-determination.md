---
# required metadata

title: Sales tax applicability and sales tax group determination logic
description: This topic explains the logic for determining sales tax applicability and sales tax groups in the tax feature setup.
author: epodkolz
ms.date: 09/14/2021
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

[!include [banner](../includes/banner.md)]

This topic explains the logic for determining sales tax applicability and sales tax groups in the tax feature setup.

## Matching logic

Before the 10.0.21 update, the Tax calculation service used straightforward logic to find a tax applicability rule in the tax applicability matrix:

1. Start at the first row of the matrix.
2. Check each row until a matching condition is found.
3. Stop the search.

In the 10.0.21 update, the applicability logic tries to match the condition that includes the most input fields. Each field that has a value has a *weight* of 10. A condition that has a higher total weight has a higher priority.

### Example

The following example shows how the matching logic works.

In Regulatory Configuration Service (RCS), the **Tax group applicability** tab is configured as shown in the following table.

| Business process | Currency | Item code | Tax group | Weight |
|------------------|----------|-----------|-----------|--------|
| Purchase         | EUR      |           | TG\_A     | 20     |
| Purchase         | EUR      | D0001     | TG\_B     | 30     |

For the first line in the table, two input fields are set. Therefore, the line has a weight of 20. For the second line, three fields are set. Therefore, the line has a weight of 30.

When sales tax is calculated for a purchase order that has the EUR currency and item D0001, the Tax calculation service uses the condition that has a higher weight. Therefore, it uses the second line in the table.

> [!NOTE]
> On the **Applicability rule** tabs, line numbers aren't visible, and the **Move up** and **Move down** buttons are no longer available. After you save a setup and reopen the page, the lines are ordered according to their weight.
> 
> Even though line numbers aren't visible in the UI, they are still available in the table. If two lines have the same weight, the line that has the smaller line number is used.

## Sales tax group and item sale tax group determination logic

Before the 10.0.21 update, the **Sales tax group** and **Item sales tax group** fields weren't editable. Instead, the field values were determined by the Tax calculation service, based on the condition that was met for the tax code applicability rule.

In the 10.0.21 update, the sales tax group and item sale tax group determination logic has been updated. When a document line is created on a business document, such as a sales order, purchase order, or vendor invoice, the **Sales tax group** and **Item sales tax group** fields are set to the values from the master data. Then, when tax is calculated, the fields are updated according to the conditions that are configured in the Tax feature setup on the **Tax group applicability** and **Item tax group applicability** tabs in RCS.

If no applicability rule is configured for the tax group or item tax group in the Tax feature setup in RCS, the Tax calculation service uses the default rules from the master data in Microsoft Dynamics 365 Finance.

> [!NOTE]
> The sales tax group and item sales tax group must be created and maintained in RCS.

You can update the tax groups that the Tax calculation service determined, without having to reconfigure the Tax feature. For example, you might have to update the tax groups because the rule is incorrectly set up, or some exception to the rule is required. By setting the **Override sales tax** option to **Yes** on the line details page for a document line, you can select the required sales tax group and item sales tax group.

![Override sales tax option set to Yes on the line details page for a document line](media/Pict1%20Override%20sales%20tax%20parameter.jpg)

The **Sales tax group** and **Item sales tax group** fields list only tax groups where the **Source** field is set to **Tax calculation service**. This value indicates that the tax groups were synchronized from the Tax feature setup in RCS.

![Source field set to Tax calculation service for an item sales tax group on the Item sales tax groups page](media/Pict2%20Source%20field%20in%20Item%20sales%20tax%20group.jpg)

The tax codes are calculated based on the intersection of the tax codes that are defined on the **Tax group** and **Item tax group** tabs in the Tax feature setup in RCS.

> [!NOTE]
> If the **Sales tax group** or **Item sales tax group** field is left blank, and the **Override sales tax** option is set to **Yes**, the line won't be sent to the Tax calculation service for processing.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
