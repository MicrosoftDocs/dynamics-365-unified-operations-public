---
# required metadata

title: Location stocking limits
description: This topic describes the location stocking limits functionality
author: perlynne
manager: tfehr
ms.date: 11/11/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: WHSLocationLimit
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
# ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: perlynne
ms.search.validFrom: 2020-11-11
ms.dyn365.ops.version: 10.0.16

---

# Location stocking limits

[!include [banner](../includes/banner.md)]

Use the **Warehouse management \> Setup \> Warehouse \> Location stocking limits** page to control the load capacity at warehouse locations without using the more advanced physical product volumetric calculation processes.

The purpose of location stocking limits is to evaluate a maximum quantity that a location can contain. You can set up the feature on any of three levels, each of which has its own tab on the **Location stocking limits** page:

- **Products**
- **Product variants**
- **Container types**

For each level, you can define different field values. The system will evaluate the capacity of a specific location based on the **Quantity** and **Unit** values for each row, and will select the most detailed matching record first. This means, for example, that a row that includes a value in the **Location profile ID** field will be evaluated before a row that only includes a value in the **Warehouse** field. The remaining capacity will also be evaluated based on the **Quantity** for the used location stocking limit record.

For the **Products** section, you can define the following field values for the location stocking limits search:

- **Warehouse**
- **Location profile ID**
- **Location**
- **Pack size category ID**
- **Item number**
- **Unit**

> [!Note]
> It is not mandatory to define a **Unit** for each location stocking limit record. The location capacity calculations will be done based on the inventory unit quantities and, when using a value without a defined unit conversion, the location stocking limit record record will get skipped (as if it had another **Item number** defined).

## Example – Purchase order receiving

This example shows the process based on a clean *USMF* demo data set with the following setting on the **Product variants** tab of the **Location stocking limits** page:

|Warehouse|Location profile ID|Item number|Size|Quantity|Unit|
|---------|-------------------|-----------|----|--------|----|
|24       |FLOOR              |D0013      |M   |300     |Ea  |
|24       |FLOOR              |D0013      |L   |240     |Ea  |
|24       |FLOOR              |D0013      |S   |360     |Ea  |

The products have different unit of measure product variant setups defined, which are aligned with the location stocking limits for three pallets (PL):

- **Size** *M*: 1 pallet (PL) = 100 each (Ea)
- **Size** *L*: 1 pallet (PL) = 80 each (Ea)
- **Size** *S*: 1 pallet (PL) = 120 each (Ea)

This means that each location that has its **Location profile ID** set to *FLOOR* can carry 3 pallets (PL) of **Item number** *D0013*.

### Prepare for the example

To illustrate the concept, let's run a purchase order receiving flow for two lines. But first make the following updates to the demo data to make sure the locations allow carrying mixed items and that we only use the empty locations *FL-002* to *FL-004* without any open inbound work.

1. For **Location** *FL-001*, change the **Location profile** from *FLOOR* to *FLOOR-05*.
1. For the **Location profile** *FLOOR*, set **Allow mixed items** to *Yes* .
1. Create a purchase order with two lines:
    |Warehouse|Item number|Size|Quantity|Unit|
    |---------|-----------|----|--------|----|
    |24       |D0013      |S   |4       |PL  |
    |24       |D0013      |L   |4       |PL  |

### Process the example

Start receiving **Quantity** *4*, **Unit** *PL*, **Size** *S* after looking at the put line locations for the created work. Then receive **Quantity** *4*, **Unit** *PL*, **Size** *L* and look at the put line locations for the created work.

1. Open the warehouse app and sign in with **User ID** *24*, **Password** *1*.
1. Use the **Inbound** \> **Purchase Receive** menu item and receive *4* *PL* of *D0013* with **Size** *S*.
1. Receive *4* *PL* of **Size** *S*.
1. Look at the putaway work that was created. You should see the following result:
    - 3 PL -> FL-002
    - 1 PL -> FL-003
1. Receive *4* *PL* of **Size** *L*
1. Look at the putaway work that was created. You should see the following result:
    - 1 PL -> FL-003
    - 3 PL -> FL-004

Logically, you might assume that the system has failed to allocate the proper putaway locations. Why did the system not assign 2 more pallets of **Size** *L* to **Location** *FL-003*, so we would have a total of 3 pallets for putaway into this location?

To explain this, we need to understand the selection criteria for the location stocking limits, where the system selects the most detailed matching record. In our case, this is the line for **Size** *L* containing the **Quantity** *240* of **Unit** *Ea*. Because we already have open work from the previous receipt of **Size** *S*, **Quantity** *120*, **Unit**  *Ea*, the remaining capacity is calculated as *240 &ndash; 120 = 120 Ea*, which can only carry 1 pallet of 80 Ea.

> [!Note]
> You can't use location stocking limits to control, for example, the replenishment of items with different quantities within the same location. In this case, use a *replenishment template*.
