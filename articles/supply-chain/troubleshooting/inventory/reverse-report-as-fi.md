---
title: Reversal of reporting as finished creates an unexpected open transaction
description: Reversal of reporting as finished that has marking creates an open transaction where the reversed quantity has the same inventory dimensions as the reversed transaction.
author: niwang
ms.date: 4/11/2021
ms.topic: troubleshooting
ms.search.form: ProdTable
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: smnatara
ms.search.validFrom: 2021-04-11
ms.dyn365.ops.version: 10.0.19
---

# Reversal of reporting as finished creates an unexpected open transaction

KB number: 4612469

## Symptoms

If you reverse reporting as finished that has marking, the system creates an open transaction where the reversed quantity has the same inventory dimensions as the transaction that was reversed.

## Resolution

When you reverse a report-as-finished operation, the inventory dimension is initialized from the production journal. Therefore, it gets the batch number. Because of marking, the sales order transactions will inherit the batch number.

The dimension can be reset when the reporting as finished is posted.
