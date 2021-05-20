---
# required metadata

title: Line discount calculation from the unit price for Poland
description: For legal entities in Poland, the line discount can be calculated from the unit price of an invoice line instead of from a line amount. This topic provides information about the Line discount calculation from unit price method and explains how to set it up.
author: ShylaThompson
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.custom: 263424
ms.search.region: Poland
# ms.search.industry: 
ms.author: kfend
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611

---

# Line discount calculation from the unit price for Poland

[!include [banner](../includes/banner.md)]

For legal entities in Poland, the line discount can be calculated from the unit price of an invoice line instead of from a line amount. This topic provides information about the Line discount calculation from unit price method and explains how to set it up.

For legal entities in Poland, the line discount doesn't have to be calculated from a line amount. Instead, it can be calculated from the unit price of an invoice line. When the Line discount calculation from unit price method is used, the discounted unit price is rounded before the line amount is calculated. The following table shows how the line discount is calculated by both the standard method and the Line discount calculation from unit price method.

|Quantity|Price|Discount percentage|Net amount (Standard method)|Net amount (Line discount calculation from unit price method)|
|--------|-----|-------------------|---------------|------------------------------------------------|
|100     |6.75 |5                  |641.25 (6.75 × 100 = 675.00; 675 × 0.95 = 641.25)|641.00 (6.75 × 0.95 = 6.4125; 6.41 × 100 = 641.00)|

> [!NOTE]
> The 0.95 that is used in the calculations equals 1.00 – 0.05, where 0.05 is the discount amount if the unit price is 1.00.

## Set up the Calculation of line discount parameter
The Line discount calculation from unit price method affects both Accounts receivable and Accounts payable, and is set up on the **Accounts receivable parameters** page and the **Procurement and sourcing parameters** page. The **Calculation of line discount** parameter has the following options:

-   **From line value** – Use the standard method to calculate the line discount.
-   **From unit price** – Use the Line discount calculation from unit price method to calculate the line discount.

The **Calculation of line discount** parameter affects the following documents:

-   Sales orders
-   Purchase orders
-   Vendor invoices






[!INCLUDE[footer-include](../../includes/footer-banner.md)]