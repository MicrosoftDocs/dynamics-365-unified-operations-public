---
# required metadata

title: Adjust on-hand inventory cost values
description: Use the Adjustment of on-hand inventory page to adjust the cost value of the on-hand inventory quantities after an inventory close process is run.
author: JennySong-SH
ms.date: 06/20/2017
ms.topic: article
ms.prod:
ms.technology:

# optional metadata

ms.search.form: InventAdjInventOnHand
# ROBOTS:
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm:
ms.assetid: bc1fde9f-5ad9-4339-8ae8-e2839b792eb2
ms.search.region: Global
ms.search.industry: Manufacturing
ms.author: yanansong
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Adjust on-hand inventory cost values

[!include [banner](../includes/banner.md)]

Use the Adjustment of on-hand inventory page to adjust the cost value of the on-hand inventory quantities after an inventory close process is run.

You can use the **Adjustment of on-hand inventory** page to adjust the cost value of on-hand inventory quantities after an inventory close process is run. **Note:** To open the **Adjustment of on-hand inventory** page, on the **Closing and adjustment** page, select the record of a completed inventory close process, and then click **Adjustment** &gt; **On-hand**. **Example:** You have the following transactions in February:

-   February 1: An inventory financial receipt for a quantity of 2 at a cost of USD 10.00
-   February 5: An inventory financial receipt for a quantity of 1 at a cost of USD 13.00
-   February 19: An inventory financial issue for a quantity of 1 at a running average cost of USD 11.00

This item was set up with the first in, first out (FIFO) inventory model, and inventory close was performed as of February 28. The financial issue transaction of USD 11.00 will be settled against the financial receipt that is dated February 1, and an adjustment of USD 1.00 will be made. The following inventory receipts will then contain open inventory quantities:

-   February 1: A quantity of 1 at a cost of USD 10.00
-   February 5: A quantity of 1 at a cost of USD 13.00

To set the cost of these two items to USD 15.00, use the on-hand adjustment option to adjust the open on-hand quantities as of the last inventory close period. **Note:** The posting date of the on-hand adjustment transaction will be the date of the last inventory close. This date can't be modified.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]