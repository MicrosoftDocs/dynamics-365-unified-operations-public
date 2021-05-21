---
title: The warehouse in the picking list journal isn't updated on a BOM line.
description: The warehouse in the picking list journal isn't updated on a bill of materials (BOM) line.
author: johanhoffmann
ms.date: 4/11/2021
ms.topic: troubleshooting
ms.search.form: ProdJournalTransBOM
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: smnatara
ms.search.validFrom: 2021-04-11
ms.dyn365.ops.version: 10.0.19
---

# The warehouse in the picking list journal isn't updated on a BOM line

KB number: 4614848

## Symptoms

The warehouse in the picking list journal isn't updated on a bill of materials (BOM) line.

## Resolution

The system is behaving as designed. If a picking list journal line is created that has a reference (via the lot ID) to a production BOM line, the warehouse on the production BOM line won't be updated if the warehouse dimension on the production picking list journal line is changed later.
