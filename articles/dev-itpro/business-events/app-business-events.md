---
# required metadata

title: Application business events
description: [Full description that appears in the search results. Often the first paragraph of your topic.]
author: Sunil-Garg
manager: AnnBe
ms.date: 01/03/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: IT Pro
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: Operations, Core
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global for most topics. Set Country/Region name for localizations
# ms.search.industry: 
ms.author: sunilg
ms.search.validFrom: Platform update 24
ms.dyn365.ops.version: 2019-02-28
---

# Application business events

[!include[banner](../includes/banner.md)]
[!include[banner](../includes/preview-banner.md)]

Procure to pay
--------------

| Business event                  | Description                                                                                                                                | Module           |
|---------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------|------------------|
| Vendor invoice matched          | This business event is triggered when invoice matching validation is completed for a vendor invoice as part of the Procure to Pay process. | Accounts Payable |
| Vendor invoice posted           | This business event is triggered when invoice matching validation is completed for a vendor invoice as part of the Procure to Pay process. | Accounts Payable |
| Vendor payment posted           | This business event is triggered when a user posts a vendor payment as part of the Procure to Pay process.                                 | Accounts Payable |
| Invoice register journal posted | This business event is triggered when a user posts an invoice register journal as part of the Procure to Pay process.                      | Accounts Payable |
| Invoice journal posted          | This business event is triggered when a user posts an invoice journal as part of the Procure to Pay process.                               | Accounts Payable |
| Invoice approval journal posted | This business event is triggered when a user posts an invoice approval journal as part of the Procure to Pay process.                      | Accounts Payable |

Quote to cash
-------------

| Business event                             | Description                                                                                                                       | Module                 |
|--------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------|------------------------|
| Invoice is created from a sales order      | This business event is triggered when a user posts a sales order invoice as part of the Quote to Cash process.                    | Accounts Receivable    |
| Free text invoice posted                   | This business event is triggered when a user posts a free text invoice as part of the Quote to Cash process.                      | Accounts Receivable    |
| Payment posted                             | This business event is triggered when a user posts a payment as part of the Quote to Cash process.                                | Accounts Receivable    |
| Transaction is written off                 | This business event is triggered when a user writes off a customer transaction as part of the Quote to Cash process.              | Accounts Receivable    |
| Collection status of a transaction changed | This business event is triggered when a user updates the collection status of a transaction as part of the Quote to Cash process. | Accounts Receivable    |
| Interest note posted                       | This business event is triggered when a user posts an interest note as part of the Quote to Cash process.                         | Accounts Receivable    |
| Collection letter created                  | This business event is triggered when a user creates a collection letter for a customer as part of the Quote to Cash process.     | Credit and collections |

