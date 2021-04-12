---
title: The warehouse in picking list journal is not linked with BOM line
description: The warehouse in picking list journal is not linked with BOM line
author: SmithaNataraj
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

# The warehouse in picking list journal is not linked with BOM line

KB Number: 4614848

The warehouse in picking list journal is not linked with BOM line


## Resolution
production BOM (parts) is a blueprint for a picking list line. If a picking list line is added retrospectively for non-existing material LOT new production BOM is created with the provided info (including dimensions). Now, if a picking line is updated (e.g. dimension is changed) related production BOM line is NOT updated. The rationality here is 1:N relationship between production BOM LOT and picking list line LOT. If that would be the case it would make production BOM blueprint error prone to invalid updates.


