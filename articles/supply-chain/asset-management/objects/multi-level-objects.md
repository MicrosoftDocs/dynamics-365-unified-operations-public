---
# required metadata

title: Multi-level assets
description: This article explains how to create and delete multi-level assets.
author: johanhoffmann
ms.date: 06/26/2019
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
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

# Multi-level assets

[!include [banner](../../includes/banner.md)]

 

This article explains how to create and delete multi-level assets. You can create assets and related sub-assets in a hierarchical tree structure. In this way, you can show relations and dependencies among assets. Maintenance jobs can be related to all levels of the tree structure. Statistics can also be created for an individual level or as a sum of all sub-asset levels.

On the **All Assets** list page (**Asset management** \> **Assets** \> **All assets**), the **Asset** column lists assets in hierarchical order. The **Parent** column shows the related parent. Additionally, if assets and sub-assets have already been created, the **Asset tree** section in the **Related information** pane shows the assets in a tree structure.

For information about how to create an asset, see [Create an asset](../objects/create-an-object.md). To create a sub-asset, select the parent asset in the **Parent** field on the **General** FastTab.

## Copy an asset or asset structure

If your company has several similar asset structures, you can use the Copy function in Asset Management to quickly create them.

1. Select **Asset management** \> **Assets** \> **All assets**.
2. On the **All assets** list page, select the asset to copy. For example, if you want to copy the whole asset structure, including sub-assets, select a parent asset.
3. Select **Copy asset**. In the **Copy from** section, the **Asset** field is set to the asset that you selected on the list page.
4. In the **Copy to** section, in the **Asset** field, enter the name of the new asset.
5. If the asset that you're creating should be part of an existing asset structure, in the **Parent asset** section, in the **Asset** field, select a parent ID.
6. Select **OK**. The new asset structure is shown on the **All assets** list page. All asset attributes, maintenance plans, and maintenance rounds that are related to the asset that you copied are transferred to the new asset or asset structure.

When you copy an asset structure, the sub-assets in the new structure have the same name as the sub-assets that you copied. After the copy procedure is completed, you can easily change the name and other settings for an asset. Select the asset on the **All assets** list page, and then select the **Edit** button.

> [!NOTE]
> When you copy an asset or asset structure, the lifecycle state of the new assets is reset to whatever state you defined as the initial lifecycle state for assets. The functional location is reset to the default functional location.

## Delete an asset or asset structure

If an asset has related sub-assets, you can delete it only if no maintenance requests, work order jobs, fault registrations, or condition assessments are registered on any of the assets.

1. On the **All assets** list page, select the asset to delete.
2. Select **Delete**.

> [!NOTE]
> If you can't delete an asset by using this procedure, another way to handle deletion is to set up an asset lifecycle state for this purpose. For example, you can set up a **Scrapped** or **Deleted** lifecycle state on the **Asset lifecycle states** page.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]