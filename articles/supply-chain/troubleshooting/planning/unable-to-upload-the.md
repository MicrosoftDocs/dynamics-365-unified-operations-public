---
title: Unable to upload the cost price in demand forecast entries
description: You are unable to upload the cost price in demand forecast entries through data management entities
author: ChristianRytt
ms.date: 4/11/2021
ms.topic: troubleshooting
ms.search.form: DataManagementWorkspace
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: angarmas
ms.search.validFrom: 2021-04-11
ms.dyn365.ops.version: 10.0.19
---

# Unable to upload the cost price in demand forecast entries

KB Number: 4614109

## Issue description
<!-- KFM: Do you mean "demand forecast entries" or "demand forecast entities". Both terms appear in this topic. Do you mean "upload" or "update"? -->
You are unable to upload the cost price in demand forecast entries through data management entities.

## Resolution

This is the expected behavior. We do not currently support updating the forecasted unit cost on the demand forecast entity. The field is read-only on this entity.
