---
# required metadata

title: Create functional locations
description: This article explains how to create a functional location in Asset Management.
author: johanhoffmann
ms.date: 06/25/2019
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: EntAssetFunctionalLocationCopyStructure, EntAssetFunctionalLocationCreate
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

# Create functional locations

[!include [banner](../../includes/banner.md)]

 

This article explains how to create a functional location in Asset Management.

When you create a functional location structure, be aware once you have created a functional location, you cannot move it from the original location. This means that you should carefully consider the structure of your functional locations before you start creating them in Asset Management. If you regret a functional location, you can delete it, provided that it has not yet been taken into use.

To be able to work with functional locations, you start by creating two "categories" of functional locations:

- Create *one* default functional location with not sub locations. This functional location is used only as the standard location for assets when you create new assets.  
- Create the functional location structures required for managing maintenance jobs in your company.

## Create a default functional location

When you use functional locations, start by creating one default location to be used when you create new assets. This functional location is the one you select in **Asset management** > **Setup** > **Asset management parameters** > **Assets** link > **Default functional location** field. The default functional location can be used when you create new assets, and you have not yet set up a functional location structure for those assets.

1. Select **Asset management** > **Functional locations** > **All Functional locations**.  
2. In **All functional locations**, select **New**.
3. Insert an ID in the **Functional location** field, for example, "0000" or "Default", to indicate that this is a special functional location.
4. Insert name for the default functional location in the **Name** field.
5. Do *not* select a parent in the **Parent** field – leave this field blank.
6. In the **Functional location type** field, select the functional location type to be used for the default functional location. See [Functional location types](../setup-for-functional-locations/functional-location-types.md) for more information on how to set up functional location types.
7. Select **OK**. You should not add further data to this functional location as it is only used as a temporary location for new assets until you install the assets on the functional locations used by your company.

## Create functional locations

The following procedure describes how you create the functional locations required for maintenance management in your company.

1. Select **Asset management** > **Functional locations** > **All Functional locations**. You can create a functional location from grid view or details view.
2. Select the **New** button.
3. Insert an ID in the **Functional location** field.
4. Insert a name for the functional location in the **Name** field.
5. If the functional location is a sub location in a structure, select the parent location in the **Parent** field.
6. Select a type in the **Functional location type** field.
7. Select **OK**.
8. Select the functional location and click the **Edit** button to add further information.

>[!NOTE]
>Depending on your setup of functional location lifecycle states, you may have to create all sub locations for a functional location, and then change the functional location lifecycle state before you can start installing assets. See [Install assets on functional
locations](../functional-locations/install-objects-on-functional-locations.md) for more information on asset installation. See [Functional location lifecycle states](../setup-for-functional-locations/functional-location-stages.md) to learn more about setup of
functional location lifecycle states.

In Details view, you will see FastTabs on which you can add and edit information about the functional location.

## General Information

This section provides an overview of parent and child information in the functional location structure. In the **Details** section, you can see the number of asset attributes, maintenance plans, and assets related to the functional location. In the **Inventory** section, you can select the site and warehouse to which the functional location is related. Site and warehouse is used in connection with work order item forecasts. When creating an item forecast, site and warehouse information from the functional location of the asset is automatically used. In the **Lifecycle state** section, information about the functional location lifecycle state is displayed.

## Installed assets

Refer to [Install assets on functional locations](../functional-locations/install-objects-on-functional-locations.md) for more information on asset installation. You can use the **View** button on this FastTab to show more fields on the FastTab. The **Valid from** and **Sub asset** fields can be shown in the grid.

## Asset attribute requirements

On this FastTab you can add specific attribute requirements for the assets that you install on the functional location. These requirements are for information purposes only. They do not prevent you from installing assets with other attribute requirements. Select **Add line** and select the attribute type. Then you insert the relevant **Value**, select a threshold in the **Threshold criteria** field and save the record.

## Maintenance plans and Maintenance rounds

Here you can add maintenance plans and maintenance rounds to the functional location, including a start date. The assets installed on a functional location may have other maintenance plans set up. All maintenance plans and maintenance rounds can be used for scheduling asset calendar entries for a functional location and its currently installed assets.

>[!NOTE]
>If you update the setup of asset types, asset brands, and asset models on maintenance plans in **All functional locations** detail view > **Maintenance plans** FastTab after you have scheduled maintenance plans, existing maintenance schedule entries related to that functional location are automatically deleted. In order to create new schedule entries, which correspond with the updated maintenance plan setup on the functional location, you must run a new maintenance plan schedule for that functional location. 

## Address

Insert the functional location address on the **Address** FastTab. Addresses on functional locations are inherited, meaning if a sub location has no address defined, the address of the parent location is used.

## Workers

On this FastTab, you can add workers affiliated with the functional location, and you can select a functional location as primary for the worker. 

## Attributes

On this FastTab, you can set values for functional location attributes. These attributes can be used to describe properties or characteristics pertinent to the functional location, for example, structural properties, building type, area descriptions, or location above or under ground.

Select **Add line** and select the attribute type. Next, insert the **Value** related to the attribute type and save the record.

## Financial dimensions

You can select financial dimensions for the functional location. [Functional location types](../setup-for-functional-locations/functional-location-types.md) can be set up to allow for automatic update of financial dimensions from a functional location. This means that assets installed on a financial dimension automatically get the financial dimensions for the functional location. This is useful if you want different cost centers, depending on locations.

When data regarding **Site**, **Warehouse**, **Address**, and **Financial dimensions** are updated on a parent functional location, the related sub functional locations can be updated accordingly if you make that selection during the update. A dialog opens, providing you with the update options.

## Copy a functional location structure

If your company has several functional locations with similar location structures, you can use the copy function in Asset Management to quickly create a number of similar location hierarchies. When you copy a specific functional location or an entire structure, the new location or structure has the same name as the one you copied. After the copy procedure is done, you can easily change the name or other settings on the new functional location, provided that the functional location lifecycle state selected for the new functional location allows it.

1. In **All functional locations**, select the functional location you want to copy. For example, you select a top location (parent) if you want to copy the entire functional location structure including sub locations.
2. Select the **Copy functional location structure** button. The location you selected in the list page is shown in the **Copy from** field.
3. Insert the name of the new location in the **New functional location** field.
4. In the **Parent to paste under** field, you should only insert a parent ID if the location you are creating should be part of an existing functional location structure.
5. Click **OK**. The new functional location structure is shown in **All functional locations**.

>[!NOTE]
>When you copy a functional location structure, functional location lifecycle states in the new structure are set to the "first state" that you have created for functional locations. Whether you can rename or delete a functional location using the **Rename** and **Delete** buttons in **All functional locations**, depends on the current lifecycle state of the functional location.

## Delete a Functional Location

A functional location with related sub locations can be deleted if no assets have been installed on any of the functional locations you are trying to delete, and if the current functional location lifecycle state allows it.

1. In **All functional locations**, select the functional location you want to delete.
2. If required, update the functional location to a functional location lifecycle state that allows deletion of a functional location.
3. Select **Delete**.

>[!NOTE]
>If you cannot delete a functional location, instead you can handle deletion by setting up a functional location lifecycle state for this purpose. For example, you can set up a "Scrapped" or "Deleted" stage, which should not be an active stage, in the **Functional location lifecycle states** form.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]