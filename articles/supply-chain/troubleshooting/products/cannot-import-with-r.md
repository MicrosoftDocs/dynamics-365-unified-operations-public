---
title: You can't import an item by using the Released products V2 entity
description: You can't import an item by using the Released products V2 entity.
author: t-benebo
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
# You can't import an item by using the Released products V2 entity

KB number: 4611825

## Symptoms

When you try to import an item by using the *Released products V2* entity, you receive an error message that resembles the following example:

> Cannot create a record in Items - tracking dimension groups (EcoResTrackingDimensionGroupItem). Item number: 2040663, Batch. The record already exists.

## Resolution

To import new released products, you must use the *Released product creation V2* entity instead of the *Released products V2* entity.
