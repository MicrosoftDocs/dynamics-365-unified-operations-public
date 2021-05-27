---
title: Cumulation of customer rebates fails when item rebate groups are used
description: When you use customer rebate agreements in combination with item rebate groups, rebates are calculated, but cumulation fails.
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

# Cumulation of customer rebates fails when item rebate groups are used

KB number: 4611372

## Symptoms

When you use customer rebate agreements (of the *amount* type) in combination with item rebate groups, rebates are calculated, but cumulation fails.

## Resolution

The system is behaving as designed. Item groups group only items that have the same threshold condition. The rebate condition (threshold) is set against the amount for each item, not against the cumulated amount for any item in the item group.
