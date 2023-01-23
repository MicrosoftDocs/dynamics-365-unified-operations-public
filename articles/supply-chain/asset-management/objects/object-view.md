---
# required metadata

title: Asset view
description: This article describes the asset view in Asset Management.
author: johanhoffmann
ms.date: 06/26/2019
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: EntAssetObjectTree, EntAssetFunctionalLocationTree
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.custom: 2214
ms.assetid: 2f3e0441-414d-402b-b28b-7ab0d650d658
ms.search.region: Global
# ms.search.industry: 
ms.author: johanho
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Asset view

[!include [banner](../../includes/banner.md)]

 

This article describes the asset view in Asset Management. The **Asset view** page shows active assets and functional locations in a tree view. Therefore, you can easily get an overview of asset relations to functional locations. Additionally, you can view detailed information about functional locations, assets, and related bills of materials (BOMs). You can also get a quick overview of active maintenance requests and work orders that are related to an asset.

1. Select **Asset management** \> **Assets** \> **Asset view**.
2. To change the view that is shown on the page, select a new value in the **View** field.

    > [!NOTE]
    > The default view that is shown when you open the **Asset view** page depends on the value that is selected in the **View** field on the **Assets** tab of the **Asset management parameters** page (**Asset management** \> **Setup** \> **Asset management parameters**).

On the right side of the page, FastTabs shows details of the selected view.

The breadcrumb trail that appears above the tree view shows the current selection in the tree view. This breadcrumb trail uses the following format:

Functional location ID / Functional location ID (if there is more than one functional location) \> Asset ID / Asset ID (if there is more than one asset) - Item number.

If you've selected an asset in the tree view, you can select **Active requests** or **Active work orders** to view the maintenance requests or work orders that are related to the asset. You can also select **Open** \> **Functional location**, **Asset**, or **Asset BOM** to open the related view.

The **Asset functional locations** option that you can select in the **View** field is also available in any asset lookup where you can select an asset. The tree view is shown on an **Asset view** tab, for example, where you [create an asset](../objects/create-an-object.md), create a maintenance request, or create a work order.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]