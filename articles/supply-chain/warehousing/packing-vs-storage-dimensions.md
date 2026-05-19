---
title: Set different dimensions for packing and storage
description: Learn how to specify which process (packing, storage, or nested packing) each specified dimension is used for with an outline of an example scenario.
author: Mirzaab
ms.author: mirzaab
ms.topic: how-to
ms.date: 5/19/2026
ms.custom:
  - bap-template
ms.reviewer: kamaybac
ms.search.form: EcoResPhysicalProductDimensions, WHSPhysDimUOM
---

# Set different dimensions for packing and storage

[!include [banner](../../includes/banner.md)]

Some items are packed or stored in such a way that you need to track physical dimensions differently for each of several different processes. The *Packaging product dimensions* feature lets you set up one or several types of dimensions for each product. Each dimension type provides a set of physical measurements (weight, width, depth, and height), and establishes the process where those physical measurement values apply. When you enable this feature, your system supports the following types of dimensions:

- *Storage* - Storage dimensions work with location volumetrics to determine how many of each item can be stored in various warehouse locations.
- *Packing* - Packing dimensions work during containerization and the manual packing process to determine how many of each item fits in various container types.
- *Nested packing* - Nested packing dimensions work when the packing process contains multiple levels.

Set up *storage* dimensions by using the **Physical dimension** page in Supply Chain Management. All processes use these dimensions when the packing and nested packing dimensions aren't specified.

Set up *packing* and *nested packing* dimensions by using the **Physical product dimensions** page.

This article provides a scenario that illustrates how to use this feature.

## Example scenario

### Set up the scenario

Before you run the example scenario, prepare your system as described in this section.

#### Enable demo data

To work through this scenario using the demo records and values that are specified here, use a system where the standard [demo data](../../fin-ops-core/fin-ops/get-started/demo-data.md) is installed. Also, select the *USMF* legal entity before you begin.

#### Add a new physical dimension to a product

Add a new physical dimension for a product by following these steps:

1. Go to **Product information management > Products > Released products**.
1. Select the product with **Item number** *A0001*.
1. On the Action Pane, open the **Manage inventory** tab. From the **Warehouse** group, select **Physical product dimensions**.
1. The **Physical product dimensions** page opens. On the Action Pane, select **New** to add a new dimension to the grid with the following settings:
    - **Physical dimension type** - *Packing*
    - **Physical unit** - *pcs*
    - **Weight** - *4*
    - **Weight unit** - *kg*
    - **Depth** - *3*
    - **Height** - *4*
    - **Width** - *3*
    - **Length** - *cm*
    - **Volume unit** - *cm3*

The **Volume** field is automatically calculated based on your **Depth**, **Height**, and **Width** settings.

#### Create a new container type

Go to **Warehouse management \> Setup \> Containers \> Container types** and create a new record with the following settings:

- **Container type code** - *Short Box*
- **Description** - *Short Box*
- **Maximum net weight** - *50*
- **Volume** - *144*
- **Length** - *6*
- **Width** - *6*
- **Height** - *4*

#### Create a container group

Go to **Warehouse management \> Setup \> Containers \> Container groups** and create a new record with the following settings:

- **Container group ID** - *Short Box*
- **Description** - *Short Box*

Add a new line to the **Details** section. Set the **Container type** to *Short Box*.

#### Set up a container build template

Go to **Warehouse management \> Setup \> Containers \> Container build templates** and select **Boxes**. Change the **Container group ID** to *Short Box*.

### Run the scenario

After you prepare your system as described in the previous section, you're ready to run the scenario as described in the next section.

#### Create a sales order and create a shipment

In this process, you create a shipment based on the item *packing* dimensions, for which the height is less than 3.

1. Go to **Sales and marketing > Sales orders > All sales orders**.
1. On the Action Pane, select **New**.
1. In **Create sales order**, set the following values:

    - **Customer account:** *US-001*
    - **Warehouse:** *63*

1. Select **OK** to create the sales order and close the dialog box.
1. The new sales order opens. It includes a new, empty line in the grid on the **Sales order lines** FastTab. On this line, set the following values:

    - **Item number:** *A0001*
    - **Quantity:** *5*

1. On the **Sales order lines** FastTab, select **Inventory > Reservation**.
1. On the **Reservation** page, on the Action Pane, select **Reserve lot** to reserve the inventory.
1. Close the page.
1. On the Action Pane, open the **Warehouse** tab and select **Release to warehouse** to create work for the warehouse.
1. On the **Sales order lines** FastTab, select **Warehouse > Shipment details**.
1. On the Action Pane, open the **Transportation** tab and select **View containers**. Confirm that the item was containerized into the two *Short Box* containers.

#### Place an item into storage

1. Open the mobile device, sign in to warehouse 63, and go to **Inventory > Adjust In**.
1. Enter **Loc** = *SHORT-01*. Make a new license plate with **Item** = *A0001* and **Quantity** = *1 pcs*.
1. Select **OK**. You receive the error "Location SHORT-01 failed because item A0001 doesn't fit in location's specified dimensions." This error occurs because the *Storage* type dimensions of the product are larger than the dimensions specified on the location profile.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
