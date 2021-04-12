---
# required metadata

title: The warehouse in picking list journal is not linked with BOM line
description: The warehouse in picking list journal is not linked with BOM line
author: SmithaNataraj
manager: tfehr
ms.date: 4/11/2021 12:00:00 AM
ms.topic: troubleshooting
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: ProdJournalTransBOM
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
submittedBy: smnatara@microsoft.com

---

# The warehouse in picking list journal is not linked with BOM line

KB Number: 4614848

The warehouse in picking list journal is not linked with BOM line


## Resolution
production BOM (parts) is a blueprint for a picking list line. If a picking list line is added retrospectively for non-existing material LOT new production BOM is created with the provided info (including dimensions). Now, if a picking line is updated (e.g. dimension is changed) related production BOM line is NOT updated. The rationality here is 1:N relationship between production BOM LOT and picking list line LOT. If that would be the case it would make production BOM blueprint error prone to invalid updates.


