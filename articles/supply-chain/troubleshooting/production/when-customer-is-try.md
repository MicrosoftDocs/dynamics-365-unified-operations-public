---
title: When customer is trying to select the LOTID field the Batch number which is already entered is vanishing.
description: When customer is trying to select the LOTID field the Batch number which is already entered is vanishing.
author: SmithaNataraj
ms.date: 4/11/2021
ms.topic: troubleshooting
ms.search.form: ProdJournalTransBOM
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: datra
ms.search.validFrom: 2021-04-11
ms.dyn365.ops.version: 10.0.19
---

# When customer is trying to select the LOTID field the Batch number which is already entered is vanishing.

KB Number: 4613107

When customer is trying to select the LOTID field the Batch number which is already entered is vanishing.


## Resolution
This is working as expected. When changing LOT, the whole item context is changed and thus, the batch number is reset.

If the batch number wants to be associated with the LOT, then user has to set the LOT first.


