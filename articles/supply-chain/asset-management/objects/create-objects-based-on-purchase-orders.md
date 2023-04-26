---
# required metadata

title: Create assets based on purchase orders
description: This article explains how you can create a list of asset items that can be used as a basis for creating assets for maintenance jobs in Asset Management.
author: johanhoffmann
ms.date: 06/26/2019
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: EntAssetObjectItem, EntAssetPendingAssets
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

# Create assets based on purchase orders

[!include [banner](../../includes/banner.md)]

 

This article explains how you can create a list of asset items that can be used as a basis for creating assets for maintenance jobs in Asset Management. Based on the asset items, you are able to view a list of the purchase order lines that have been created on those items. The purpose of this functionality is to easily create an asset in Asset Management based on a purchase order.

First, you set up the items to be used for creating assets from a purchase order in **Asset items**. After creating a purchase order line, you create the assets in **Pending assets**. It is possible to decide at which stage of the purchase order the asset should be created.


## Select asset items

1. Click **Asset management** > **Setup** > **Assets** > **Items**.
2. Click **New** to create a new asset item.
3. Select the item in the **Item number** field. When you leave that field, the item name is automatically inserted in the **Product name** field.
4. On the **General** FastTab, select an asset type for the item.
5. Select asset manufacturer and model for the item.
6. Save the item.


## Create assets from pending assets

1. Click **Asset management** > **Assets** > **Pending Assets**.
2. You will see an updated list of the purchase orders based on the items selected in **Asset items**.
3. You can filter the status of purchase orders to select at which lifecycle state the asset should be created. For example, you may only want to create assets when a product receipt has been posted on a purchase order.
4. Select the **Reference number** link on a purchase order line to view detailed information about the item.
5. If you want to edit which dimensions are displayed on the **Inventory dimensions** FastTab, click the **Display Dimensions** button, and make your selections.
6. If you want to create an asset based on a purchase order line, select the check box in the **Mark** column for that line on the list page, and click **Create assets**. A message will be displayed informing you of the asset ID.
7. Select the asset in the **All assets** list and click **Edit** to add more information to the asset.
8. In **Pending assets**, if you want to delete a line because you don't want to create an asset, select the check box in the **Mark** column for that line, and click **Discard pending assets**. A message will be displayed informing you of the asset ID. You are not deleting the purchase order or sales order, just the record from which you could have created an asset in **Asset Management**.

>[!NOTE]
>All product dimensions (size, color, configuration etc.) are automatically transferred to the asset attributes. Tracking dimensions (serial number) are stored directly on the asset when the asset is created.


## Find pending assets

You can run a **Pending asset count** to check for pending assets. For example, this function can be used for receiving a notification each time a pending asset is ready to be created as an asset.

1. Click **Asset management** > **Periodic** > **Assets** > **Pending asset count**.
2. Click **OK** to run the job and update the list in **Pending assets**.
3. You can set up this job to run as a batch job, for example, once each day.

**Caution:** If data is changed on a purchase order *after* you have created an asset based on the appertaining item, those changes will not be reflected on the asset.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]