---
title: Unable to update the forecasted unit cost when importing demand forecast records
description: When you use data entities to import demand forecast records, the cost price for existing records doesn't get updated to match the imported data
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

# Unable to update the forecasted unit cost when importing demand forecast records

KB Number: 4614109

## Symptoms

When you use data entities to import demand forecast records, the **Forecasted unit cost** for existing records doesn't get updated to match the imported data.

## Cause

**Forecasted unit cost** is a read-only field. Its value is set based on the product unit cost and can't be set directly through import.

## Resolution

The field is read only, so you can't import values for it. The value will be calculated according to the existing business logic.
