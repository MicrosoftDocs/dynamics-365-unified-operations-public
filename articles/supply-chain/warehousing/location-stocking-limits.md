---
# required metadata

title: Location stocking limits
description: This topic describes the location stocking limits functionality
author: perlynne
manager: tfehr
ms.date: 09/15/2020
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
ms.search.validFrom: 2020-09-15
ms.dyn365.ops.version: 10.0.15

---

# Location stocking limits

[!include [banner](../includes/banner.md)]

The  **Warehouse management \> Setup \> Warehouse \> Location stocking limits** can be used to control the load capacity on warehouse locations without using the more advanced physical product volumetric calculation processes.
The concept of the **Location stocking limits** is to evaluate a maximum quantity, a location can contain.
The setup can get defined on three levels:
-	Products
-	Product variants
-	Container types

For each level, different field values can get defined, but the evaluation of the capacity on a specific location will happen based on the selected **Location stocking limits** **Quantity** and **Unit** record values, which will get selected for the most detailed matching record first. This e.g. means that a record including a value in the **Location profile ID** field will get evaluated before a record only including a value in the **Warehouse** field. The remaining capacity will as well get evaluated based on the used **Location stocking limit** **Quantity**.

For the **Products** section, the following field values can get defined for the **Location stocking limits** search:
-	Warehouse
-	Location profile ID
-	Location
-	Pack size category ID
-	Item number
-	Unit

>[!Note]
> It is not mandatory to define an **Unit** for the **Location stocking limit**. The location capacity calculations will be done based on the inventory unit quantities and in case of using a value without a defined unit conversion, the **Location directive limit** record will get skipped (like it had another **Item number** defined).


## Example – Purchase order receiving

This example shows the process based on a clean _USMF_ demo data set having the **Location stocking limits \> Product variant** setup defined as:


|Warehouse|Location profile ID|Item number|Size|Quantity|Unit|
|---------|-------------------|-----------|----|--------|----|
|24       |FLOOR              |D0013      |M   |100     |Ea  |
|24       |FLOOR              |D0013      |L   |240     |Ea  |
|24       |FLOOR              |D0013      |S   |360     |Ea  |

The products have different unit of measure product variant setup defined which is aligned with the **Location stocking limits** for 3 pallets (PL):

> **Size** **_M_** 1 pallet (PL) = 100 each (Ea)
>
> **Size** **_L_** 1 pallet (PL) = 80 each (Ea). 
>
>**Size** **_S_** 1 pallet (PL) = 120 each (Ea). 

This basically means that each location having the **Location profile** **_FLOOR_** defined can carry 3 pallets (PL) of item **_D0013_**.

### Prepare for the example
To illustrate the concept, let’s run a purchase order receiving flow for two lines. But please make the following two updates in the demo data to make sure the locations allow to carry mixed items and that we only use the empty locations: _FL-002_ - _FL-004_ without any open inbound work.

> Change the **Location profile** from **_FLOOR_** to **_FLOOR-05_** for **Location** **_FL-001_**.

And

> Select the **Allow mixed items** to **_Yes_** for the **Location profile** **_FLOOR_**.

>Then create a purchase order with two lines:
>|Warehouse|Item number|Size|Quantity|Unit|
>|---------|-----------|----|--------|----|
>|24       |D0013      |S   |4       |PL  |
>|24       |D0013      |L   |4       |PL  |


### Process the example

Start receiving **_4_** **_PL_** **Size** **_S_** following looking at the put line locations for the created work.
Then receive **_4_** **_PL_** of **Size** **_L_** and then look at the put line locations for the created work.
1.	Use the **Warehouse app** and login with **User ID** **_24_** Password **_1_** 
2.	Use the **Inbound** \> **Purchase Receive** menu item and receive **_4_** **_PL_** of **_D0013_** **Size** **_S_**.
3.	Receive **_4_** **_PL_** of **Size** **_S_**
4.	Look at the put-away work getting created. You should see the following result:
> - 3 PL -> FL-002
> - 1 PL -> FL-003
5.	Receive **_4_** **_PL_** of **Size** **_L_**
6.	Look at the put-away work getting created. You should see the following result:
> - 1 PL -> FL-003
> -	3 PL -> FL-004

Logically one would ague that the system has failed in allocating the proper put-away locations. Why did the system not assign 2 more pallets of **Size** **_L_** to location **_FL-003_**, so we in total would have 3 pallets for put-away into this location?

To explain this, we need to understand the selection criteria for the **Location stocking limit** where the most detailed record match gets selected. In our case this will be the line for **Size** **_L_** containing the **Quantity** **_240_** of **Unit** **_Ea_**.
Because we already have open work from the previous receiving of **Size** **_S_**  of **_120_** **_Ea_** the remaining capacity gets calculated as 240-120 =120 Ea which then only can carry 1 pallet of 80 Ea.
> [!Note]
> **Location stocking limits** is not a process you can use to control e.g. replenishment of items with different quantities within the same location, here you should use the **Replenishment templates**.
