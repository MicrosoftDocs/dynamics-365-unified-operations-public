---
title: Configure cash denominations for the point of sale (POS)
description: Cash denominations for notes and coins can be defined in the back office to be used by cashiers, sales associates, and managers at the store from within the POS.
author: josaw1
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: josaw
ms.search.region: global
ms.author: josaw
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0, Retail July 2017 update
ms.assetid: f28a827c-3a50-4d5e-83eb-e5a768db70a1
ms.search.industry: Retail
ms.search.form: RetailStoreTable, RetailStoreCashDeclarationTable
---

# Configure cash denominations for the point of sale (POS)

[!include [banner](includes/banner.md)]

Cash denominations for notes and coins can be defined in the back office to be used by cashiers, sales associates, and managers at the store from within the POS. These denominations can be used to aid in counting cash for end of day tender declarations or for quickly tendering a sale.

## Define denominations

The denominations are set up per store on the **Set up** \> **Cash declaration** option from the store property page.

![Cash declaration option.](./media/image1-denomination.png)

To define a denomination:

1. Click **New**.
1. Specify the type (coin or note).
1. Specify the amount (value).

![Cash declaration denominations page.](./media/image2-denomination.png)

## Configure the functionality profile

When paying by cash in POS, the user can use the note denominations to quickly enter the amount paid by the customer. In the functionality profile, you can configure the two options for showing the denomination in POS.

- **Greater or equal to amount due** – By default, POS will only show the note denominations that are greater than the amount due, which allows for one-touch tendering. For example, if the amount due is $7.50, POS would show the following denominations: $10, $20, $50, and $100. Touching any of these amounts will automatically tender the sale for that amount. The $1 and $5 notes are not shown since these amounts are less than the amount due.
- **All denominations** – Select this option to always show all note denominations in POS, regardless of the amount due. This means that the user can use a combination of notes to reach the amount due. For example, if the amount due is $25.00, the user can choose $20 and $5 to complete the sale.


[!INCLUDE[footer-include](../includes/footer-banner.md)]
