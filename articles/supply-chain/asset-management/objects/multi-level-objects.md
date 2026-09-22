---
title: Multi-level assets
description: Learn how to create and delete multi-level assets, including outlines on copying assets and asset structures and deleting asset structures.
author: jodahlMSFT
ms.author: jodahl
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 09/22/2026
ms.custom:
  - bap-template
---

# Multi-level assets

[!INCLUDE [banner](../../includes/banner.md)]

This article explains how to create and delete multi-level assets. You can create assets and related sub-assets in a hierarchical tree structure. By using this structure, you can show relations and dependencies among assets. You can relate maintenance jobs to all levels of the tree structure. You can also create statistics for an individual level or as a sum of all sub-asset levels.

On the **All Assets** list page (**Asset management** > **Assets** > **All assets**), the **Asset** column lists assets in hierarchical order. The **Parent** column shows the related parent. If you create assets and sub-assets, the **Asset tree** section in the **Related information** pane shows the assets in a tree structure.

For information about how to create an asset, see [Create an asset](../objects/create-an-object.md). To create a sub-asset, select the parent asset in the **Parent** field on the **General** FastTab.

## Copy an asset or asset structure

If your company has several similar asset structures, use the copy function in Asset Management to quickly create them.

1. Select **Asset management** > **Assets** > **All assets**.
1. On the **All assets** list page, select the asset to copy. For example, if you want to copy the whole asset structure, including sub-assets, select a parent asset.
1. Select **Copy asset**. In the **Copy from** section, the **Asset** field is set to the asset that you selected on the list page.
1. In the **Copy to** section, in the **Asset** field, enter the name of the new asset.
1. If the asset that you're creating should be part of an existing asset structure, in the **Parent asset** section, in the **Asset** field, select a parent ID.
1. Select **OK**. The new asset structure is shown on the **All assets** list page. All asset attributes, maintenance plans, and maintenance rounds that are related to the asset that you copied are transferred to the new asset or asset structure.

When you copy an asset structure, the sub-assets in the new structure have the same name as the sub-assets that you copied. Their IDs combine the new top-level asset ID with the original sub-asset ID. For example, if you copy to new asset *AST-000200*, sub-asset *AST-000046* becomes *AST-000200AST-000046*. However, if the number sequence for assets is automatic, each new sub-asset takes the next ID from that number sequence instead. After the copy procedure is completed, you can easily change the name and other settings for an asset. Select the asset on the **All assets** list page, and then select the **Edit** button.

> [!NOTE]
> When you copy an asset or asset structure, the lifecycle state of the new assets resets to the initial lifecycle state for assets. The functional location resets to the default functional location.

## Delete an asset or asset structure

If an asset has related sub-assets, you can delete it only if no maintenance requests, work order jobs, fault registrations, or condition assessments are registered on any of the assets.

1. On the **All assets** list page, select the asset to delete.
1. Select **Delete**.

> [!NOTE]
> If you can't delete an asset by using this procedure, another way to handle deletion is to set up an asset lifecycle state for this purpose. For example, you can set up a **Scrapped** or **Deleted** lifecycle state on the **Asset lifecycle states** page.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
