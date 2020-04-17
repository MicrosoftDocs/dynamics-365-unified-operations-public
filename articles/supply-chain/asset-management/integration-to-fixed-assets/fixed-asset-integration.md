---
# required metadata

title: Integrate asset management with fixed assets
description: By integrating asset management with fixed assets, you'll be able to link fixed assets with maintenance assets.
author: kamaybac
manager: tfehr
ms.date: 04/17/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope:  Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: dabourq
ms.search.validFrom: 2020-04-17
ms.dyn365.ops.version: Release 10.0.11
---

# Integrate asset management with fixed assets

[!include [banner](../../includes/banner.md)]

By integrating the asset management and fixed assets modules, you'll be able to link fixed assets with maintenance assets. This enables fixed asset users to create a maintenance asset from a new or existing fixed asset, and enables asset management users to associate a maintenance asset with an existing fixed asset. This feature also makes it easy for fixed assets users to view the costs posted from work orders for the related maintenance asset.

> [!NOTE]
> In the remainder of this topic, we refer to assets from the asset-management module as *maintenance assets*, and assets from the fixed-assets module as *fixed assets*.

## Set a default location for new maintenance assets created from fixed assets (optional)

This optional configuration option enables you to set a default functional location for new maintenance assets created from fixed assets. You'll typically do this just once, if at all. To make this setting:

1. Go to **Asset Management > Setup > Asset Management parameters**.
1. Open the **Fixed assets** tab.
1. Open the **Functional location** drop-down list and select the default location.
1. On the action pane, select **Save**.

## Work with integrated maintenance and fixed assets

This section provides a collection of procedures that illustrate various ways that can work with the integrated asset-management and fixed-assets features.

### Associate an existing maintenance asset with a fixed asset

To associate an existing maintenance asset with a fixed asset:

1. Go to **Asset management > Assets > All assets** (or **Active assets**).
1. Select an asset.
1. On the **Fixed asset** FastTab, open the **Fixed assets number** drop-down list and select an existing fixed asset.
1. On the action pane, select **Save**.

### View the fixed asset associated with a selected maintenance asset

To view the fixed asset associated with a selected maintenance asset:

1. Go to **Asset management > Assets > All assets** (or **Active assets**).
1. Select an asset.
1. On the **Fixed asset** FastTab, select the hyperlink shown on the **Fixed assets number** drop-down list.
1. The **Fixed assets** page for your selected asset opens (normally found under **Fixed assets > Fixed assets > Fixed assets**).

### View the maintenance asset associated with a selected fixed asset

To view the maintenance asset associated with a selected fixed asset:

1. Go to **Fixed assets > Fixed assets > Fixed assets**.
1. Select an asset.
1. On the action pane, open the **Asset management** tab and select **View > Maintenance asset**.
1. The **Maintenance asset** page for the asset associated with your selected fixed asset opens (normally found under **Asset management > Assets > All assets**).

### View maintenance costs associated with a fixed asset

Maintenance assets can have asset-management work orders posted for them, and each of these work orders typically has a cost. When a fixed asset is associated with a maintenance asset, you can jump straight from the fixed asset to view these related costs.

To view maintenance costs associated with a fixed asset:

1. Go to **Fixed Assets > Fixed Assets > Fixed Assets**.
1. Select an asset.
1. On the action pane, open the **Asset Management** tab and select **View > Maintenance cost**.
1. The **Maintenance cost** page opens, showing the related costs.

<a name="new-maintenance-from-fixed"></a>

### Create a new maintenance asset for an existing fixed asset

To create a new maintenance asset for an existing fixed asset:

1. Go to **Fixed Assets > Fixed Assets > Fixed Assets**.
1. Select an asset.
1. On the action pane, open the **Asset Management** tab and select **New > Create maintenance asset**. (If this option is disabled, then your selected fixed asset might already have a  maintenance asset associated with it.)
1. Finish creating the asset as described in [Create an asset](../objects/create-an-object.md).

### Create a new fixed asset and add a new maintenance asset for it

To create a new fixed asset and add a new maintenance asset for it:

1. Go to **Fixed assets > Fixed assets > Fixed assets**.
1. On the action pane, select **New**.
1. Finish creating the fixed asset as described in [Create a fixed asset](../../../finance/fixed-assets/tasks/create-fixed-asset.md)
1. On the action pane, open the **Asset Management** tab and select **New > Create maintenance asset**.
1. Finish creating the asset as described in [Create an asset](../objects/create-an-object.md).

### Remove the association between two assets

In some cases, you may need to disassociate a maintenance asset from its fixed asset. For example, if you want to [create a new maintenance asset](#new-maintenance-from-fixed) from a fixed asset, then you must clear the existing association first (if there is one).

To remove an existing association between a maintenance asset and fixed asset:

1. Go to **Asset management > Assets > All assets** (or **Active assets**).
1. Find and open the target fixed asset.
1. On the **Fixed asset** FastTab, select and clear the value shown in the **Functional location** field.
1. On the action pane, select **Save**.
