---
title: Default descriptions for the general ledger
description: Learn how default descriptions can be used to update the Description field in voucher postings to the general ledger with a table defining description types.
author: lisascholz91
ms.author: lisascholz
ms.reviewer: kamaybac
ms.search.form: TransactionTexts
ms.topic: how-to
ms.date: 02/12/2025
ms.custom: 
  - bap-template
---

# Default descriptions for the general ledger

[!include [banner](../../includes/banner.md)]

Default descriptions can be used to update the **Description** field in voucher postings to the general ledger. This functionality has been enhanced to work with Landed cost.

To set up default descriptions for ledger postings, go to **Organizational administration \> Setup \> Default descriptions**.

The following table lists the new values that were added for the **Description** field on the **Default descriptions** page to support Landed cost.

| Description type | Notes |
|---|---|
| Import costing – Cost accrual | When a purchase order invoice is posted, a cost accrual is processed for estimate voyage costs. Default descriptions can be specified to add the voyage number to the description. Use *%4* for the shipment number. |
| Import costing – Goods in transit order | If you're using in-transit processing, the purchase order invoice is posted, and the goods are posted to a goods-in-transit account. Default descriptions can be specified to add the in-transit order number to the description. Use *%4* for the in-transit order number. |
| Inventory – close – adjustment | When the accounts payable (AP) invoice is processed for a voyage cost, an inventory adjustment is processed to estimate voyage costs. Default descriptions can be specified to add the voyage number to the description. Use *%4* for the shipment number. |

For more information about how to work with the **Default descriptions** page, see [Set up default descriptions for automatic posting](../../finance/general-ledger/set-up-default-descriptions-for-automatic-posting.md).
