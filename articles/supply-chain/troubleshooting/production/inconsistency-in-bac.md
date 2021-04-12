---
title: Inconsistency in backflushing of warehouse managed raw material when formula item is warehouse managed vs when formula item is not warehouse managed.
description: Inconsistency in backflushing of warehouse managed raw material when formula item is warehouse managed vs when formula item is not warehouse managed.
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

# Inconsistency in backflushing of warehouse managed raw material when formula item is warehouse managed vs when formula item is not warehouse managed.

KB Number: 4612640

## Issue description

Inconsistency in backflushing of warehouse managed raw material when formula item is warehouse managed vs when formula item is not warehouse managed.

## Resolution

The Microsoft core team has investigated this case and with a by-design resolution. In the current design it is possible to backflush raw materials enabled for the advanced warehouse processes in an un-reserved state. This is not possible for raw materials that are not enabled for the advanced warehouse processes.
We need to run this batch "Automatic release of BOM and formula lines" to update the inventory transaction for formula line with location.
