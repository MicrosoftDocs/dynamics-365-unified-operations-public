---
# required metadata

title: Synchronizing on-demand with the Dynamics 365 Supply Chain Management price engine
description: This topic describes how to use the pricing engine in Dynamics 365 Supply Chain Management from Dynamics 365 Sales.
author: RamaKrishnamoorthy
manager: AnnBe
ms.date: 03/10/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User, IT Pro
# ms.devlang: 
ms.reviewer: rhaertle
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: global
ms.search.industry: 
ms.author: ramasri
ms.dyn365.ops.version: 
ms.search.validFrom: 2020-03-10

---

# Synchronizing on-demand with the Dynamics 365 Supply Chain Management price engine

[!include [banner](../../includes/banner.md)]

[!include [preview banner](../../includes/preview-banner.md)]

Dynamics 365 Supply Chain Management includes a pricing engine that handles trade agreements, price lists, customer loyalty programs, promotions, and discounts. The pricing engine uses complex rules to determine the best price for the given quotation or order. Using dual-write, you use static pricing or the pricing engine from Supply Chain Management on the Quote and Order forms in Dynamics 365 Sales.

### Using the pricing engine from Supply Chain Management in Dynamics 365 Sales

In **Dynamics 365 Sales**, navigate to **Sales \> Orders**.

1. Click **New** to create a new order, or select an existing order frome the **My Orders** list.
2. Add a new order line.
3. If you are creating a new order, click the **Price Order** button in the menu bar. If you are updating an existing order, click **Recalculate** in the menu bar.

    After you click **Price Order** or **Recalculate***, these fields are automatically filled in:

    + Detail Amount
    + Discount %
    + Discount
    + Pre-Freight Amount
    + Freight Amount
    + Total Tax
    + Total Amount

### How it works

When you click **Price Order** in Dynamics 365 Sales, the **Totals** function in the **Sales Order \> View** tab in Supply Chain
Management for the associated Sales Order is invoked. The values in the Dynamics 365 Sales order total are used to populate the corresponding fields in Supply Chain Management.

When the Sales Order Total is calculated in Supply Chain Management it goes through the existing trade and sales agreements for the customer and products at and calculated the Total values. When the '**Price Order** button is invoked all the setup done in Supply Chain Management is automatically reflected in Dynamics 365 Sales.

### Limitations

When the fields are populated in Dynamics 365 Sales, these limitations apply:

+ Any setup of Charges and Charges allocation in Supply Chain Management is not replicated in Dynamics 365 Sales.
+ Pricing does not take into consideration special Retail Pricing that is specified in the **Retail Channel** field in Supply Chain Management sales order line form.
+ Discounts that are defined in the Trade Allowance Management section of Supply Chain Management are not considered.
