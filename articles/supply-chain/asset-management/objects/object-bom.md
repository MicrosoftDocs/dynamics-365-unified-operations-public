---
# required metadata

title: Asset BOMs
description: This article describes asset bills of materials (BOMs) in Asset Management.
author: johanhoffmann
ms.date: 06/26/2019
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: EntAssetStandardSparePartsItemGroup, EntAssetObjectBOM
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

# Asset BOMs

[!include [banner](../../includes/banner.md)]

 

This article describes asset bills of materials (BOMs) in Asset Management. The **Asset BOM** page shows a list of all items (spare parts and other items) that are used on an asset during its whole lifetime. When you create a new asset, you should consider setting up an asset BOM as a part of the setup procedure. In this way, you can track item history for the asset from the creation date.

After you've completed a maintenance job, and item consumption has been registered on a work order, you can track consumption of spare parts and other items that are used on the asset. This functionality lets you keep a complete item consumption record for all your assets. For example, you can use the record to monitor whether a specific spare part is often replaced, or to keep track of the spare parts or other items that are currently used on an asset.

> [!NOTE]
> On a work order, item consumption might include both spare parts and other, additional items, such as lubricants, bolts, and gaskets.

An asset BOM can be automatically updated based on the setup in Asset Management. If a work order lifecycle state has been created to handle finished or completed work orders, and if the **Update asset BOM** option for that work order lifecycle state is set to **Yes** on the **Work order lifecycle states** page, all items that are used on the work order will be automatically updated on the **Asset BOM** page when the work order is updated to that lifecycle state. 


You can also manually update an asset BOM by creating new item lines on the **Asset BOM** page.

On the **Asset BOM** page, you can track spare parts history for assets after item consumption is registered on a work order. To use this functionality, you must select the item groups that should be used for spare parts registration on the **Spare parts item groups** page.

To use asset BOM functionality, you must first set up the required spare parts items groups. Then, if you want the asset BOM to be automatically updated when a work order is completed, you can set up a work order lifecycle state to handle that update. 


## Set up spare parts item groups

The setup of spare parts history is based on item groups that are created in the **Inventory and warehouse management** module. In Asset Management, you set up item groups so that you can track spare parts history for the items in the selected item groups.

1. Select **Asset management** \> **Setup** \> **Asset** \> **Spare parts item groups**.
2. Select **New** to set up an item group.
3. In the **Item group** field, select the group. The name of the group is automatically entered in the **Name** field.

## View and update asset BOMs

After you post item consumption on a work order, you can view the registered item consumption on the **Asset BOM** page.

1. Select **Asset management** \> **Assets** \> **Active assets**. Select the asset in the list, and then select **Asset BOM**.

    > [!NOTE]
    > To view all item consumption registrations on all assets, select **Asset management** \> **Inquiries** \> **Assets** \> **Asset BOM**.

2. Select **Update asset BOM**. You can add assets, asset types, and resources to the update as you require by selecting **Select**. Select **OK** to start the update. You can also set up the Update function as a batch job.
3. If you want to see more information that is related to the items, you can add inventory dimensions. Select **Inventory** \> **Dimensions display**, and then select the check boxes for the dimensions that you want to see. To keep this setup for all assets on the **Asset BOM** page, set the **Save setup** option to **Yes**.
4. To get an overview of where in Asset Management the item on the selected line is used, in relation to assets, job type defaults, spare parts, and work orders, select **Item where used**. 
5. If you want to see only active item lines, select **View** \> **Current**. To see all item lines, including lines where the expiration date is earlier than the current date, select **View** \> **All**.

> [!NOTE]
> When you've completed a work order, if some items or spare parts that are related to the related asset have expired or have been replaced by other items or spare parts, we recommend that you update the asset BOM accordingly.

## Create a new item line in an asset BOM

You can manually create item lines for assets.

1. On the **Asset BOM** page, select **New**.
2. In the **Asset** field, select the asset to add an item line for.
3. In the **Line number** field, enter a sequential line number.
4. In the **Effective** field, enter a start date for the item.
5. If the item will expire, in the **Expiration** field, enter an end date.
6. In the **Item number** field, select the item. The name is automatically entered in the **Product name** field.
7. In the **Quantity** field, enter the quantity that is used. The **Unit** field is automatically updated.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]