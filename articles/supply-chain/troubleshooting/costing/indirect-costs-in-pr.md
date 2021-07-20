---
title: The Indirect costs in process report includes deleted production orders
description: The Indirect costs in process report presents information about production orders that were partially processed and later deleted.
author: niwang
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

# The Indirect costs in process report includes deleted production orders

KB number: 4612748

## Symptoms

The **Indirect costs in process** report presents information about production orders that were partially processed and later deleted.

## Resolution

When you reverse a production order, you also reverse all the transactions of that production order. When you delete the production order, the subledger tables and general ledger persist all transactions that are related to it. The reports will show the transactions in the subledger tables. For the specific production order, the net value should be 0.00.
