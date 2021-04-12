---
title: Indirect costs in process report includes deleted production orders
description: The indirect costs in process report presents information on production orders that were partially processed and later deleted.
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

# Indirect costs in process report includes deleted production orders

KB Number: 4612748

## Issue description

The *indirect costs in process* report presents information on production orders that were partially processed and later deleted.

## Resolution

<!-- KFM: Is this how we have agreed to communicate "by design" resolutions? -->

Microsoft has evaluated the reported issue and found that the system behaves as designed. When you reverse a production order, you also reverse all the transactions of the production order. The subledger tables and general ledger will persists all transactions related to the production order when you delete the production order it self. The transactions in the subledger tables will be shown in the reports. For the specific production order, the net value should be 0.00
