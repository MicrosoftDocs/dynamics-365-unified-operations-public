---
title: When importing to the Item coverage V2 entity in certain scenarios when accessing the Item coverage form after import/update, you will receive the error: "Do you want to save your changes before closing?", even though the user made no changes.
description: When importing to the Item coverage V2 entity in certain scenarios when accessing the Item coverage form after import/update, you will receive the error: "Do you want to save your changes before closing?", even though the user made no changes.
author: SmithaNataraj
ms.date: 4/11/2021
ms.topic: troubleshooting
ms.search.form: DataManagementWorkspace_
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: angarmas
ms.search.validFrom: 2021-04-11
ms.dyn365.ops.version: 10.0.19
---

# When importing to the Item coverage V2 entity in certain scenarios when accessing the Item coverage form after import/update, you will receive the error: "Do you want to save your changes before closing?", even though the user made no changes.

## Issue description

When importing to the Item coverage V2 entity in certain scenarios when accessing the Item coverage form after import/update, you will receive the error: "Do you want to save your changes before closing?", even though the user made no changes.

## Resolution

Coverage form has a complex defaulting logic that might lead to the observed message in case there were direct modifications in the database or entity imports before.

To change PRODUCTCOVERAGEGROUPID through the entity a user needs to set AREGENERALSETTINGSOVERRIDDEN to Yes
