---
# required metadata

title: Location stocking limits
description: This article describes the functionality for location stocking limits.
author: perlynne
ms.date: 11/11/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: WHSLocationLimit
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
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

You can use the **Location stocking limits** page (**Warehouse management \> Setup \> Warehouse \> Location stocking limits**) to control the load capacity at warehouse locations without having to use the more advanced processes for volumetric calculations of physical products.

The purpose of location stocking limits is to evaluate the maximum quantity that a location can contain. You can set up the feature on any of three levels, each of which has its own tab on the **Location stocking limits** page:

- Products
- Product variants
- Container types

For each level, you can define different field values. The system will then evaluate the capacity of a specific location, based on the **Quantity** and **Unit** values for each row. It will select the most detailed matching record first. For example, a row that has a value in the **Location profile ID** field will be evaluated before a row that has a value only in the **Warehouse** field. The remaining capacity will also be evaluated, based on the **Quantity** value for the location stocking limit record that is used.

In the **Products** section of the page, you can define the following field values for the search for location stocking limits:

- Warehouse
- Location profile ID
- Location
- Pack size category ID
- Item number
- Unit

> [!NOTE]
> You don't have to define a **Unit** value for each location stocking limit record. The location capacity calculations will be based on the inventory unit quantities. If no unit conversion is defined for a value that is used, the location stocking limit record will be skipped, as if another **Item number** value is defined for it.

For more information about how to set up stocking limits based on container types, see [Manage inbound putaway based on container types](inbound-putaway-by-container-type.md).

## Example – Purchase order receiving

This example is based on a clean *USMF* demo data set, where the following values are set on the **Product variants** tab of the **Location stocking limits** page.

| Warehouse | Location profile ID | Item number | Size | Quantity | Unit |
|-----------|---------------------|-------------|------|----------|------|
| 24        | FLOOR               | D0013       | M    | 300      | Ea   |
| 24        | FLOOR               | D0013       | L    | 240      | Ea   |
| 24        | FLOOR               | D0013       | S    | 360      | Ea   |

Different unit of measure product variants are set up for the products. These variants are aligned with the location stocking limits for three pallets (PL):

- **Size M:** 1 PL = 100 each (Ea)
- **Size L:** 1 PL = 80 Ea
- **Size S:** 1 PL = 120 Ea

Therefore, each location where the **Location profile ID** value is set to *FLOOR* can carry *3* *PL* of item number *D0013*.

### Prepare for the example

In this example, you will run a purchase order receiving flow for two lines. However, you must first update the demo data in the following way to ensure that the locations allow mixed items to be carried, only the empty locations *FL-002* through *FL-004* are used, and there is no open inbound work.

1. For location *FL-001*, change the value of the **Location profile** field from *FLOOR* to *FLOOR-05*.
1. For the *FLOOR* location profile, set the **Allow mixed items** option to *Yes*.
1. Create a purchase order that has the following two lines.

    | Warehouse | Item number | Size | Quantity | Unit |
    |-----------|-------------|------|----------|------|
    | 24        | D0013       | S    | 4        | PL   |
    | 24        | D0013       | L    | 4        | PL   |

### Process the example

You will first receive a quantity of *4* of unit *PL* in size *S*, and review the put line locations for the work that is created. You will then receive a quantity of *4* of unit *PL* in size *L*, and review the put line locations for the work that is created.

1. In the Warehouse Management mobile app, sign in by using *24* as the user ID and *1* as the password.
1. Select **Inbound** \> **Purchase Receive**.
1. Receive *4* *PL* of item number *D0013* in size *S*.
1. Review the putaway work that was created. You should see the following result:

    - 3 PL -\> FL-002
    - 1 PL -\> FL-003

1. Receive *4* *PL* of item number *D0013* in size *L*.
1. Review the putaway work that was created. You should see the following result:

    - 1 PL -\> FL-003
    - 3 PL -\> FL-004

Based on the results, you might conclude that the system failed to allocate the correct putaway locations. Otherwise, why did the system add only *1* *PL* of size *L* to location *FL-003* in the last step, not *2* *PL*? That is, why isn't there is a total of *3* *PL* for putaway to that location?

To explain this apparent failure, you must understand the selection criteria for the location stocking limits. The system selects the most detailed matching record. In this example, the most detailed matching record is the line where the **Size** value is *L*, the **Quantity** value is *240*, and the **Unit** value is *Ea*. Because you already have open work from the previous receipt of a quantity of *120* *Ea* of size *S*, the remaining capacity is calculated as *240* – *120* = *120* *Ea*. Therefore, the remaining capacity can carry only *1* *PL* of *80* *Ea*.

> [!NOTE]
> You can't use location stocking limits to control, for example, the replenishment of items that have different quantities in the same location. In this case, use a *replenishment template*.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]