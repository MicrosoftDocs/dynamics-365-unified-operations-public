---
title: Unified number sequence for job IDs
description: This feature provides a single, unified number sequence that generates job IDs for the Production control, Manufacturing execution, and Time and attendance modules.
author: johanhoffmann
ms.date: 03/25/2021
ms.topic: article
# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: johanho
ms.search.validFrom: 2021-03-05
ms.dyn365.ops.version: 10.0.16
---

# Unified number sequence for job IDs

[!include [banner](../includes/banner.md)]

This feature provides a single, unified number sequence that generates job IDs for the Production control, Manufacturing execution, and Time and attendance modules. Previously, you were able to choose a different number sequence for each of these modules, which could result in conflicting job IDs if two or more of these sequences used an identical format. Such a conflict can cause data corruption.

## Turn on this feature for your system

If your system doesn't already include the feature described in this topic, go to [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) and turn on the *Unified number sequence for job IDs* feature.

## Set up the unified number sequence for job IDs

After enabling this feature, the existing **Job identification** number-sequence settings located on the parameters pages for the Production control, Manufacturing execution, and Time and attendance modules will be deprecated and a new **Unified job ID** field will be added. The **Unified job ID** value is shared by all three modules, thus ensuring that all modules reference the same number sequence. Job IDs will therefore be unique across all three modules and a conflict will never occur.

To set up the unified number sequence for job IDs:

1. Turn on the feature as described in the previous section.
1. Either identify the number sequence you want to use for your unified job IDs, or create a new one. For more information, see [Number sequences overview](../../fin-ops-core/fin-ops/organization-administration/number-sequence-overview.md).
1. Go to the **Production control parameters**, **Manufacturing execution parameters**, or **Time and attendance parameters** page. It doesn't matter which one you choose because when you make this setting on any of those pages, all of the other pages will update automatically.
1. Open the **Number sequences** tab on your selected parameters page.
1. Assign the **Number sequence code** that you identified previously to the **Unified job IDs** row of the grid.
