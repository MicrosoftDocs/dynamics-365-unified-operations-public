---
# required metadata

title: Packing vs. storage dimensions
description: Some items are packed or stored in such a way that you may need to track physical dimensions differently for each of several different processes. This topic shows how to specify which process (packing, storage, or nested packing) each specified dimension is used for.
author: mirzaab
manager: tfehr
ms.date: 07/21/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: WHSPhysDimUOM
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope:  Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: mirzaab
ms.search.validFrom: 2020-07-21
ms.dyn365.ops.version: Release 10.0.7
---

# Packing vs. storage dimensions

[!include [banner](../includes/banner.md)]

Some items are packed or stored in such a way that you may need to track physical dimensions differently for each of several different processes. The **Physical dimensions** page lets you specify which process (packing, storage, or nested packing) each specified dimension is used for.

- Storage dimensions are used along with location volumetrics to determine how many of each item can be stored various warehouse locations.
- Packing dimensions are used during containerization and the manual packing process to determine how many of each item will fit in various container types. 
- Nested packing dimensions are used when the packing process contains multiple levels.

The remainder of this topic provides a scenario that illustrates how to use this feature.

## Example scenario

### Set up the scenario

### Enable demo data

To work through this scenario using the demo records and values that are specified here, you must be on a system where the standard [demo data](../../fin-ops-core/dev-itpro/deployment/deploy-demo-environment.md) is installed. Additionally, you must select the *USMF* legal entity before you begin.

#### Add a new physical dimension to a product

Add a new physical dimension for a product by doing the following:

1. Go to **Product information management \> Products \> Released products**.
1. On the Action Pane, open the **Manage inventory** tab and, from the **Warehouse** group, select **Physical dimensions**.
1. The **Physical dimensions** page opens. On the Action Pane, select **New** to add a new dimension to the grid and make the following settings for it:
    - **Unit** - Set to *pcs*.
    - **Height** - Change from *4* to *1*.
    - **Type** - Change from *Storage* to *Packing*

    Leave the other settings at their initial values.

<!-- KFM: I don't see the **Type** setting. Do we need to enable something in FM? I couldn't find a likely feature name there. -->

#### Create a new container type

Go to **Warehouse management \> Setup \> Containers \> Container types** and create a new record with the following settings:

- **Container type code** - *Short Box*
- **Description** - *Short Box*
- **Maximum net weight** - *50*
- **Volume** - *300*
- **Length** - *10*
- **Width** - *10*
- **Height** - *3*

#### Create a container group

Go to **Warehouse management \> Setup \> Containers \> Container groups** and create a new record with the following settings:

- **Container group ID** - *Short Box*
- **Description** - *Short Box*

Add a new line to the **Details** section. Set the **Container type** to *Short Box*.

#### Set up a container build template

Go to **Warehouse management \> Setup \> Containers \> Container build templates** and select **Boxes**. Change the **Container group ID** to *Short Box*.

#### Create a location profile

Go to **Warehouse management \> Setup \> Warehouse \> Location profiles** and create a new record with the following settings:

- **Location profile ID** - *Short Storage*
- **Name** - *Short Storage*
- **Location format** - *BULK*
- **Location type** - *BULK*
- **Use license plate tracking** - *Yes*

In the **Dimensions** section, make the following settings:

- **Volume utilization percentage** - *100*
- **Volumetric method used for inventory location** - *Use location volume*
- **Actual location height** - *3*
- **Actual location width** - *10*
- **Actual location depth** - *10*
- **Maximum weight** - *50*

#### Locations

Go to **Warehouse management \> Setup \> Warehouse \> Locations** and create a new record with the following settings:

- **Warehouse** - *63*
- **Location** - *SHORT-01*
- **Location profile ID** - *Short Storage*

### Scenario process

#### Create a sales order and create a shipment

In this process you will create a shipment based on the item *packing* dimensions, for which the height is less than 3.

1. Go to **Sales and marketing \> Sales orders \> All sales orders**.
1. On the Action Pane, select **New**.
1. In the **Create sales order** dialog box, set the following values:

    - **Customer account:** *US-001*
    - **Warehouse:** *63*

1. Select **OK** to create the sales order and close the dialog box.
1. The new sales order is opened. It should include a new, empty line in the grid on the **Sales order lines** FastTab. On this line, set the following values:

    - **Item number:** *A0001*
    - **Quantity:** *1*

1. On the **Sales order lines** FastTab toolbar, select **Inventory \> Reservation**.
1. On the **Reservation** page, on the Action Pane, select **Reserve lot** to reserve the inventory.
1. Close the page.
1. On the Action Pane, open the **Warehouse** tab and select **Release to warehouse** to create work for the warehouse.
1. On the **Sales order lines** FastTab toolbar, select **Warehouse \> Shipment details**.
1. On the Action Pane, open the **Transportation** tab and select **View containers**. Confirm that the item was containerized into the *Short Box* container.

#### Place an item into storage

1. Open the mobile device, sign in to warehouse 63 and go to **Inventory \> Adjust In**.
1. Enter **Loc** = *SHORT-01*, make a new license plate with **Item** = *A0001*, and **Quantity** = *1 pcs*. <!-- KFM: This step might be too vague. I can't picture what's going on here. -->
1. Select **OK**. You will receive the error "Location SHORT-01 failed because item A0001 does not fit in location's specified dimensions." This is because the *Storage* type dimensions of the product are larger than the dimensions specified on the location profile.
