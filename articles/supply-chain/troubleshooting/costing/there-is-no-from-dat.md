---
title: There is no From date filed in Active prices tab.
description: There is no From date filed in Active prices tab.
author: SmithaNataraj
ms.date: 4/11/2021
ms.topic: troubleshooting
ms.search.form: InventItemPrice
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: smnatara
ms.search.validFrom: 2021-04-11
ms.dyn365.ops.version: 10.0.19
---

# There is no From date filed in Active prices tab.

KB Number: 4613548

There is no From date filed in Active prices tab.


## Resolution
The "From date" set on Pending price won't be transfered to Active price.
Following is a public doc: https://docs.microsoft.com/en-us/dynamics365/supply-chain/cost-management/costing-versions, under Entering costs section:
When an item cost record is first entered, it has Pending status and an intended effective date. When you activate the item cost record, the status is updated to Active, and the effective date is updated to the activation date. 
So the Active price's activation date is always the actual date doing the activation.




