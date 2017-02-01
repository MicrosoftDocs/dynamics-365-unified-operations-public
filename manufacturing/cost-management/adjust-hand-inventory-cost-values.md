---
# required metadata

title: Adjust on-hand inventory cost values | Microsoft Docs
description: Use the Adjustment of on-hand inventory page to adjust the cost value of the on-hand inventory quantities after an inventory close process is run.
author: YuyuScheller
manager: AnnBe
ms.date: 2016-02-24 15:12:09
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

keywords: InventAdjInventOnHand
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: 2094
ms.suite: Released- Dynamics AX 7.0.0
# ms.tgt_pltfrm: 
ms.custom: 53231
ms.assetid: 213e6e6d-50f4-4815-983d-43f717c13cba
ms.region: Global
ms.industry: Manufacturing
ms.author: mguada

---

# Adjust on-hand inventory cost values

Use the Adjustment of on-hand inventory page to adjust the cost value of the on-hand inventory quantities after an inventory close process is run.

You can use the **Adjustment of on-hand inventory** page to adjust the cost value of on-hand inventory quantities after an inventory close process is run. **Note:** To open the **Adjustment of on-hand inventory** page, on the **Closing and adjustment** page, select the record of a completed inventory close process, and then click **Adjustment** &gt; **On-hand**. **Example:** You have the following transactions in February:

-   February 1: An inventory financial receipt for a quantity of 2 at a cost of USD 10.00
-   February 5: An inventory financial receipt for a quantity of 1 at a cost of USD 13.00
-   February 19: An inventory financial issue for a quantity of 1 at a running average cost of USD 11.00

This item was set up with the first in, first out (FIFO) inventory model, and inventory close was performed as of February 28. The financial issue transaction of USD 11.00 will be settled against the financial receipt that is dated February 1, and an adjustment of USD 1.00 will be made. The following inventory receipts will then contain open inventory quantities:

-   February 1: A quantity of 1 at a cost of USD 10.00
-   February 5: A quantity of 1 at a cost of USD 13.00

To set the cost of these two items to USD 15.00, use the on-hand adjustment option to adjust the open on-hand quantities as of the last inventory close period. **Note:** The posting date of the on-hand adjustment transaction will be the date of the last inventory close. This date can't be modified.

