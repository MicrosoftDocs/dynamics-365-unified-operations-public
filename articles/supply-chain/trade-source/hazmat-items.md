---
# required metadata

title: Work with hazardous material products
description: This topic describes how to set hazardous material properties on release products, how to set stock limits on hazardous items, and how to include hazardous materials in a sales order.
author: dasani-madipalli
manager: tfehr
ms.date: 06/10/2020
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
ms.author: damadipa
ms.search.validFrom: 2020-06-10
ms.dyn365.ops.version: Release 10.0.11
---

# Work with hazardous material products

[!include [banner](../includes/banner.md)]

This topic describes how to set hazardous material properties on release products, how to set stock limits on hazardous items, and how to include hazardous materials in a sales order.

## Set hazardous material specifications for products

Once you have defined a hazardous materials regulation and set up the related reference codes (as described in [Set up hazardous materials](#_Set_up_hazardous)), you can relate this information to released items. The shipping text for shipping documents will be drawn from the released item hazardous materials information.

As part of associating a released item with a hazardous material, you must specify the regulation code and the material. There could be different regulation codes associated with an item depending on various modes of transport, and you can associate multiple regulations and material codes to each item.

To set up a released product as a hazardous material:

1. Go to **Product Information Management \> Products \> Released Products.**
2. Select or create a product to open its **Released product details** page.
3. Expand the **Manage inventory** FastTab and set **Hazardous material** to **Yes**. This flag identifies the item as a dangerous good and is used when printing shipping documentation.
4. On the Action Pane, open the **Manage inventory** tab and, in the **Compliance** group, select **Item hazardous material**.
5. Fill out the **Item hazardous materials** page for your selected item using the settings described in the following subsections.

### Item hazardous materials header

The following table describes the settings available at the top of the **Item hazardous materials** page.

| **Setting** | **Description** |
| --- | --- |
| **Item number** | This is the released product you are working with. |
| **Regulation code** | This is the hazardous material regulation that applies for this product. The regulation defines how the printed shipping text is created for an item and the associated the delivery methods. Once assigned, the code can't be edited on this page. However, you can assign a new regulation code by selecting the **New** button. |
| **Material code** | Select the hazardous material code that applies for the current product (optional). The material code provides a template with default values for many of the other settings on this page. When you select a code, all its hazardous materials specifications are copied to the current product. The system shows a dialog box asking the user to confirm if they want to default the item material data from material code. |
| **Group code** | Select the Hazardous material classification group code that applies for the current product (optional). As with the **Material code** , this setting copies hazardous materials specifications to the current product. The system shows a dialog box asking the user to confirm if they want to default item class group data from group code. |

<a name="hazmat-description"></a>

### Descriptions FastTab

The following table describes the settings available on the **Descriptions** FastTab.

| **Setting** | Description |
| --- | --- |
| **Proper shipping name** | A standard description for the material based on regulation. |
| **Technical name** | This represents the common or generic name for the material that you might manage for your company. |
| **N.O.S.** | Not otherwise specific (N.O.S.) description for the item. N.O.S. shipping names cover groups of similar chemicals and materials with particular end uses that aren't specifically listed by name in the hazmat table. |

### Item ship text translation FastTab

The following table describes the settings available on the **Item ship text translation** FastTab. Use these settings to define shipping print text in each of several languages. You can add as many languages as needed.

| **Setting** | **Description** |
| --- | --- |
| **Language** | Select the language code for the shipping print text used by this row. For example, select **en-us** , if the shipping text is applicable for US English. |
| **Shipping print text** | When you specify a language, the system generates the shipping print text for the material description based on the regulation code. |

<a name="material-management"></a>

### Material management FastTab

The following table describes the settings available on the **Material management** FastTab.

| **Setting** | **Description** |
| --- | --- |
| **Class** | The [hazardous material class](#_Hazardous_material_classes), which is a type of hazardous material that typically maps to the list of classes provided in the regulation that you are conforming to. Note you must select both a class and a division. |
| **Description** | Displays the description defined for the class selected in the **Class** field (read only). |
| **Division** | A [hazardous material division](#_Hazardous_material_divisions)is a subset of a hazardous material class. You must assign both a division and class to each product that includes hazardous materials. |
| **Identification** | The [hazardous material identification](#_Hazardous_material_identification) value, typically based on a United Nations (UN) standard. |
| **Packing group** | This specification identifies the [packing group](#_Hazardous_material_packing) for a hazardous item. |
| **Description** | Displays the description defined for the group selected in the **Packing group** field (read only). |
| **Packing Descriptions** | This is a an identifying code for a [hazardous material packing description](#_Hazardous_material_packing_1) that references a description of how the product must be packed. Packing descriptions can also be translated to multiple languages by selecting a language code and an applicable description for the language. |
| **Hazardous material labels** | A reference to a dangerous goods label. |
| **Limited quantity** |   |
| **Quantity** | This is maximum quantity (in the specified **Unit** ) of this product that will be permitted per shipment if you enable the **Limited quantity** option. |
| **Multiplier** |  |
| **Unit** | The unit of measure that applies to the specified **Quantity**. This will default to the inventory unit for the item.
The quantity limit and hazardous points calculations will convert from this unit to the shipping units as needed based on the conversion rates established in your system. |

### Transport information FastTab

The following table describes the settings available on the **Transport information** FastTab.

| **Setting** | Description |
| --- | --- |
| **Transport category** | The related transport category. |
| **Tunnel Code** | The related tunnel restriction code for this item. |
| **Hazardous material stowage** | This is a reference code often used for sea freight stowage handling when this item is shipped by sea freight |
| **Aircraft type** | This is the aircraft restriction for this material when shipped by air freight. |
| **Packing - cargo aircraft only** | Based on the **Aircraft type** , select the packing instructions code that applies when the product can only be shipped by cargo aircraft. |
| **Packing - passenger and cargo aircraft** | Based on the **Aircraft type** , select the packing instructions code that applies when the product is shipped by either cargo or passenger aircraft. |
| **IATA Star** | A reference to the International Air Transport Association (IATA) dangerous goods list for reference information. |
| **Emergence response** | A reference code often used with sea fright to indicate how to handle the material in an emergency. |

### Environmental information FastTab

The following table describes the settings available on the **Environmental information** FastTab.

| **Setting** | Description |
| --- | --- |
| **Environmentally dangerous** | Set this to **Yes** to indicate that this product is environmentally dangerous. Use for your own reporting purposes. |
| **Marine pollutant** | Set this to **Yes** to indicate that this product is a marine pollutant. Use for your own reporting purposes. |

## Set stock limits for hazardous products

For safety reasons, you may need to limit the total amount of a given product that can be stocked at a single location. To set stock limits for a released product:

1. Go to **Product information management \> Products \> Released products**.
2. Select a product to open its **Released product details** page.
3. On the Action Pane, open the **Manage inventory** tab and, in the **Compliance** group, select **Reporting details**.
4. Set values for the **Hazardous stock limit** and **Hazardous warning limit** fields, as they apply to your selected product.

The **Hazardous material stock limit report** page lets you monitor the stock levels of the hazardous materials in your warehouse locations to make sure they remain under the established, safe limits established here. For details, see [Hazardous material stock limit report](#_Hazardous_material_stock).

## Sales order transactions

To include a product classified as a hazardous material on a sales order, you must associate the relevant shipping carrier to the sales order. To do this, open the sales order, expand the **Delivery** FastTab, and set the **Shipping carrier** and **Carrier service** as needed.

The shipping carrier is also associated with the mode of delivery, so you must ensure that this information aligns with the hazardous material regulation. This means that the mode of delivery specified on the hazardous material regulation must match the specifications on the sales order header. This connects the regulation, shipping carrier, and service with the shipment lines used on a sales order.

Once a sales order is finalized and ready to be shipped, it can be released to warehouse to indicate the transfer between sales to warehouse operations.

The following diagram shows the sequence of activities that occur when the system generates hazardous material reports.

## Shipments

### View hazardous material scores for each shipment line

When viewing **Shipment details** , you can see the hazardous materials points values calculated for each of the load lines included in that shipment. To view the scores:

1. Go to **Warehouse management \> Shipments \> All shipments**.
2. Select a shipment to open its **Shipment details** page.
3. Inspect the lines in the **Load lines** FastTab, where you can see the scores in the following columns:

- **Hazardous material points** : This calculation is based on the products that are marked as hazardous material in the released product setup. It will take the quantity on the load line and reference to the multiplier on the [released product hazardous material setup](#_Material_management_FastTab).
- **Limited quantity net weight:** This calculation is based on the products that are marked as hazardous material in the released product setup. It will take the quantity on each load line and reference the weight on the [released product hazardous material setup](#_Material_management_FastTab) if this item is marked as limited quantity.

### Check for compatibility among hazardous materials included in a shipment

To check whether all the hazardous materials included in a shipment are suitable to be shipped together:

1. Go to **Warehouse management \> Shipments \> All shipments**.
2. Select a shipment to open its **Shipment details** page.
3. On the Action Pane, open the **Shipments** tab and, in the **Actions** group, select **Compatibility check**.
4. The system returns a message to inform you of the results of the check.

The system evaluates compatibility by checking the compatibility group assigned to each product included in the shipment. For more information, see [Hazardous material compatibility groups](#_Hazardous_material_compatibility).

## Loads

### View hazardous material scores for each load line

When viewing **Load details** , you can see the hazardous materials points values calculated for each of the load lines included in that load. To view the scores:

1. Go to **Warehouse management \> Shipments \> All loads**.
2. Select a load to open its **Load details** page. (You can also open load details by selecting a link from a related shipment.)
3. In the **Load** FastTab, you can review the total scores for entire load by inspecting the following fields:

- **Hazardous material points total** : This calculation is based on the products that are marked as hazardous material in the released product setup. It will take the quantity on the load line and reference to the multiplier on the [released product hazardous material setup](#_Material_management_FastTab).
- **Limited quantity net weight:** This calculation is based on the products that are marked as hazardous material in the released product setup. It will take the quantity on the load lines and reference the weight on the [released product hazardous material setup](#_Material_management_FastTab) if this item is marked as limited quantity.

1. To review the scores for each individual line, go to the **Load lines** FastTab, which provides values for each line similar to those described for the previous step.

### Check for compatibility among hazardous materials included in a load

To check whether all the hazardous materials included in a load are suitable to be shipped together:

1. Go to **Warehouse management \> Shipments \> All loads**.
2. Select a shipment to open its **Load details** page. (You can also open load details by selecting a link from a related shipment.)
3. On the Action Pane, open the **Loads** tab and, in the **Actions** group, select **Compatibility check**.
4. The system returns a message to inform you of the results of the check.

The system evaluates compatibility by checking the compatibility group assigned to each product included in the shipment. For more information, see [Hazardous material compatibility groups](#_Hazardous_material_compatibility).

