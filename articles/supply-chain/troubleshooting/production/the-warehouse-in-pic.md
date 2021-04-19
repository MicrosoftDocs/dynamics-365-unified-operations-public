---
title: The warehouse in the picking list journal is not linked to a BOM line
description: The warehouse in the picking list journal is not linked to a BOM line
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
<!--KFM: Johan will revisit this topic before publishing. -->
# The warehouse in the picking list journal is not updated on a BOM line

KB Number: 4614848

## Issue description

The warehouse in the picking list journal is not updated on a bill of material (BOM) line.

## Resolution

This is the expected behavior. If a picking list line is added to a production picking list journal, and references an existing production BOM line (via lot ID), a new production BOM line *is not* created with the provided info. If the picking list journal line is then updated (for example, by changing the warehouse), the related production BOM line *is not* updated.
