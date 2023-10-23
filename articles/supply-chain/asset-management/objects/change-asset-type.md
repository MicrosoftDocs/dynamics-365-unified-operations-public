---
title: Change the asset type of an existing asset
description: This article explains how to change the asset type of an existing asset.
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

# Change the asset type of an existing asset

[!include [banner](../../includes/banner.md)]
[!INCLUDE [preview-banner](../../includes/preview-banner.md)]

<!-- KFM: Preview until further notice -->

This article explains how to change the [asset type](../setup-for-objects/object-types.md) of an existing asset.

## Prerequisites

To use this feature, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management 10.0.38 or later.
- The feature that is named *(Preview) Change types on assets and functional locations* must be turned on in [feature management](../../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

## Change the asset type of an asset

To change the asset type of an existing asset, follow these steps:

1. Go to **Asset management** \> **Assets** \> **All assets**.
1. On the **All assets** list page, select one or more assets for which you want to change asset type. If you select multiple assets, then all of them must be of the same asset type.
1. On the Action Pane, open the **Asset** tab and, from the **Maintain** field group, select **Change asset type**.
1. The **Change asset type** dialog opens. Expand the **Parameters** FastTab and make the following settings:
    - **New asset type** - Select the new asset type to assign to the selected assets.
    - **Attributes** - Set to *Yes* to append the attribute types associated with the new asset type to the selected assets.
    - **Maintenance plans** - Set to *Yes* to append the maintenance plans associated with the new asset type to the selected assets.
1. Expand the **Run in background** FastTab and set **Batch processing** to *Yes* to run the process of changing asset types as a batch job.
1. Select **OK** in the **Change asset type** dialog to apply your settings.

> [!NOTE]
> Each asset type has settings that define which supporting data can be used for assets of that type. This includes information such as maintenance job types, counters, and attribute types. When you change the asset type, the supporting data for existing assets might not match the supporting data for the new asset type.
>
> For example, suppose asset *A1* has an asset type of *AT1*. *AT1* has two selected maintenance job types: *JT1* and *JT2*. Work orders have been created for *A1* and maintenance job types *JT1* and *JT2* are selected for those work orders. The asset type on asset *A1* is then changed to *AT2*. *AT2* has maintenance job types *JT3* and *JT4* selected. As a result of changing the asset type, you'll now have work orders with maintenance job types that aren't associated with the asset type of the asset for these work orders.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]