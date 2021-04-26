---
title: Rebate condition for the item rebate group will only check each item's eligibility not the cumulative eligibility
description: When set up a rebate, using the item rebate group is to group all the items that the rebate condition needs to check for the eligibility. But the rebate condition is set against each of the item amount, NOT the cumulated amount for any items in the item group. 
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
The system is behaving as designed. Item groups only group items that have the same threshold condition.The rebate condition (threshold) is set against each of the item amount, Not the cumulcated amount for any item in the item group. 
