---
title: Inconsistency in backflushing WMS-enabled raw materials
description: When backflushing raw materials, the system behaves differently for materials enabled for advanced warehouse management (WMS) when compared to materials not enabled for WMS.
author: SmithaNataraj
ms.date: 4/11/2021
ms.topic: troubleshooting
ms.search.form: ProdTableListPage
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: johanho
ms.search.validFrom: 2021-04-11
ms.dyn365.ops.version: 10.0.19
---
<!-- KFM: This topic isn't clear. Please revise. I made an attempt to edit, please also review for accuracy. -->
# Inconsistency in backflushing WMS-enabled raw materials

KB Number: 4612640

## Issue description
<!-- KFM: In what ways does it behave differently? -->
When backflushing raw materials, the system behaves differently for materials enabled for advanced warehouse management (WMS) when compared to materials not enabled for WMS.

## Resolution

This is the expected behavior. It is possible to backflush unreserved raw materials that are WMS enabled. This is not possible for raw materials that are not enabled for WMS.

<!-- KFM: The following paragraph is not clear. Please revise. -->
We need to run this batch "Automatic release of BOM and formula lines" to update the inventory transaction for formula line with location.
