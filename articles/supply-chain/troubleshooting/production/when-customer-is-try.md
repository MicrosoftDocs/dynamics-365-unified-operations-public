---
title: Batch number is cleared when a new lot ID is selected
description: When you're reviewing a picking list journal line, the value in the Batch number field is cleared if you select a new value in the Lot ID field.
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

# Batch number is cleared when a new lot ID is selected

KB number: 4613107

## Symptoms

When you're reviewing a picking list journal line, the value in the **Batch number** field is cleared if you select a new value in the **Lot ID** field.

## Resolution

The system is behaving as designed. If you change the lot ID, you change the item context. Therefore, the batch number is reset.

To associate the batch number with a lot ID, you must set the lot ID first.
