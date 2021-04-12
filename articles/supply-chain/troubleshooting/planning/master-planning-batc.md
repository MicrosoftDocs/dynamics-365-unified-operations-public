---
title: Master planning batch job filter is not working as expected
description: Master planning batch job filter is not working as expected
author: SmithaNataraj
ms.date: 4/11/2021
ms.topic: troubleshooting
ms.search.form: ReqTransPo
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: ilebedev
ms.search.validFrom: 2021-04-11
ms.dyn365.ops.version: 10.0.19
---

# Master planning batch job filter is not working as expected

KB Number: 4612572

Customer is unable torun the master planning as per the provided filter. The filter is not workingwhen the batch job is created as well


## Resolution
The observed behavior is by design as batch job filter is used solely to filter items to include in the planning, after that we run planning for all the coverage groups those filtered items have. Including a particular coverage group in items filter does not affect the planning output once the item actually included in the run.


