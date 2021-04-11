---
# required metadata

title: Indirect Costs in Process report presents information on Production Orders that were partially processed and later deleted.
description: Indirect Costs in Process report presents information on Production Orders that were partially processed and later deleted.
author: SmithaNataraj
manager: tfehr
ms.date: 4/11/2021 12:00:00 AM
ms.topic: troubleshooting
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: ProdIndirectCostInProgress
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

# Indirect Costs in Process report presents information on Production Orders that were partially processed and later deleted.

KB Number: 4612748

Indirect Costs in Process report presents information onProduction Orders that were partially processed and later deleted.


## Resolution
Microsoft has evaluated the reported issue and found that the system behaved as designed. When you reverse a Production order you also reverse all the transactions of the Production order. The Sub-ledger tables and General ledger will persists all transactions related to the Production order when you delete the Production order it self. The transactions in the sub-ledger tables will be shown in the reports. For the specific Production order the net value should be 0.00


