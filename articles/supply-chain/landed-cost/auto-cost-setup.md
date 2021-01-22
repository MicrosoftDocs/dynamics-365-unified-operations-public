---
# required metadata

title: Auto costs setup
description: This topic describes how to set up cost rules for various inbound voyage levels. Based on these rules, the system will calculate the costs an add it automatically. These rules eliminate the need for the user to manually add a cost.
author: RichardLuan
manager: tfehr
ms.date: 01/21/2021
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: [Operations AOT form name to tie this topic to]
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: riluan
ms.search.validFrom: 2021-01-21
ms.dyn365.ops.version: Release 10.0.17
---

# Auto costs setup

[!include [banner](../includes/banner.md)]

Use the **Auto costs** page to set up cost rules for various cost areas (such as voyage, shipping container, folio, purchase order, item, or transfer order line). Based on the rules, and the fields selected when creating records for one of these cost areas, the system will calculate the cost and add it automatically. These rules eliminate the need for the user to manually add a cost.

To work with auto costs, go to **Landed cost \> Costing setup \> Auto costs**. Then set up your auto cost rules using the settings described in the rest of this topic.

## Work with cost areas

Auto costs work like trade agreements or auto miscellaneous charges. Each auto cost record belongs to a particular cost level. Use the **Cost area** drop-down list in the list pane to choose which cost area you want to work with. The list pane only shows auto costs in the currently selected **Cost area**. When you create a new auto cost, it will likewise belong to the **Cost area** currently set here.

Cost areas enable the system to apportion costs across the purchase order lines within that area. For example, a cost for one container will apportion the value to all the products within that shipping container. If there are two or more shipping containers, the same cost type can be specified for each shipping container. This means that it is possible to find the correct auto cost based on container type.

## Commands in the Action Pane

The following table describes the commands available in the Action Pane of the **Auto costs** page.

| **Action** | **Description** |
| --- | --- |
| **Edit** | Edit an existing auto cost. |
| **New** | Create an auto cost. |
| **Delete** | Delete an auto cost. |
| **Copy from** | Create a new auto cost record based on an existing one. You can then freely edit the new record. This can help you create new auto costs quickly. |
| **Display dimensions** | Open a dialog box where you can select the inventory dimensions that appear for the cost transactions that you view. If you clear check boxes, the cost transactions appear with fewer inventory dimensions, and therefore with less detail. If a particular inventory dimension is specified for a particular auto cost, the auto cost will only be applied when the specified inventory dimension is used for the item on a voyage. |

## Settings in the header

The combination of the settings on the header section will determine when and how a particular auto cost is added to a voyage. Only when the details of the auto cost match the details of the header of the voyage/shipping container/folio will the auto cost be applied to that cost area. The total of all of the matching auto costs will determine the estimated landed cost of a voyage, apportioned across each item within the vessel/voyage.

The following table describes all of the settings that can appear in the header section. However, the specific settings available vary according to the currently selected **Cost area** and **Display dimensions** settings.

| Setting | Description |
| --- | --- |
| **Account Code** | Select one of the following values:<ul><li>**Table** - The cost rule applies only to the specified vendors.</li><li>**Group** - The system will look for the vendor cost group associated with the vendor record to apply the cost rule to.<!--KFM: This could be more clear. --></li><li>**All** - The cost rule applies to all vendors. |
| **Shipping&nbsp;company**<br>or **Customs&nbsp;broker**<br> | Select the vendors where this rule applies. If **Account code** is set to *All*, then this field is inactive. If **Account code** is set to *Table* or *Group*, select the vendor or vendor group. |
| **Item code** | Select one of the following values:<ul><li>**Table** - The cost rule applies only to the specified items.</li><li>**Group** - The system will look for the item cost group associated with the item record to apply the cost rule to.<!--KFM: This could be more clear. --></li><li>**All** - The cost rule applies to all items.|
| **Item relation** | Select the items where this rule applies. If **Account code** is set to *All*, then this field is inactive. If **Account code** is set to *Table* or *Group*, select the item or item group. |
| **Mode of delivery** | This field serves two purposes, informational and cost selection. <!--KFM: This could be more clear. --> |
| **Container type** | The shipping container type that the goods will be shipped in. For an auto cost to be applied to a voyage, the container type in the auto cost setup must match that of the voyage. |
| **From&nbsp;port** and **To&nbsp;port** | The ports where voyage source and destination ports. (It is possible that some shipping containers will have a different to ports because the voyage may stop at multiple ports.) For the auto cost to be applied to a voyage, it must have an exact match of both the to and from ports. |
| **Auto cost number** | Shows a unique identifier for the auto cost rule. Its value is generated automatically based on the number sequence set up on the **Landed cost parameters** page. |
| **Inventory dimensions** | Some cost areas allow you to include one or more item dimensions in the header (such as size, color, warehouse, batch number, and so on). Select **Display dimensions** from the Action Pane to choose which dimensions to include. |

## Settings on the Lines FastTab

On the **Lines** FastTab, add a row for each currency that could be used when applying a cost to a purchase order line on a voyage. The system will match the currency of each purchase order line against the currencies specified here on the **Lines** FastTab and will only apply the cost set for the matching line. If there is no line set up for the currency of the purchase order line, that purchase order line will not have the auto cost applied to it. <!-- KFM: But currency is only available for purchase orders and items. Which lines apply for other types of cost area? -->

The following table describes all of the settings that can appear for each line. However, the specific settings available vary according to the currently selected **Cost area**.

| Setting | Description |
| --- | --- |
| **Currency** | Select the currency for which the line applies. This currency relates to the purchase order. The system will select the line with the same currency as the purchase order when attempting to find which auto costs will be applied to s voyages and its voyage lines. (This setting is only available when **Cost area** is set to *Purchase order* or *Item*.) |
| **Cost type code** | Identifies the cost type. |
| **Apportionment method** | <p>Specifies the method of distributing cost to lines. Options are:<ul><li>**Percent** - The value of the **Cost value** field will be a percentage. This percentage applies to the total value of goods. For example:</p><ul><li>Cost value (percent) = 10%</li><li>Goods amount = $800</li><li>Cost value (value) = $80</li></ul><li>**Quantity** - The cost will apportion based on the quantity of goods.</li><li>**Amount** - The cost will apportion based on value of the goods.</li><li>**Volume** - The cost will apportion based on the volume of goods. Volume is specified on the item master.</li><li>**Weight** - The cost will apportion based on the weight of goods. Weight is specified on the item master.</li><li>**Volumetric** - The volumetric divisor is a business defined rate at which to apportion the cost. The divisors are set in a separate table.<!-- KFM: This seems to be missing the point. --></li><li>**Measurement** - This allows for a measurement to be specified within the Landed cost module. This is often used by organizations that do not know the individual volume or weight of the goods but they require a more accurate apportionment than amount or quantity. The freight forwarder or agent will supply them with the weight or cubic measurement, which they place at either an item level or purchase order level.</li></ul><p>For example:</p><ul><li>Sea Freight = $900</li><li>Item A has weight 800kg and volume 2m³</li><li>Item B has weight 100kg and volume 1m³</li></ul><p>The resulting costs apportioned by weight are:</p><ul><li>Item A = $800</li><li>Item B = $100</li></ul><p>The resulting costs apportioned by volume are:</p><ul><li>Item A = $600</li><li>Item B = $300</li></ul><p>**Note**: The measurements field uses the measurement entered for both the &quot;area&quot; (the shipping container) and the lines. For flexible reasons they do not need to add up, but a check can be done if this is required using the statistics to review what the total measurement is. The measurement prompt setting and automatic update of measurement at the shipment/container level are in the shipping parameters. <!-- KFM: This note is confusing. Please revise. --> |
| **From date** | Specify date range (if any) for costing. This is the first date as which the auto cost will apply. |
| **To date** | Specify date range (if any) for costing. This is the last date as which the auto cost will apply. |
| **Category** | <p>Select the method to use for calculating cost. Choose one of the following:</p><ul><li>**Fixed** - Cost will be apportioned based on the apportionment method.</li><li>**Pieces** - Cost per piece will be allocated, so the method apportionment is not used.</li><li>**Percent** - A percentage of the goods&#39; value will be added, so the method of apportionment is not used.</li><li>**Rate** - Used if there are quantity breakdowns. The **Apportionment method** must be *Measurement*.</li><ul> |
| **Broken by quantity** | <p>Select this check box to enable the **Quantity breaks** button on the **Lines** toolbar. Quantity breaks allow the cost to be broken down and have different costs depending on the quantity on the purchase order line of the voyage. This is often used when the mode of delivery is air. To use this option, the **Category** for the line must be set to *Rate*.</p><p>The quantity pertains to the option selected for the **Apportionment method**. The cost value will be up to the quantity entered in the **Quantity** field <!--KFM: Where is the **Quantity** field? -->. For example:</p><ul><li>Quantities of 45-100kg result in a charge of $6.00 per measurement (such as kg/m³)</li><li>Quantities of over 100kg result in a charge of $5.50 per measurement (such as kg/m³)</li></ul> |
| **Cost value** | Enter the value of the cost. |
| **Cost currency code** | Select the currency of the cost. |
| **Item sales tax group** | Select the tax code for the cost. |
| **Minimum cost** | <p>This setting only applies if the **Broken by quantity** check box is selected. Regardless of the costs specified on the **Quantity breaks** page, if the measurement doesn't reach this value, then the minimum value is selected. For example:</p><ul><li>A quantity of 0-45kg results in a charge of $6 per measurement (kg/m³)</li><li>A quantity of 46-100kg results in a charge of $5.50 per measurement (kg/m³)</li></ul><p>If two kilograms were shipped, the quantity break would create a cost value of $12 but if the **Minimum cost** was *$100*, then the final cost would be $100.</p> |
| **Aggregate** | Select this check box to allow users to move this specific cost from the shipping container level to the voyage level. This allows costs to be automatically calculated on the shipping container level but also combined together and apportioned across all items within all the containers on a voyage rather than all items in the individual shipping containers. |
| **Linked cost type** | <p>Link the current line to another line in this same auto costs record by specifying the **Cost type code** for the line you want to link to. The **Category** for the current line must be set to *Percent* to allow this feature. When a line is linked here, the current line will then base its cost on that other cost.</p><p>For example, assume freight is $1,000 and we want a fuel surcharge to be 10% of the freight cost. The line would need a **Category** of *Percent*, a **Cost value** of *10%*, and the **Linked cost type** of *Freight*. |
| **Value&nbsp;adjustment** and **Adjustment&nbsp;amount** | <p>Use these settings to adjust the value and amount for various percentage values (Only available when **Cost area** is set to *Item*)</p><p>Different costing can be set up for different components of an item. One component of an item may have a different cost percentage than the other components of the item, which is sometimes required to value a certain portion of the goods using different rates. For example, duty is calculated for one item at two rates, like a watch where one component has a 2% duty rate and a second component that has a 15% duty rate. In this case, costing would be split between the various components. The cost is calculated for the item, but the cost value is adjusted by the value of the component(s) with the different cost category. The cost of the remaining component(s) can then be calculated by using the amount that the previous calculation was adjusted by.</p><p>For example:</p><ul><li>Component A has a cost of $9.50 and a duty of 15%</li><li>Component B has a cost of $0.50 and a duty of 2%</li><li>Therefore, the total cost is $10.00</li></ul><p>The first entry is for the 10% line. It uses the following values:</p><ul><li>**Category** = *Percent*</li><li>**Cost value** = *10*</li><li>**Value adjusted** = *Adjust by*</li><li>**Adjusted value** = *-0.50*</li></ul><p>This first setup specifies that the cost of the item ($10) must be reduced by $0.50 (the price of the component B) before a 10% duty charge is calculated. Therefore, 10% will be applied to $9.50.</p><p>The second entry is for the 2% line (the $0.50 that the previous entry was adjusted by). It uses the following values:</p><ul><li>**Category** = *Percent*</li><li>**Cost value** = *2*</li><li>**Value adjusted** = *Use*</li><li>**Adjustment** = *0.50*</li></ul><p>This second setup calculates the remaining duty payable on component B.</p> |