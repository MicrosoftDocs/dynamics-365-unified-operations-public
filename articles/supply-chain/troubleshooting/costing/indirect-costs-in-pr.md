---
title: Indirect Costs in Process report presents information on Production Orders that were partially processed and later deleted.
description: Indirect Costs in Process report presents information on Production Orders that were partially processed and later deleted.
author: SmithaNataraj
ms.date: 4/11/2021
ms.topic: troubleshooting
ms.search.form: ProdIndirectCostInProgress
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: smnatara
ms.search.validFrom: 2021-04-11
ms.dyn365.ops.version: 10.0.19
---

# Indirect Costs in Process report presents information on Production Orders that were partially processed and later deleted.

KB Number: 4612748

Indirect Costs in Process report presents information onProduction Orders that were partially processed and later deleted.


## Resolution
Microsoft has evaluated the reported issue and found that the system behaved as designed. When you reverse a Production order you also reverse all the transactions of the Production order. The Sub-ledger tables and General ledger will persists all transactions related to the Production order when you delete the Production order it self. The transactions in the sub-ledger tables will be shown in the reports. For the specific Production order the net value should be 0.00


