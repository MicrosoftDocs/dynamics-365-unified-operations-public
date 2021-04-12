---
title: Cumulating customer rebates using item rebate groups fails
description: Cumulating customer rebates using item rebate groups fails
author: SmithaNataraj
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

When usingcustomer rebate agreements (type amount) in combination with item rebate groups,rebates are calculated but the cumulation of these calculated rebates fail



## Resolution
This is by design as the item group only group the items that have the same threshold condition.


