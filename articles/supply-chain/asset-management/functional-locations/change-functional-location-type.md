---
title: Change the type of existing functional locations
description: Learn how to change the functional location type of an existing functional location, including prerequisites and a step-by-step process.
author: jodahlMSFT
ms.author: jodahl
ms.topic: how-to
ms.date: 10/27/2023
ms.custom: bap-template
ms.reviewer: kamaybac
ms.search.form:
---

# Change the type of existing functional locations

[!include [banner](../../includes/banner.md)]

This article explains how to change the [functional location type](../setup-for-functional-locations/functional-location-types.md) of an existing functional location.

## Prerequisites

Before you can use this feature, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management 10.0.38 or later.
- The feature that's named *Change types on assets and functional locations* must be turned on in [Feature management](../../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md). As of Supply Chain Management version 10.0.43, this feature is turned on by default.

## Change the functional location type of one or more existing functional locations

To change the functional location type of one or more existing functional locations, follow these steps.

1. Go to **Asset management** \> **Functional locations** \> **All functional locations**.
1. On the **All functional locations** list page, select one or more functional locations that you want to change the type for. If you select multiple functional locations, all of them must be of the same type.
1. On the Action Pane, on the **Functional locations** tab, in the **Maintain** group, select **Change functional location type**.
1. In the **Change functional location type** dialog box, on the **Parameters** FastTab, set the following fields:

    - **New functional location type** – Select the new type to assign to the selected functional locations.
    - **Attributes** – Set this option to *Yes* to append the attribute types that are associated with the new functional location type to the selected functional locations.
    - **Asset attribute requirements** – Set this option to *Yes* to append the asset attribute requirements that are associated with the new functional location type to the selected functional locations.
    - **Maintenance plans** – Set this option to *Yes* to append the maintenance plans that are associated with the new functional location type to the selected functional locations.

1. On the **Run in background** FastTab, set the **Batch processing** option to *Yes* to run the process of changing functional location types as a batch job.
1. Select **OK** to apply your settings.

> [!NOTE]
> Each functional location type has settings that define which supporting data applies to functional locations of that type. This supporting data includes information such as asset types, maintenance plans, and asset attribute requirements. When you change the functional location type, the supporting data for existing functional locations might not match the supporting data for the new functional location type.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
