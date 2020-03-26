---
# required metadata

title: Sync with the Dynamics 365 Supply Chain Management pricing engine on demand
description: This topic describes how to use the pricing engine in Microsoft Dynamics 365 Supply Chain Management from Dynamics 365 Sales.
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

# Sync with the Dynamics 365 Supply Chain Management pricing engine on demand

[!include [banner](../../includes/banner.md)]

[!include [preview banner](../../includes/preview-banner.md)]

Microsoft Dynamics 365 Supply Chain Management includes a pricing engine that handles trade agreements, price lists, customer loyalty programs, promotions, and discounts. The pricing engine uses complex rules to determine the best price for a given quotation or order. When you use dual-write, you use either static pricing or the pricing engine from Dynamics 365 Supply Chain Management on the Quote and Order pages in Dynamics 365 Sales.

## Use the pricing engine from Supply Chain Management in Sales

1. In Sales, go to **Sales \> Orders**.
2. Select **New** to create a new order, or select an existing order in the **My Orders** list.
3. Add a new order line.
4. If you're creating a new order, select **Price Order** on the Action Pane. If you're updating an existing order, select **Recalculate** on the Action Pane.

    The following fields are automatically filled in:

    + Detail Amount
    + Discount %
    + Discount
    + Pre-Freight Amount
    + Freight Amount
    + Total Tax
    + Total Amount

## How it works

When you select **Price Order** in Sales, the **Totals** function on the **Sales Order \> View** tab in Supply Chain Management is called for the associated sales order. The values in the order total in Sales are used to fill in the corresponding fields in Supply Chain Management.

When the sales order total is calculated in Supply Chain Management, the calculation evaluates the existing trade agreements and sales agreements for the customer and the products that are listed in the sales order. This information is used to calculate the totals. When **Price Order** is selected, Sales automatically reflects all the setup that has been done in Supply Chain Management.

## Limitations

When the fields in Sales are filled in, the following limitations apply:

+ The setup of charges and charge allocations in Supply Chain Management isn't replicated in Sales.
+ Pricing doesn't consider special retail pricing that is specified in the **Retail Channel** field on the sales order line page in Supply Chain Management.
+ Discounts that are defined in the **Trade Allowance Management** section of Supply Chain Management aren't considered.
