---
title: Reversing a report as finished creates an unexpected open transaction
description: Reverse report as finished with marking creates an open transaction with the quantity reversed having the same inventory dimensions of the transaction reversed.
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
<!-- KFM: this topic is unclear. Please revise or remove. -->
# Reversing a report as finished creates an unexpected open transaction

KB Number: 4612469

## Symptoms

Reverse report as finished with marking creates an open transaction with the quantity reversed having the same inventory dimensions of the transaction reversed.

## Resolution

This is the expected behavior. When you reverse a report-as-finished operation, the inventory dimension is initialized from the production journal, so it gets the batch number. The sales order transactions will inherit the batch number due to marking.

The dimension can be reset when posting report as finished.
