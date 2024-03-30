---
title: Managing dual-write integration keys
description: This article describes managing integration keys for dual-write
author: jaredha
ms.date: 03/29/2024
ms.topic: how-to
ms.collection:
  - bap-ai-copilot
audience: Developer
ms.reviewer: johnmichalak
ms.search.region: Global
ms.author: jaredha
ms.search.validFrom: 2020-03-20
ms.dyn365.ops.version: AX 7.0.0
---

# Managing dual-write integration keys

[!include [banner](../../includes/banner.md)]

Integration keys for dual-write are the natural key for an entity that uniquely identifies a row of a Dataverse table. The key is used to find the correct record in the Dataverse table on which to perform the dual-write operation that originated in finance and operations apps. For example, for a dual-write map that associates a finance and operations entity to the Global Product table in Dataverse, the integration key must be defined for the Global Product table to ensure the map processes correctly. An update or delete of the product record in finance and operations apps is then able to find the unique related record in the Global Product table to perform the operation.

> [!NOTE]
> Integration keys must only be defined for Dataverse tables. They are not required for finance and operations entities.

The integration key is based on an alternate key of the Dataverse table. A purpose of the alternate keys on the table is to faciliate simplified programming and integration with external systems. See [Define alternate keys to reference rows](https://learn.microsoft.com/power-apps/maker/data-platform/define-alternate-keys-reference-records) for more information on alternate keys in Dataverse.

> [!IMPORTANT]
> The alternate key used for the integration key should only include columns for which application users are not allowed to change the value. The integration key defines the relationship between the record in finance and operations apps and Dataverse. If a value in a column that is part of the alternate key changes for a record, it is essentially changing the identity of the record and breaks the relationship between the record in finance and operations apps and Dataverse. It's important that keys be matched between the finance and operations apps and Dataverse.
