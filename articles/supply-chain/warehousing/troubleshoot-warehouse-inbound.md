---
# required metadata

title: Troubleshoot inbound warehouse operations
description: XXXX
author: perlynne
manager: tfehr
ms.date: 10/19/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application user
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: perlynne
ms.search.validFrom: 2020-10-19
ms.dyn365.ops.version: 10.0.15
---

# Troubleshoot inbound warehouse operations

[!include [banner](../includes/banner.md)]

This topic describes how to fix common issues that you might encounter while working with inbound warehouse operations in Dynamics 365 Supply Chain Management.

## Quality order XXXX has been generated. Cluster profile could not be found please check your configuration.
<!-- KFM: Is this an error message? If so, it should be labelled as such and put in quotes. -->
**Issue:** Related to a receiving process where QM or QMS is enabled. Additional detail about the transaction could further enhance the fix.
<!-- KFM: Spell out "QM" and "QMS". Second sentence isn't clear. Issue should be better explained better. -->
**Fix:** Check the cluster profile setup. You can't use a cluster picking mobile device menu item without the cluster profiles.
<!-- KFM: So, what should I do? Create a profile? -->

## Mixed license plate receiving doesn't work for disposition codes other than credit.

**Issue:** You can only use the mixed license plate receiving menu item when the disposition code is *Credit*.

**Remarks:** Microsoft has evaluated this issue and determined it to be a feature limitation. The Disposition codes with Action Credit and Scrap are only supported at this time. <!-- KFM: I don't understand the last sentence. Please also check capitalization and set field labels in bold. -->

## Update product receipts periodic task. 
<!-- KFM: Section title should be phrased as an issue/problem -->

**Issue:** After running the periodic task "Update product receipts", the system automatically confirms unconfirmed purchase orders with a status of inventory transaction *Registered*.

**Fix:** Use the new inbound load handling feature. You must use [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) to enable this feature. First enable the *Associate purchase order inventory transactions with load* feature, then enable *Over receipt of load quantities*. For more information, see [Post registered product quantities against purchase orders](inbound-load-handling.md#post-registered-quantities)
