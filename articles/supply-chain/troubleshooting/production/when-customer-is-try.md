---
title: Batch number vanishes when selecting the LOTID field
description: Batch number vanishes when selecting the LOTID field
author: johanhoffmann
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
<!-- KFM: The context of this topic is not clear. Much more detail is needed, please rewrite. What is "LOT"? -->

# Batch number vanishes when selecting the LOTID field

KB Number: 4613107

## Issue description

When you select the LOTID field the Batch number which is already entered is vanishing.

## Resolution

This is the expected behavior.  When changing LOT, the whole item context is changed and thus, the batch number is reset.

If the batch number wants to be associated with the LOT, then user has to set the LOT first.
