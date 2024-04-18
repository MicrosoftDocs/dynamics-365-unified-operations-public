---
title: Application business events
description: Learn about application business events, including a table that outlines Procure to pay business events and their respective modules.
author: Sunil-Garg
ms.author: sunilg
ms.topic: article
ms.date: 09/23/2019
ms.custom: 
ms.reviewer: johnmichalak
audience: IT Pro
ms.search.region: Global
ms.search.validFrom: Platform update 24
# ms.search.form:  [Operations AOT form name to tie this article to]
ms.dyn365.ops.version: 2019-02-28
---

# Application business events

[!include[banner](../includes/banner.md)]

This article lists application business events.

## Procure to pay

| Business event | Description | Module |
|----|----|----|
| Vendor invoice matched          | This event is triggered when invoice matching validation is completed for a vendor invoice as part of the Procure to pay process. | Accounts payable |
| Vendor invoice posted           | This event business event is triggered when a user posts a vendor invoice as part of the Procure to Pay process. | Accounts payable |
| Vendor payment posted           | This event is triggered when a user posts a vendor payment as part of the Procure to pay process.                                 | Accounts payable |
| Invoice register journal posted | This event is triggered when a user posts an invoice register journal as part of the Procure to pay process.                      | Accounts payable |
| Invoice journal posted          | This event is triggered when a user posts an invoice journal as part of the Procure to pay process.                               | Accounts payable |
| Invoice approval journal posted | This event is triggered when a user posts an invoice approval journal as part of the Procure to pay process.                      | Accounts payable |
|Purchase order confirmed |This event is triggered when a purchase order is confirmed by a vendor. One of the following actions triggers the event: the user manually confirms a purchase order in the user interface for purchase orders, when the purchase order confirmation is executed in a batch, or when the confirmation is executed programmatically in intercompany scenarios. In scenarios where vendor collaboration is used, and the vendor collaboration policy is set to autoconfirm a purchase order, the trigger occurs when the **Accept** button is clicked on the **Purchase order confirmation**  page in the **Vendor collaboration** portal.|Procurement and sourcing|
|Purchase order received |This event is triggered when goods or services are registered as received against one or more purchase orders. One of the following actions triggers the event: a product receipt is generated for one or more purchase orders manually in the user interface for purchase orders and product receipts, when product receipts are generated in a batch, or when product receipts are generated programmatically in intercompany scenarios.|Procurement and sourcing|

## Quote to cash

| Business event                             | Description                                                                                                                       | Module                 |
|--------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------|------------------------|
| Invoice is created from a sales order      | This event is triggered when a user posts a sales order invoice as part of the Quote to Cash process.                    | Accounts receivable    |
| Free text invoice posted                   | This event is triggered when a user posts a free text invoice as part of the Quote to Cash process.                      | Accounts receivable    |
| Payment posted                             | This event is triggered when a user posts a payment as part of the Quote to Cash process.                                | Accounts receivable    |
| Transaction is written off                 | This event is triggered when a user writes off a customer transaction as part of the Quote to Cash process.              | Accounts receivable    |
| Collection status of a transaction changed | This event is triggered when a user updates the collection status of a transaction as part of the Quote to Cash process. | Accounts receivable    |
| Interest note posted                       | This event is triggered when a user posts an interest note as part of the Quote to Cash process.                         | Accounts receivable    |
| Collection letter created                  | This event is triggered when a user creates a collection letter for a customer as part of the Quote to Cash process.     | Credit and collections |


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]