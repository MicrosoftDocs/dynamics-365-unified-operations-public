---
title: Pack containers using the Warehouse Management mobile app
description: This article describes how to configure and use Pack containers using the Warehouse Management mobile app.
author: perlynne
ms.date: 09/01/2022
ms.topic: article
ms.search.form: WHSMobileAppFlowStepListPage, WHSMobileAppFlowStepAddDetour,WHSMobileAppFlowStepDetourSelectFields
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: perlynne
ms.search.validFrom: 2022-09-01
ms.dyn365.ops.version: 10.0.31
---

# Pack containers using the Warehouse Management mobile app

[!include [banner](../includes/banner.md)]

## Feature introduction

Businesses that ship large items or have large packing areas will benefit from this mobile packing experience. The Dynamics 365 Warehouse Management mobile app provides warehouse workers with the freedom to move around while performing their packing activities.
Traditionally, warehouse workers have performed packing activities at a specific packing station configured in Dynamics 365 Supply Chain Management, using a process optimized for shipments of small to medium sized parcels. To improve efficiency when working in larger packing areas, and to better support the packing and shipment of larger items, the Dynamics 365 Warehouse Management mobile app provides a mobile packing experience that gives workers the freedom to move around while performing packing activities.
This section will describe how to use the shipment container packing process on the Warehouse Management mobile app which can be used in combination with the rich client **Pack** page process. You can read more about how to enable the general warehouse management packing process [here]( packing-containers.md).


## Turn on the Pack containers using the Warehouse Management mobile app feature and its prerequisites

Before you can use the functionality that is described in this article, you must complete the following procedure to turn on the required features.

1. Go to **System administration \> Workspaces \> Feature management**. (For more information about how to use the **Feature management** workspace, see [Feature management overview](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).)

 

1. If not already on, turn on the feature that is listed in the following way:

    - **Module:** *Warehouse management*
    - **Feature name:** *Warehouse app step instructions*

    This feature is a prerequisite for the *Warehouse management app data inquiry flow* feature. For more information about the *Warehouse app step instructions* feature, see [Customize step titles and instructions for the Warehouse Management mobile app](mobile-app-titles-instructions.md).

1. If not already on, turn on the feature that is listed in the following way:

    - **Module:** *Warehouse management*
    - **Feature name:** *Warehouse management app detours*

    This feature is a prerequisite for the *Warehouse management app data inquiry flow* feature. For more information about the *Warehouse management app detours* feature, see [Configure detours for steps in mobile device menu items](warehouse-app-detours.md).


1. If not already on, turn on the feature that is listed in the following way:

    - **Module:** *Warehouse management*
    - **Feature name:** *Multi-level detours for the Warehouse Management mobile app*

   See [Multi-level detours for the Warehouse Management mobile app](warehouse-app-multi-level-detours.md).

1. Make sure to update the field names in the Warehouse Management mobile app by going to **Warehouse management \> Setup \> Mobile device \> Warehouse app field names** and selecting **Create default setup**. Repeat this step for each legal entity (company) where you use the Warehouse Management mobile app. For more information, see [Configure fields for the Warehouse Management mobile app](configure-app-field-names-priorities-warehouse.md).

1. If not already on, turn on the feature that is listed in the following way:

    - **Module:** *Warehouse management*
    - **Feature name:** *Warehouse management app data inquiry flow*

   See [Query data using Warehouse Management mobile app detours](warehouse-app-data-inquiry.md).

1. If not already on, turn on the feature that is listed in the following way:

    - **Module:** *Warehouse management*
    - **Feature name:** *Pack containers using the Warehouse Management mobile app*

      This feature is the one that is described in this article.

## Warehouse Management mobile app packing process
As soon as the shipment inventory items have been brought forward to the packing area you can start processing the **Pack inventory into containers** on the Warehouse Management mobile app. 
 ![Warehouse app packing flow](media/wma-packing-flow.png "Warehouse app packing flow")

To leverage all the supported packing processes on the Warehouse Management mobile app you must enable three mobile device menu items:
-	**Pack inventory into containers** - Used for the main process to pack items into containers
-	**Container creation** - Used to create containers going to be used to pack shipment items into
-	**Container closing** -  Used to close the shipment containers

It is recommended to use the [Detour]( warehouse-app-detours.md) functionality to ease the Warehouse Management mobile app operations by having the **Container creation** and **Container closing** embedded into the **Pack inventory into containers** menu item by using the [Detour](warehouse-app-detours.md) option. It is as well recommended to add several look up options as part of the Warehouse Management mobile app to easy and fasten the packing operation by using the [Data inquiry](warehouse-app-data-inquiry.md) in combination with the [Detour]( warehouse-app-detours.md) functionalities. This is especially effective in cases of having unreadable or missing barcodes.

### Pack inventory into containers
During the **Pack inventory into containers** process the workers must identify and confirm the following information:
-	**Packing location** - Where the container packing occurs (can get defaulted from the warehouse **Worker** page)
-	**Shipment Id** - To validate which inventory items to pack
-	**Item number** and **Quantity** - To identify what is going to get packed
-	**Container Id** - In where the shipping items are going to get packed into

Please note that the **Container packing policy** must be defaulted from the **Worker** setup.

### Container creation
To create a container on the *Warehouse Management mobile app* the following data are needed:
-	**Packing location** - Where the container creation happens (can get defaulted from the warehouse **Worker** page - and/or via a [Detour](warehouse-app-detours.md))
-	**Shipment Id** - to validate which inventory items are planned to get packed into the container (Can get defaulted via [Detour](warehouse-app-detours.md))
-	**Container type Id** - to identify the maximum values for the physical volume and weight capacity constraints for the container
-	**Container ID** - to get a unique number to identify the shipping container

Please note that the **Container packing policy** must be defaulted from the **Worker** setup.
### Container closing
For the **Container closing** process which can get triggered directly from the Warehouse Management mobile app menu and/or embedded into the **Pack inventory into containers** menu item by using the [Detour](warehouse-app-detours.md) option, the following information must get defined:
-	**Container ID** to get closed
-	**Weight** of the container which will get defaulted based on the item master weight definition


# Example scenario
In the following example you lean how to setup a *Warehouse Management mobile app packing flow* and process an simple outbound sales order flow in the [Contoso demo data](../../fin-ops-core/dev-itpro/deployment/deploy-demo-environment.md) company **USMF** by packing a container and closing it via the *Warehouse Management mobile app*. 


 
The example will be running with the demo data associated with the *Worker*/*Person* 'Julia Funderburk'.
## Define Worker set up for container packing
You must set up the **Container packing policy** and **Packing profile ID** for the workers using the Warehouse Management mobile app container packing process.

1.	Go to **Warehouse management > Setup > Worker**
2.	Select **Edit**
3.	Select worker *Julia Funderburk* in the list.
4.	Make the following settings for the worker in the **Profile** section:
    - **Container packing policy** - Select *WH62Close* which will move container the *Baydoor* location when closing a container.
- **Packing profile ID** - Select * WH62* which will not create warehouse work after the closing of a container.
5.	Make the following settings for the worker in the **Default packing station** section:
-	**Site** - Select *6*, released to the warehouse we are going to use
-	**Warehouse** - Select *62*, a warehouse already enabled for the packing process in the demo data.
-	**Location** - Select *Pack*. Note that the Warehouse Management mobile app will always prompt for confirmation for the assigned value, which can get overwritten. In case you do not provide a default packing location value the warehouse worker must always scan or look up the packing location in the app.
## Create a new mobile device menu item -- + Container create and close?
You must create a new mobile device menu item to pack inventory into containers via the Warehouse Management mobile app.
1.	Go to **Warehouse management > Setup > Mobile device > Mobile device menu items**
2.	Select **New** on the Action Pane to add a new mobile device menu item
3.	Make the following settings for the new menu item:
    - **Menu item name** - Enter *Container packing* as the name for the new menu item
    - **Title** - Enter *Container packing*, this will get displayed on the Warehouse app
   - **Mode** - Select *Indirect*
   - **Activity code** - Select *Pack inventory into containers*
       4. Close the page

## Add the new mobile device menu items to a menu
With now having the mobile device menu item, we are ready to get it added to the **Mobile device menu**. This is required to use it for the container packing process.
In this example we will add it to the existing *Outbound** mobile device menu.
1. Open **Warehouse management > Setup > Mobile device > Mobile device menu**.
1. Select **Edit**.
1. Select **Outbound** menu in the list
1. Select the new **Container packing** mobile device menu items in the **Available menus and menu items** list.
1. Select the arrow-bottom to move this menu item into the **Menu structure** list in the select **Outbound** menu.
1. Close the page
## Container create
## Container close
## Create sales orders
We will create a single sales order line to quickly showcase the capability: 
<!-- Copy from existing doc. When reviewed--> 
….
1. Make a note about the *Shipment ID*


## Process container packing using the Warehouse app
(Copy from review page) The inventory items have now been brought forward to the packing area and are ready to get packed into containers via the Warehouse Management mobile app.
1.	Open the Warehouse Management mobile app and login with User ID *62*, Password *1*
2.	Select menu *Outbound*
3.	Select mobile device menu item *Container packing*
4.	Confirm the *Pack* packing location in the **Packing location Id** page
5.	Enter the *Shipment ID* from previous section in the **Shipment ID** page
6.	Enter *A0001* in the **Item Id** page
7.	
8.	Confirm to pack the two pcs … create container
In case you only want to pack 1 out the two you can click on the quantity and thereby go to the a page where the quantity can get updated.

TIP!
You can enable detours to look up packing locations, shipments, container types, and containers to close in case barcodes cannot get read or non-existing. Please refer to the [Query data using Warehouse Management mobile app detours](????.md) for more information regarding this capability. 



## Rich client **Pack** vs Warehouse Management mobile app
List of “scenarios” - like C&E documentation
The following table shows which functionalities are supported when using the Warehouse Management mobile app.

|Function                 |  Warehouse app processing |
|------------------------| -------------------------------------| 
|License plate or shipment| Only **Shipment id** identification is supported|
|New container                                         | Yes - via **Container creation**|
|Close container                                       |Yes - via **Container closing**  |
|Release container                                    |Only via container closing policy |
|Reopen container                                    | No |
|Change container packing policy           | No - it is only possible to use the Container packing policy defined on Worker|
|Release shipment                                    | No |
|Work details                                            |View via Data inquire detour (link) |
|Containers for shipment (Open/Closed) | View via Data inquire detour (link) |
|Shipment details                                      | View via Data inquire detour (link) |
|Display dimensions  | No - Capturing of tracking dimensions are not possible |
|Manifest containers | No - Only automatic manifesting setup is supported |
|Unmanifest containers | No |
|Manifest container group | No - Only automatic manifesting setup is supported |
|Unmanifest container group | No |
|Manifest shipment|  No - Only automatic manifesting setup is supported |
|Unmanifest shipment | No |
|Transport route rate details
|Transport shipment accessorial charges
|Transport status
|Print packing slip |  No - Only automatic printing setup is supported |
|Print container content |  No - Only automatic printing setup is supported |
|Print shipping label |  No - Only automatic printing setup is supported |

|Pack (all shipment items) |  No - Each item number must be identified |
|Pack items (based on defined quantity) |  Only AFTER the item number has been identified by updating the quantity as part of the **Pack inventory into containers** process |
|Container group license plate ID with delayed work creation|   No |


Catch weight, product variants, and tracking dimension capturing are not supported.
Closing container ….


Container closing policy (Automatic release/Delayed release/Optional)
Container release policy (

|Close (auto release) container without work creation
|Close container with packing slip processing

Unsupported

Deliverable 703573: [RF Packing][Container closing] Support for "Container closing policy" Optional (visualstudio.com)
Container packing policy
Container closing policy = Optional will not prompt the worker to select if the container will get released or not.




## Example scenarios

This article uses example scenarios to show how you can use the *Pack containers using the Warehouse Management mobile app* feature.





[!INCLUDE[footer-include](../../includes/footer-banner.md)]