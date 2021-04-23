---
title: The "Last tested date" field isn't updated when creating multiple quality orders
description: The field ‘last tested date’ is not updated when multiple quality order is created. 
author: niwang
ms.date: 4/11/2021
ms.topic: troubleshooting
ms.search.form: InventBatch
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: smnatara
ms.search.validFrom: 2021-04-11
ms.dyn365.ops.version: 10.0.19
---

# The "Last tested date" field isn't updated when creating multiple quality orders

KB Number: 4612803

## Symptoms

The "Last tested date" field isn't updated when creating multiple quality orders.

## Resolution

The system is behaving as designed. The last tested date isn't related to quality order. it stores the date when the finished goods are first purchased or manufactured. This date is be used to calculate the shelf life advice day.
