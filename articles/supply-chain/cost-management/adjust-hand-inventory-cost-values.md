---
title: Adjust on-hand inventory cost values
description: Use the Adjustment of on-hand inventory page to adjust the cost value of the on-hand inventory quantities after an inventory close process is run.
author: prasungoel
ms.author: prasungoel
ms.reviewer: kamaybac
ms.search.form: InventAdjInventOnHand
ms.topic: how-to
ms.date: 12/02/2024
ms.custom: 
  - bap-template
---

# Adjust on-hand inventory cost values

[!include [banner](../includes/banner.md)]

Use the **Adjustment of on-hand inventory** page to adjust the cost value of the on-hand inventory quantities after running an inventory close process. To open the **Adjustment of on-hand inventory** page, start on the **Closing and adjustment** page, select the record of a completed inventory close process, and then select **Adjustment** \> **On-hand**.

For example, suppose you have the following transactions in February:

- February 1: An inventory financial receipt for a quantity of 2 at a cost of USD 10.00
- February 5: An inventory financial receipt for a quantity of 1 at a cost of USD 13.00
- February 19: An inventory financial issue for a quantity of 1 at a running average cost of USD 11.00

This item was set up with the first in, first out (FIFO) inventory model, and inventory close was performed as of February 28. The financial issue transaction of USD 11.00 will be settled against the financial receipt that is dated February 1, and an adjustment of USD 1.00 will be made. The following inventory receipts will then contain open inventory quantities:

- February 1: A quantity of 1 at a cost of USD 10.00
- February 5: A quantity of 1 at a cost of USD 13.00

To set the cost of these two items to USD 15.00, use the on-hand adjustment option to adjust the open on-hand quantities as of the last inventory close period.

> [!NOTE]
> The posting date of the on-hand adjustment transaction will be the date of the last inventory close. This date can't be modified.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
