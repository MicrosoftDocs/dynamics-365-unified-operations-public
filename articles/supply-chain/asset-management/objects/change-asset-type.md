---
title: Change the asset type of existing assets (preview)
description: Learn how to change the asset type of existing assets, including prerequisites and an outline on changeing asset types of one or more existing assets.
author: jodahl
ms.author: jodahl
ms.topic: how-to
ms.date: 10/27/2023
ms.custom: bap-template
ms.reviewer: kamaybac
ms.search.form:
---

# Change the asset type of existing assets (preview)

[!include [banner](../../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
<!-- KFM: Preview until further notice -->

This article explains how to change the [asset type](../setup-for-objects/object-types.md) of an existing asset.

[!INCLUDE [preview-note](~/../shared-content/shared/preview-includes/preview-note-d365.md)]

## Prerequisites

Before you can use this feature, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management 10.0.38 or later.
- The feature that's named *(Preview) Change types on assets and functional locations* must be turned on in [Feature management](../../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

## Change the asset type of one or more existing assets

To change the asset type of one or more existing assets, follow these steps.

1. Go to **Asset management** \> **Assets** \> **All assets**.
1. On the **All assets** list page, select one or more assets that you want to change asset type for. If you select multiple assets, all of them must be of the same asset type.
1. On the Action Pane, on the **Asset** tab, in the **Maintain** group, select **Change asset type**.
1. In the **Change asset type** dialog box, on the **Parameters** FastTab, set the following fields:

    - **New asset type** – Select the new asset type to assign to the selected assets.
    - **Attributes** – Set this option to *Yes* to append the attribute types that are associated with the new asset type to the selected assets.
    - **Maintenance plans** – Set this option to *Yes* to append the maintenance plans that are associated with the new asset type to the selected assets.

1. On the **Run in background** FastTab, set the **Batch processing** option to *Yes* to run the process of changing asset types as a batch job.
1. Select **OK** to apply your settings.

> [!NOTE]
> Each asset type has settings that define which supporting data can be used for assets of that type. This supporting data includes information such as maintenance job types, counters, and attribute types. When you change the asset type, the supporting data for existing assets might not match the supporting data for the new asset type.
>
> For example, asset *A1* has an asset type of *AT1*. Two maintenance job types, *JT1* and *JT2*, are selected for asset type *AT1*. Work orders have been created for asset *A1*, and maintenance job types *JT1* and *JT2* are selected for those work orders. Later, the asset type of asset *A1* is changed to *AT2*. Maintenance job types *JT3* and *JT4* are selected for asset type *AT2*. Therefore, after the asset type is changed, the work orders have maintenance job types that aren't associated with the asset type of the asset for those work orders.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
