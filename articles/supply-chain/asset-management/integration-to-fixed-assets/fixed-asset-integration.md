---
# required metadata

title: Integrate asset management with fixed assets
description: This article explains how to integrate the Asset management and Fixed assets modules, so that you can link fixed assets with maintenance assets.
author: johanhoffmann 
ms.date: 04/17/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this article to]
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for articles migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: johanho
ms.search.validFrom: 2020-04-17
ms.dyn365.ops.version: 10.0.11
---

# Integrate asset management with fixed assets

[!include [banner](../../includes/banner.md)]

By integrating the **Asset management** and **Fixed assets** modules, you can link fixed assets with maintenance assets. Fixed assets users can then create a maintenance asset from a new or existing fixed asset, and Asset management users can associate a maintenance asset with an existing fixed asset. This feature also makes it easy for Fixed assets users to view the costs that were posted from work orders for related maintenance assets.

> [!NOTE]
> In this article, *maintenance assets* refer to assets from the **Asset management** module, and *fixed assets* refer to assets from the **Fixed assets** module.

## Set a default location for new maintenance assets that are created from fixed assets (optional)

This optional configuration lets you set a default functional location for new maintenance assets that are created from fixed assets. You typically complete this configuration this just one time, if you complete it at all.

To complete the configuration, follow these steps.

1. Go to **Asset management \> Setup \> Asset management parameters**.
1. On the **Fixed assets** tab, in the **Functional location** field, select the default location.
1. On the Action Pane, select **Save**.

## Work with integrated maintenance assets and fixed assets

This section provides a collection of procedures that show various ways that you can work with the integrated Asset management and Fixed assets features.

### Associate an existing maintenance asset with a fixed asset

To associate an existing maintenance asset with a fixed asset, follow these steps.

1. Go to **Asset management \> Assets \> All assets** (or **Active assets**).
1. Select an asset.
1. On the **Fixed asset** FastTab, in the **Fixed asset number** field, select an existing fixed asset.
1. On the Action Pane, select **Save**.

### View the fixed asset that is associated with a selected maintenance asset

To view the fixed asset that is associated with a selected maintenance asset, follow these steps.

1. Go to **Asset management \> Assets \> All assets** (or **Active assets**).
1. Select an asset.
1. On the **Fixed asset** FastTab, in the **Fixed asset number** field, select the link.

    The **Fixed assets** page for the selected asset is opened. (Typically, this page is found at **Fixed assets \> Fixed assets \> Fixed assets**.)

### View the maintenance asset that is associated with a selected fixed asset

To view the maintenance asset that is associated with a selected fixed asset, follow these steps.

1. Go to **Fixed assets \> Fixed assets \> Fixed assets**.
1. Select an asset.
1. On the Action Pane, on the **Asset management** tab, in the **View** group, select **Maintenance asset**.

    The **Maintenance asset** page for the asset that is associated with the selected fixed asset is opened. (Typically, this page is found at **Asset management \> Assets \> All assets**.)

### View maintenance costs that are associated with a fixed asset

Asset management work orders can be posted for maintenance assets, and each of those work orders typically has a cost. When a fixed asset is associated with a maintenance asset, you can go directly from the fixed asset to view the related costs.

To view the maintenance costs that are associated with a fixed asset, follow these steps.

1. Go to **Fixed assets \> Fixed assets \> Fixed assets**.
1. Select an asset.
1. On the Action Pane, on the **Asset management** tab, in the **View** group, select **Maintenance cost**.

    The **Maintenance cost** page is opened and shows the related costs.

### <a name="new-maintenance-from-fixed"></a>Create a new maintenance asset for an existing fixed asset

To create a new maintenance asset for an existing fixed asset, follow these steps.

1. Go to **Fixed assets \> Fixed assets \> Fixed assets**.
1. Select an asset.
1. On the Action Pane, on the **Asset management** tab, in the **New** group, select **Create maintenance asset**. (If this option is unavailable, a maintenance asset might already be associated with the selected fixed asset.)
1. Finish creating the asset as described in [Create an asset](../objects/create-an-object.md).

### Create a new fixed asset and add a new maintenance asset for it

To create a new fixed asset and add a new maintenance asset for it, follow these steps.

1. Go to **Fixed assets \> Fixed assets \> Fixed assets**.
1. On the Action Pane, select **New**.
1. Finish creating the fixed asset as described in [Create a fixed asset](../../../finance/fixed-assets/tasks/create-fixed-asset.md).
1. On the Action Pane, on the **Asset management** tab, in the **New** group, select **Create maintenance asset**.
1. Finish creating the asset as described in [Create an asset](../objects/create-an-object.md).

### Remove the association between two assets

In some cases, you might have to disassociate a maintenance asset from its fixed asset. For example, if you want to [create a new maintenance asset](#new-maintenance-from-fixed) from a fixed asset, you must first remove any existing association.

To remove an existing association between a maintenance asset and a fixed asset, follow these steps.

1. Go to **Asset management \> Assets \> All assets** (or **Active assets**).
1. Find and open the maintenance asset.
1. On the **Fixed asset** FastTab, clear the value from the **Fixed asset number** field.
1. On the Action Pane, select **Save**.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
