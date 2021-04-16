---
title: Master planning batch job filter is not working as expected
description: Master planning batch job filter is not working as expected
author: ChristianRytt
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

## Issue description

<!-- KFM: This issue description is not clear. Please revise in a way that addresses the general reader rather than referring to particular customer case. -->

Customer is unable to run the master planning as per the provided filter. The filter is not working when the batch job is created as well.

## Resolution

This is the expected behavior. The batch job filter is only able to filter items to include in the planning. After that, the system runs planning for all the coverage groups those filtered items have. Any coverage groups that are included in the items filter won't affect the planning output after a given item is already included in the run.
