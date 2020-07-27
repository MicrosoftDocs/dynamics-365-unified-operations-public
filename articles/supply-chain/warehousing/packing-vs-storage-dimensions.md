---
# required metadata

title: Packing vs. storage dimensions
description: This topic illustrates the differences between the packing and storage dimensions
author: mirzaab
manager: tfehr
ms.date: 07/21/2020
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
ms.author: mirzaab
ms.search.validFrom: 2020-07-21
ms.dyn365.ops.version: Release 10.0.7
---

# Packing vs. storage dimensions

[!include [banner](../includes/banner.md)]

<!-- KFM: Please add an intro that explains what this topic is about. -->

## Set up

### Release product

Go to **Product information management \> Products \> Released products**  and select A0001. Select **Physical dimensions** in the **Manage inventory – Warehouse** section of the ribbon.

Create a new record, specify the unit pcs, and change the height from 4 to 1. Change the **Type** from *Storage* to *Packing*.

### Container types

Go to **Warehouse management \> Setup \> Containers \> Container types** and create a new record with the following settings:

- **Container type code** - *Short Box*
- **Description** - *Short Box*
- **Maximum net weight** - *50*
- **Volume** - *300*
- **Length** - *10*
- **Width** - *10*
- **Height** - *3*

### Container groups

Go to **Warehouse management \> Setup \> Containers \> Container groups** and create a new record with the following settings:

- **Container group ID** - *Short Box*
- **Description** - *Short Box*

Add a new line to the **Details** section. Set the **Container type** to *Short Box*.

### Container build template

Go to **Warehouse management \> Setup \> Containers \> Container build templates** and select **Boxes**. Change the **Container group ID** to *Short Box*.

### Location profiles

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

### Locations

Go to **Warehouse management \> Setup \> Warehouse \> Locations** and create a new record with the following settings:

- **Warehouse** - *63*
- **Location** - *SHORT-01*
- **Location profile ID** - *Short Storage*

## Process

### Containerization (packing)

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

This process used the *Packing* type dimensions, for which the height is less than 3.

### Storage

1. Open the mobile device, sign in to warehouse 63 and go to **Inventory \> Adjust In**.
1. Enter Loc = SHORT-01, make up a new LP, Item = A0001, and quantity = 1 pcs.
1. Select **OK**. You will receive the error "Location SHORT-01 failed because item A0001 does not fit in location's specified dimensions." This is because the *Storage* type dimensions of the product are larger than the dimensions specified on the location profile.
