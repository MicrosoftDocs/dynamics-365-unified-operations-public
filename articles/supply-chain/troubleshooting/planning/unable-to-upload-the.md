---
title: You can't update the forecasted unit cost when you import demand forecast records
description: When you use data entities to import demand forecast records, the cost price for existing records isn't updated so that it matches the imported data.
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

# You can't update the forecasted unit cost when you import demand forecast records

KB number: 4614109

## Symptoms

When you use data entities to import demand forecast records, the **Forecasted unit cost** value for existing records isn't updated so that it matches the imported data.

## Cause

**Forecasted unit cost** is a read-only field. The value is based on the product unit cost and can't be set directly through import.

## Resolution

Because the field is read only, you can't import values for it. The value will be calculated according to the existing business logic.
