---
# required metadata

title: Integrate asset management with fixed assets
description: By integrating asset management with fixed assets, you'll be able to link fixed assets with maintenance assets.
author: dabourq
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
ms.author: XXXX
ms.search.validFrom: 2020-04-14
ms.dyn365.ops.version: Release 10.0.12
---
<!-- KFM: add Dana's GitHub user name to metadata -->
# Integrate asset management with fixed assets

By integrating asset management with fixed assets, you'll be able to link fixed assets with maintenance assets. This enables fixed asset users to create a maintenance asset from a new or existing fixed asset, and enables asset management users to associate a maintenance asset with an existing fixed asset. This feature also makes it easy for fixed assets users to view the costs posted from work orders for the related maintenance asset.

To associate an asset-management asset to a fixed-assets asset:

1. Go to **Asset management > Assets > All assets** (or **Active assets**).
1. Select an asset.
1. On the **Fixed asset** FastTab, open the **Fixed assets number** drop-down list and select an existing fixed-assets asset.
1. On the action pane, select **Save**.

To view a fixed-assets asset from asset management:

1. Go to **Asset management > Assets > All assets** (or **Active assets**).
1. Select an asset.
1. On the **Fixed asset** FastTab, select the hyperlink shown on the **Fixed assets number** drop-down list.
1. The **Fixed assets** page for your selected fixed asset opens (normally found under **Fixed assets > Fixed assets > Fixed assets**).

To view an asset-management asset for an existing fixed-assets asset:

1. Go to **Fixed assets > Fixed assets > Fixed assets**.
1. Select an asset.
1. On the action pane, select **Asset Management**.
1. On the View menu, click Maintenance Asset 
1. This will redirect the user to that asset in Asset Management > Assets form.

To view cost from posted Asset Management Work Orders for an asset, from Fixed Assets: 
1.    Go to Navigation pane > Modules > Fixed Assets > Fixed Assets > Fixed Assets 
2.    Select and click on an asset.
3.    On the Action pane, click Asset Management. 
4.    On the View menu, click Maintenance Cost.

To create a Maintenance Asset for an existing Fixed Assets asset
1.    Go to Navigation pane > Modules > Fixed Assets > Fixed Assets > Fixed Assets 
2.    Select and click on an asset.
3.    On the Action pane, click Asset Management. 
4.    In New Menu, click on "Create maintenance asset"
5.    Create asset as shown in https://docs.microsoft.com/en-us/dynamics365/supply-chain/asset-management/objects/create-an-object 

To set a default Functional Location for Management Assets created from Fixed Assets:
1.    Go to Navigation pane > Modules > Asset Management > Setup > Asset Management parameters > Fixed assets
2.    Select the desired Functional Location
3.    Save and exit

To create an Asset Management asset for a new Fixed Assets asset:
1.    Go to Navigation pane > Modules > Fixed assets > Fixed assets > Fixed assets
2.    On the Action pane, click New.
3.    Create the Fixed Asset as described in https://docs.microsoft.com/en-us/dynamics365/finance/fixed-assets/tasks/create-fixed-asset
4.    In New Menu, click on "Create maintenance asset"
5.    Create asset as shown in https://docs.microsoft.com/en-us/dynamics365/supply-chain/asset-management/objects/create-an-object