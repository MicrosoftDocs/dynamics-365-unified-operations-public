---
title: Cannot import with Released products V2 entity
description: Cannot import with Released products V2 entity
author: SmithaNataraj
ms.date: 4/11/2021
ms.topic: troubleshooting
ms.search.form: EcoResProductDetailsExtended, DataManagementWorkspace
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: myvakalo
ms.search.validFrom: 2021-04-11
ms.dyn365.ops.version: 10.0.19
---

# Cannot import with Released products V2 entity

KB Number: 4611825

## Issue description

When trying to import an item using the Released Products V2 entity, it is giving error message: Cannot create a record in Items - tracking dimension groups (EcoResTrackingDimensionGroupItem). Item number: 2040663, Batch. The record already exists.

## Resolution

In order to import new released products, the released product creation V2 entity must be used. The released products V2 entity must not be used.  
