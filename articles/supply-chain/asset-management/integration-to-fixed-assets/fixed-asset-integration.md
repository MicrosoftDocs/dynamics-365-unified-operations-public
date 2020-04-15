---
# required metadata

title: Integrate asset management with fixed assets
description: By integrating asset management with fixed assets, you'll be able to link fixed assets with maintenance assets.
author: XXXX
manager: tfehr
ms.date: 04/14/2020
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
ms.search.validFrom: 2020-04-14
ms.dyn365.ops.version: Release 10.0.12
---
<!-- KFM: add Dana's GitHub user name to metadata -->
# Integrate asset management with fixed assets

By integrating the asset management and fixed assets modules, you'll be able to link fixed assets with maintenance assets. This enables fixed asset users to create a maintenance asset from a new or existing fixed asset, and enables asset management users to associate a maintenance asset with an existing fixed asset. This feature also makes it easy for fixed assets users to view the costs posted from work orders for the related maintenance asset.

<!-- KFM: Is a "maintenance asset" the same as an "asset-management asset"? If so, we should describe this in the intro and then use just one of these terms in the rest of this topic. (I prefer "maintenance asset") -->

## Set a default location for new asset-management assets created from fixed assets (optional)

This optional configuration option enables you to set a default functional location for new asset-management assets created from fixed assets. You'll typically do this just once, if at all. To make this setting:

1. Go to **Asset Management > Setup > Asset Management parameters**.
1. Open the **Fixed assets** tab.
1. Open the **Functional location** drop-down list and select the default location.
1. On the action pane, select **Save**.

<!-- KFM: The labeling in the UI here suggests that we are choosing a functional location for *fixed assets*, not for *asset-management assets* (which aren't mentioned here). We should consider improving the labeling, though the tooltip helps to clarify this.  -->

## Work with integrated assets

This section provides a collection of procedures that illustrate various ways that can work with the integrated asset-management and fixed-assets features.

<!-- Maybe we should have a procedure that describes how to remove the asset association (eg, so we can make a new one).  -->

### Associate an existing asset-management asset with a fixed-assets asset

To associate an existing asset-management asset with a fixed-assets asset:

1. Go to **Asset management > Assets > All assets** (or **Active assets**).
1. Select an asset.
1. On the **Fixed asset** FastTab, open the **Fixed assets number** drop-down list and select an existing fixed-assets asset.
1. On the action pane, select **Save**.

### View the fixed-assets asset associated with a selected asset-management asset

To view the fixed-assets asset associated with a selected asset-management asset:

1. Go to **Asset management > Assets > All assets** (or **Active assets**).
1. Select an asset.
1. On the **Fixed asset** FastTab, select the hyperlink shown on the **Fixed assets number** drop-down list.
1. The **Fixed assets** page for your selected asset opens (normally found under **Fixed assets > Fixed assets > Fixed assets**).

### View the maintenance asset associated with a selected fixed-assets asset

To view the maintenance asset associated with a selected fixed-assets asset:

1. Go to **Fixed assets > Fixed assets > Fixed assets**.
1. Select an asset.
1. On the action pane, open the **Asset management** tab and select **View > Maintenance asset**.
1. The **Maintenance asset** page for the asset associated with your selected fixed asset opens (normally found under **Asset management > Assets > All assets**).

### View maintenance costs associated with a fixed asset

Maintenance assets can have asset-management work orders posted for them, and each of these work orders typically has a cost. When a fixed asset is associated with a maintenance asset, you can jump straight from the fixed asset to view these related costs.

<!-- KFM: This confused me, so I added the intro here. Please read and confirm that I have understood this correctly. -->
To view maintenance costs associated with a fixed asset:

1. Go to **Fixed Assets > Fixed Assets > Fixed Assets**.
1. Select an asset.
1. On the action pane, open the **Asset Management** tab and select **View > Maintenance cost**.
1. The **Maintenance cost** page opens, showing the related costs.

### Create a maintenance asset for an existing fixed-assets asset

To create a maintenance asset for an existing fixed-assets asset:

1. Go to **Fixed Assets > Fixed Assets > Fixed Assets**.
1. Select an asset.
1. On the action pane, open the **Asset Management** tab and select **New > Create maintenance asset**. (If this option is disabled, then your selected fixed asset might already have a  maintenance asset associated with it.)
1. Finish creating the asset as described in [Create an asset](../objects/create-an-object.md).

### Create a new fixed-assets asset and add a new maintenance asset for it
<!-- KFM: The following procedure seems redundant with the previous one. Maybe we should delete it. -->
To create a new fixed-assets asset and add a new maintenance asset for it:

1. Go to **Fixed assets > Fixed assets > Fixed assets**.
1. On the action pane, select **New**.
1. Finish creating the fixed asset as described in [Create a fixed asset](../../../finance/fixed-assets/tasks/create-fixed-asset.md)
1. On the action pane, open the **Asset Management** tab and select **New > Create maintenance asset**.
1. Finish creating the asset as described in [Create an asset](../objects/create-an-object.md).