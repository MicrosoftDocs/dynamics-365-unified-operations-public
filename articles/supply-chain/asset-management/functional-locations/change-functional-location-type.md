---
title: Change the type of an existing functional location
description: This article explains how to change the functional location type of an existing functional location.
author: johanhoffmann
ms.author: johanho
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 10/27/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Change the type of an existing functional location

[!include [banner](../../includes/banner.md)]
[!INCLUDE [preview-banner](../../includes/preview-banner.md)]

<!-- KFM: Preview until further notice -->

This article explains how to change the [functional location type](../setup-for-functional-locations/functional-location-types.md) of an existing functional location.

## Prerequisites

To use this feature, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management 10.0.38 or later.
- The feature that is named *(Preview) Change types on assets and functional locations* must be turned on in [feature management](../../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

## Change the functional location type of an existing functional location

To change the functional location type of an existing functional location, follow these steps:

1. Go to **Asset management** \> **Functional locations** \> **All functional locations**.
1. On the **All functional locations** list page, select one or more functional locations for which you want to change the type. If you select multiple functional locations, then all of them must be of the same type.
1. On the Action Pane, open the **Functional locations** tab and, from the **Maintain** field group, select **Change functional location type**.
1. The **Change functional location type** dialog opens. Expand the **Parameters** FastTab and make the following settings:
    - **New functional location type** - Select the new type to assign to the selected functional location.
    - **Attributes** - Set to *Yes* to append the attribute types associated with the new functional location type to the selected functional locations.
    - **Asset attribute requirements** - Set to *Yes* to append the asset attribute requirements associated with the new functional location type to the selected functional locations.
    - **Maintenance plans** - Set to *Yes* to append the maintenance plans associated with the new functional location type to the selected functional locations.
1. Expand the **Run in background** FastTab and set **Batch processing** to *Yes* to run the process of changing functional location types as a batch job.
1. Select **OK** in the **Change functional location type** dialog to apply your settings.

> [!NOTE]
> Each functional location type has settings that define which supporting data applies for functional locations of that type. This includes information such as asset types, maintenance plans, and asset attribute requirements. When you change the functional location type, the supporting data for existing functional locations might not match the supporting data for the new functional location type.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]