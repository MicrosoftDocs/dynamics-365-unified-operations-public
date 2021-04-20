---
title: Cumulating customer rebates using item rebate groups fails
description: Cumulating customer rebates using item rebate groups fails
author: sherry-zheng
ms.date: 4/11/2021
ms.topic: troubleshooting
ms.search.form: PdsRebateTableListPage
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: smnatara
ms.search.validFrom: 2021-04-11
ms.dyn365.ops.version: 10.0.19
---

# Cumulating customer rebates using item rebate groups fails

KB Number: 4611372

## Symptoms

When using customer rebate agreements (of type *amount*) in combination with item rebate groups, rebates are calculated but the cumulation fails.

## Resolution
<!-- KFM: It isn't clear how this description relates to the issue, which doesn't mention "threshold condition". More information is needed. -->
This is the expected behavior. Item groups only group items that have the same threshold condition.
