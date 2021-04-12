---
title: Reverse report as finished with marking creates an open transaction with the quantity reversed having the same inventory dimensions of the transaction reversed
description: Reverse report as finished with marking creates an open transaction with the quantity reversed having the same inventory dimensions of the transaction reversed
author: SmithaNataraj
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

# Reverse report as finished with marking creates an open transaction with the quantity reversed having the same inventory dimensions of the transaction reversed

KB Number: 4612469

Reverse report as finished with marking createsan open transaction with the quantity reversed having the same inventorydimensions of the transaction reversed


## Resolution
This works as expected.

When reversing the report as finished, the inventory dimension is initialized from production journal, so it gets the batch number. The sales order transactions will inherit the batch number due to marking.

This is not a blocking issue. As the dimension can be reset when posting RAF.




