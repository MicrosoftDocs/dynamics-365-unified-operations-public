---
# required metadata

title: There is no From date filed in Active prices tab.
description: There is no From date filed in Active prices tab.
author: SmithaNataraj
manager: tfehr
ms.date: 4/11/2021 12:00:00 AM
ms.topic: troubleshooting
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: InventItemPrice
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
submittedBy: smnatara@microsoft.com

---

# There is no From date filed in Active prices tab.

KB Number: 4613548

There is no From date filed in Active prices tab.


## Resolution
The "From date" set on Pending price won't be transfered to Active price.
Following is a public doc: https://docs.microsoft.com/en-us/dynamics365/supply-chain/cost-management/costing-versions, under Entering costs section:
When an item cost record is first entered, it has Pending status and an intended effective date. When you activate the item cost record, the status is updated to Active, and the effective date is updated to the activation date. 
So the Active price's activation date is always the actual date doing the activation.




