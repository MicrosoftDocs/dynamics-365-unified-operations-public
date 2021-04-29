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

## Symptoms

Customer is unable to run the master planning as per the filter defined for specific item coverage settings. The filter is not working as expected by the customer, when master planning processing is scheduled in a batch.

## Resolution

The batch job filter is only able to filter on items. Item coverage settings can be joined to the query as well, however, doing so will limit the query by items only, and not by specific item coverage settings (like **Vendor** and/or **Coverage group**). After that, the system runs planning for all the coverage groups and variations those filtered items have. Any coverage groups that are included in the items filter won't affect the planning output after a given item is already included in the run.
