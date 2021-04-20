---
title: Batch number is cleared on selecting a new lot ID
description: When reviewing a picking list journal line, the specified batch number is cleared when you select a new value for the lot ID.
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

# Batch number is cleared on selecting a new lot ID

KB Number: 4613107

## Symptoms

When reviewing a picking list journal line, the specified **Batch number** is cleared when you select a new value for the **Lot ID**.

## Resolution

This is the expected behavior.  Changing the **Lot ID** changes the item context, and therefore the batch number is reset.

If you want to associate the batch number with a lot ID, you must set the lot ID first.
