---
# required metadata

title: Price adjustments and discounts
description: This article provides information about price adjustments and discounts in Retail and commerce in Microsoft Dynamics 365 for Operations.
author: josaw1
manager: AnnBe
ms.date: 2015-12-03 21 - 02 - 28
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: annbe
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 15891
ms.assetid: f80bf68d-8b1e-44e8-8bad-90a99e047726
ms.search.region: global
ms.search.industry: Retail
ms.author: scotttuc
ms.dyn365.ops.intro: Feb-16
ms.dyn365.ops.version: AX 7.0.0

---

# Price adjustments and discounts

This article provides information about price adjustments and discounts in Retail and commerce in Microsoft Dynamics 365 for Operations.

In Dynamics 365 for Operations - Retail, you can make price adjustments to products, and can also set up discounts that are applied to a line item or a transaction at the point of sale (POS), in a call center sales order, or in an online order. Both price adjustments and discounts can be linked to price groups. For both price adjustments and discounts, you can specify a single start date and end date or a reoccurring period, a discount code, and a few additional attributes. Price adjustments and discounts can be applied to products, variants, or categories. If more than one discount applies to a product, a customer might receive either one of the discounts or a combined discount, depending on the configuration of the discount. Dynamics 365 for Operations automatically applies the discount or combination of discounts that gives the best price to the customer. When you set up a price adjustment or a discount, be sure to confirm that price groups are assigned to the correct channels, catalogs, affiliations, or loyalty programs that you want the discount to apply to. Additionally, if you want to automatically generate the discount ID, set up number sequences on the **Retail parameters** page before you define a new price adjustment or discount. **Note:** You can delete a price adjustment or a discount. However, statistical information will be lost.

### Types of discounts

There are four types of retail discounts:

-   **Simple discount** – A single percentage or amount.
-   **Quantity discount** – A discount that is applied when two or more products are purchased.
-   **Mix and match discount** – A discount that is applied when a specific combination of products is purchased.
-   **Threshold discount** – A discount that is applied when the transaction total is more than a specified amount.

Both price adjustments and discounts can be associated with price groups. Price groups can then be associated with channels, catalogs, affiliations, and loyalty programs.

