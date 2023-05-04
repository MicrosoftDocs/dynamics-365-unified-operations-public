---
# required metadata

title: Create an asset
description: This article describes how to create an asset in Asset Management.
author: johanhoffmann
ms.date: 06/26/2019
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: EntAssetObjectTableCopyStructure, EntAssetObjectTableCreate
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

# Create an asset

[!include [banner](../../includes/banner.md)]

 

This article describes how to create an asset in Asset Management.

1. Click **Asset management** > **Assets** > **All assets** or **Active assets**.
2. Click the **New** button.
3. In the **Create assets** dialog, insert data regarding **Asset** (the asset ID) and the asset name. Select date and time for the asset in the **Effective** field. From that date, you are able to install the asset on a functional location as well as move and replace the asset in an asset structure.
4. In the **Asset type** field, select the asset type for the asset (mandatory field). If required, select **Asset manufacturer** and **Asset model** for the asset. If only one product has been set up, that product is automatically selected in the **Asset manufacturer** field. The selections available in the **Asset manufacturer** and **Asset model** fields depend on the setup in [Asset manufacturers and models](../setup-for-objects/product-and-model.md).
5. In the **Parent asset** group, the **Asset** field is blank as default. If required, you can select a parent asset, and then all fields in the **Parent asset** group will automatically be filled out.
    >[!NOTE]  
    >When you select a parent asset, two or three tabs are available: The **My assets** tab contains assets related to the functional locations to which you (the maintenance worker who is logged on the system) may be allocated. If no functional locations are set up on a maintenance worker in the [Maintenance workers and worker groups](../setup-for-objects/workers-and-worker-groups.md) form, the **My assets** tab will not be visible. The **Active assets** tab contains a list of all assets with asset lifecycle state "Active". The **Asset view** tab displays a tree view of functional locations and assets installed on those locations.

6. The default functional location you have set up is suggested for the asset in the **Asset** group > **Functional location** field. Select another functional location, if required.

    >[!NOTE]
    >After you have created an asset, you can install it on another functional location, if required. Only top-level assets (assets without a current parent asset) can be installed on a functional location. This means that you install the top level as well as any child assets on the selected functional location. Read more about installing assets on functional locations in [Introduction to functional locations](../functional-locations/introduction-to-functional-locations.md).

7. Click **OK**.
8. Select the asset in the **All Assets** list and click the **Edit** button to add further information to the asset.

## General information

The functional location to which the asset is related is shown in the **Functional location** field. If the asset is a parent asset, the number of children related to the asset is shown in the **Children** field. If the asset is a sub asset to an existing asset, the ID of the parent asset is shown in the **Parent** field.

You can edit **Asset manufacturer** and **Asset model** information on the asset, which is used to manage spare parts, alternative spare parts, and job type defaults. Refer to [Asset manufacturers and models](../setup-for-objects/product-and-model.md) for more information. You can also add information about **Model year** and **Serial number**, if required.

**Current lifecycle state** is used to define if the asset is active or inactive. When creating an asset, the stage is always set to the first stage in the asset stage group. When you are ready to activate an asset, click **Update asset state**, and select the lifecycle state that you have defined as "asset active", and click **OK**.

**Note:** When an asset is set to "inactive", it is no longer possible to create work orders for the asset. Also, you cannot schedule preventive maintenance jobs for an inactive asset.

The **Service level** and **Criticality** fields relate to work orders created for the asset. The fields show the **Service level** and **Criticality** numbers calculated for the current setup for the asset. Refer to [Asset service levels](../setup-for-objects/object-priorities.md) and [Asset criticality types](../setup-for-objects/object-criticalities.md) regarding setup of those values.

## Asset

You can select a **Resource** for the asset. The resource selection determines which calendar is used for work order scheduling. Resource selection is often used for fixed assets. Resources and
resource groups are set up in **Organization administration** > **Resources** > **Resource groups** or **Resources**.

In the **Fixed assets number** field, you can select a fixed asset to be related to the asset. This is relevant if your asset is related to an investment project.

- If the asset is related to a fixed asset, you can create a work order type to be used for work orders related to an investment project. 
- Information about fixed assets for an asset is related to the **Fixed assets** module in Dynamics 365 Supply Chain Management. This means that in **Fixed assets** > **Fixed assets** > **Fixed assets**, you can get an overview of the Asset Management projects that may be related to a fixed asset by selecting the asset in the list and viewing the contents in the **Related information** pane > **Associated projects** section.


## Details

In the **Active from** field, the date on which you updated the asset lifecycle state to an active state (refer to [Asset lifecycle states](../setup-for-objects/object-stages.md) regarding setup of asset lifecycle states), is shown. If the asset is no longer active, and you have updated the asset lifecycle state to an inactive lifecycle state, the date from which the asset is inactive is shown in the **Active to** field. If required, you can manually change those dates.

If required, you can insert an expected date for replacement of the asset in the **Replacement date** field. An estimated value for replacing the asset can be inserted in the **Replacement value** field. Example: You can use replacement information to compare it with the costs of maintaining an asset, and subsequently make a decision for purchasing a new asset if maintenance costs on the existing asset increase rapidly.

## Notes

You can add notes related to the asset on the **Notes** FastTab. Click the **Add timestamp** button before you write the note, if you want to add user information and a date/timestamp to the note.

## Attributes

On this FastTab, you can set values for asset attributes. These attributes can be used to describe properties or characteristics pertinent to the asset, for example, size, weight, or machine configuration.

Click **Add line** and select the attribute type. Next, insert the **Value** related to the attribute type and save the record.

>[!NOTE] 
>You can get an overview of asset attribute types and their relation to the assets in **Asset attribute** and **Asset attribute overview**. Refer to [Asset attribute overview](../objects/object-specification-overview.md) for more information.

## Vendor

On the **Vendor** FastTab, select a vendor account for the asset. Also, if a vendor warranty has been granted, you can insert warranty information here.

## Address

On the **Address** FastTab, you can insert the address of the equipment. If no address is inserted on the asset, the asset uses the address of a parent asset, if the parent asset has an address. If no address is related to the asset or any parents in the asset hierarchy, the address of the functional location on which the asset is installed may be used. If that functional location does not have an address related to it, the address of the parent functional location is used on the asset.

## Asset management plans

Maintenance plans are used for scheduling preventive maintenance jobs at regular intervals on the asset. On this FastTab, you can set up maintenance plan lines for the selected asset. Maintenance rounds can be set up for various assets, on which you need to carry out a similar task at regular intervals. On the **Functional location maintenance plans** tab, you see the maintenance plans related to the functional location on which the asset is installed.

>[!NOTE]
>If you delete a maintenance plan line or a maintenance round related to an asset in **All Asset**, you also automatically delete all maintenance schedules with status "Created" that have been created based on that maintenance plan or maintenance round.

## Functional location maintenance plans

On this FastTab, you get an overview of the maintenance plans related to the functional location on which the asset is installed.

## Maintenance rounds

On this FastTab, you can add or remove maintenance rounds, which are related to the asset.

## Financial dimensions

You can select financial dimensions for the asset.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]