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

# The warehouse in the picking list journal is not updated on a BOM line

KB Number: 4614848

## Issue description

The warehouse in the picking list journal is not updated on a bill of material (BOM) line.

## Resolution

This is the expected behavior. If a picking list journal line is created with a reference to a production BOM line (via the Lot ID), then the warehouse on the production BOM line will not be updated if the warehouse dimension on the production picking list journal line is later changed.