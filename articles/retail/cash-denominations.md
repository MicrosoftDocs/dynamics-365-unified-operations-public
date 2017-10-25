---
# required metadata

title: Configure cash denominations for POS
description: Cash denominations for notes and coins can be defined in the back office to be used by cashiers, sales associates, and managers at the store from within the POS.
author: jblucher
manager: AnnBe
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Core, AX 7.0.0, Operations, UnifiedOperations, Retail
# ms.tgt_pltfrm: 
ms.custom: 16231
ms.assetid: f28a827c-3a50-4d5e-83eb-e5a768db70a1
ms.search.region: global
ms.search.industry: Retail
ms.author: jeffbl
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0, Retail July 2017 update

---

# Configure cash denominations for POS

[!include[banner](includes/banner.md)]

Cash denominations for notes and coins can be defined in the back office to be used by cashiers, sales associates, and managers at the store from within the POS. These denominations can be used to aid in counting cash for end of day tender declarations or for quickly tendering a sale.

## Define denominations
The denominations are set up per store on the **Set up** > **Cash declaration option from the store property** page. 

![cash denominations](./media/image1-denomination.png)

To define a denomination:
1. Click **New**.
1. Specify the type (coin or note).
1. Specify the amount (value).

![cash denominations](./media/image2-denomination.png)

## Configure the functionality profile
When paying by cash in POS, the user can use the note denominations to quickly enter the amount paid by the customer. In the functionality profile, you can configure the two options for showing the denomination in POS.

**Greater or equal to amount due**: By default, POS will only show the note denominations that are greater than the amount due, which allows for one-touch tendering. For example, if the amount due is $7.50, POS would show the following denominations: $10, $20, $50, and $100. Touching any of these amounts will automatically tender the sale for that amount. The $1 and $5 notes are not shown since these amounts are less than the amount due.

**All denominations**: Select this option to always show all note denominations in POS, regardless of the amount due. This means that the user can use a combination of notes to reach the amount due. For example, if the amount due is $25.00, the user can choose $20 and $5 to complete the sale.
