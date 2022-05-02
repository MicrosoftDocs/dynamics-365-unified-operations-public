---
# required metadata

title: Auto costs setup
description: This topic describes how to set up cost rules for various inbound voyage levels. Based on these rules, the system calculates the costs and automatically adds them. Therefore, users don't have to manually add the costs.
author: Weijiesa
ms.date: 01/21/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: ITMCostAutoSetup
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: weijiesa
ms.search.validFrom: 2021-01-21
ms.dyn365.ops.version: 10.0.17
---

# Auto costs setup

[!include [banner](../../includes/banner.md)]

You can use the **Auto costs** page to set up cost rules for various cost areas (such as voyages, shipping containers, folios, purchase orders, items, or transfer order lines). Based on the rules, and the fields that users select when they create records for one of the cost areas, the system calculates the costs and automatically adds them. Therefore, users don't have to manually add the costs.

To work with auto costs, go to **Landed cost \> Costing setup \> Auto costs**. Then set up your auto cost rules as described in the rest of this topic.

## Work with cost areas

Auto costs work like trade agreements or auto miscellaneous charges. Each auto cost record belongs to a specific cost level. Use the **Cost area** field in the list pane of the **Auto costs** page to select the cost area that you want to work with. The list pane shows only auto costs that belong to the currently selected cost area. Any auto cost that you create will belong to the currently selected cost area.

Cost areas enable the system to apportion costs across the purchase order lines in a cost area. For example, a cost for one shipping container will apportion the value to all the products in that shipping container. If there are two or more shipping containers, the same cost type can be specified for each shipping container. Therefore, the container type can be used to find the correct auto cost.

## Buttons on the Action Pane

The following table describes the buttons that are available on the Action Pane of the **Auto costs** page.

| Button | Description |
|---|---|
| Edit | Edit an existing auto cost. |
| New | Create an auto cost. |
| Delete | Delete an auto cost. |
| Copy from | Create a new auto cost record that is based on an existing record. You can then freely edit the new record. This button helps you quickly create new auto costs. |
| Display dimensions | Open a dialog box where you can select the inventory dimensions that are shown for the cost transactions that you view. If you clear check boxes, fewer inventory dimensions will be shown for the cost transactions. Therefore, less detail will be shown for the transaction. If an inventory dimension is specified for an auto cost, the auto cost will be applied only when the specified inventory dimension is used for the item on a voyage. |

## Settings on the header

The combination of settings in the header section determines when and how a specific auto cost is added to a voyage. An auto cost will be applied to a voyage, shipping container, or folio only when the details of the auto cost match the details on the header of that cost area. The sum of all matching auto costs determines the estimated landed cost of a voyage. This cost is apportioned across all the items on the vessel or voyage.

The following table describes all the fields that can appear in the header section. However, the specific fields that are available vary, depending on the cost area and display dimensions that are currently selected.

| Field | Description |
|---|---|
| **Account code** | <p>Select one of the following values:</p><ul><li>**Table** – The cost rule applies only to a specific vendor.</li><li>**Group** – The cost rule applies to a specific vendor group. The system will look for the [vendor cost type group](costing-parameters-setup.md) that is associated with the vendor record.</li><li>**All** – The cost rule applies to all vendors. |
| **Shipping company** | Select the vendor or vendor group that the cost rule applies to. This field is available only if you select *Table* or *Group* in the **Account code** field. |
| **Customs broker** | Select the vendor or vendor group that the cost rule applies to. This field is available only if you select *Table* or *Group* in the **Account code** field. |
| **Item code** | <p>Select one of the following values:</p><ul><li>**Table** – The cost rule applies only to a specific item.</li><li>**Group** – The cost rule applies to a specific item group. The system will look for the [item cost type group](costing-parameters-setup.md) that is associated with the item record.</li><li>**All** – The cost rule applies to all items.|
| **Item relation** | Select the item or item group that the cost rule applies to. This field is available only if you select *Table* or *Group* in the **Item code** field. |
| **Mode of delivery** | Select the mode of delivery (such as air or sea) that the cost rule applies to. |
| **Container type** | The type of shipping container that the goods will be shipped in. An auto cost can be applied to a voyage only if the container type in the auto cost setup matches the container type of the voyage. |
| **From port** and **To port** | The source ("from") port and destination ("to") port of the voyage. (Some shipping containers might have different "to" ports, because the voyage might stop at multiple ports.) An auto cost can be applied to a voyage only if the "from" and "to" ports in the auto cost setup match the "from" and "to" ports of the voyage. |
| **Auto cost number** | The unique identifier of the auto cost rule. The value of this field is automatically generated based on the number sequence that is set up on the **Landed cost parameters** page. |
| **Inventory dimensions** | Some cost areas let you include one or more item dimensions on the header (such as size, color, warehouse, and batch number). Select **Display dimensions** on the Action Pane to select the dimensions that should be included. |

## Settings on the Lines FastTab

On the **Lines** FastTab, add a row for each currency that can be used when a cost is applied to a purchase order line on a voyage. 

For items and purchase orders, the system will match the currency of each purchase order line against the currencies that are specified on the **Lines** FastTab. It will apply only the cost value that is set for the matching line or item. If no line is set up for the currency of the line or item, the auto cost won't be applied to that line or item.

For other types of cost areas, all lines on the **Lines** FastTab will apply to each voyage, shipping container, folio, or transfer order line that matches the values that are established on the header.

The following table describes all the fields that can appear on each line. However, the specific fields that are available vary, depending on the cost area that is currently selected.

| Field | Description |
|---|---|
| **Currency** | Select the currency that the line applies to. This currency is related to the purchase order. When the system is trying to find the auto costs that should be applied to a voyage and its voyage lines, it will select the line that has the same currency as the purchase order. This field is available only when the **Cost area** field is set to *Purchase order* or *Item*. |
| **Cost type code** | The cost type. |
| **Apportionment method** | <p>The method that is used to distribute costs to lines. The following options are available:</p><ul><li><p>**Percent** – The value of the **Cost value** field is a percentage that applies to the total value of goods.</p><p>For example, if the **Cost value** field is set to *10*, and the total value of goods is $800, the cost value is $80 (= $800 × 10 percent).</p></li><li>**Quantity** – The cost will be apportioned based on the quantity of goods.</li><li>**Amount** – The cost will be apportioned based on value of the goods.</li><li>**Volume** – The cost will be apportioned based on the volume of goods. Volume is specified on the item master.</li><li>**Weight** – The cost will be apportioned based on the weight of goods. Weight is specified on the item master.</li><li>**Volumetric** – The cost will be apportioned based on the volumetric measurement of goods.</li><li><p>**Measurement** – This option enables a measurement to be specified in the **Landed cost** module. It's often used by organizations that don't know the individual volume or weight of the goods, but that require a more accurate apportionment than the **Amount** and **Quantity** options allow for. The freight forwarder or agent will provide the organization with the weight or cubic measurement, at either the item level or the purchase order level.</p><p>For example, sea freight equals $900. Item A has a weight of 800 kilograms (kg) and a volume of 2 cubic meters (m³). Item B has a weight of 100 kg and a volume of 1 m³. Here are the results when the costs are apportioned by weight:</p><ul><li>Item A = $800</li><li>Item B = $100</li></ul><p>Here are the results when the costs are apportioned by volume:</p><ul><li>Item A = $600</li><li>Item B = $300</li></ul><p>**Note:** When the **Apportionment method** field is set to *Measurement*, the system uses the measurements that are entered for both the cost area (the shipping container) and the lines. These measurements don't necessarily have to add up to the expected total. However, if you require that they add up to the expected total, you can do a check by using the statistics to review the total measurement. The measurement prompt setting and automatic update of the measurement at the shipment or container level are set on the voyage header.</p></li></ul> |
| **From date** | Specify the start of the date range for costing, if there is a range of dates. This date is the first date when the auto cost will apply. |
| **To date** | Specify the end of the date range for costing, if there is a range of dates. This date is the last date when the auto cost will apply. |
| **Category** | <p>Select the method that should be used to calculate cost. The following options are available:</p><ul><li>**Fixed** – Cost will be apportioned based on the apportionment method.</li><li>**Pieces** – Cost will be allocated per piece. Therefore, the apportionment method won't be used.</li><li>**Percent** – A percentage of the goods' value will be added. Therefore, the apportionment method won't be used.</li><li>**Rate** – Select this option if there are quantity breakdowns. The **Apportionment method** field for the line must be set to *Measurement*.</li><ul> |
| **Broken by quantity** | <p>Select this check box to make the **Quantity breaks** button available on the **Lines** FastTab. Quantity breaks enable the cost to be broken down and the different costs to vary, depending on the quantity on the purchase order line of the voyage. This functionality is often used when the mode of delivery is air. The **Category** field for the line must be set to *Rate*.</p><p>The quantity pertains to the option that is selected in the **Apportionment method** field. The cost value will be up to the quantity that is entered in the **Cost value** field.<p>For example, quantities of 45–100 kg produce a charge of $6.00 per measurement (such as kg/m³). Quantities that exceed 100 kg produce a charge of $5.50 per measurement (such as kg/m³).</p> |
| **Cost value** | Enter the value of the cost. |
| **Cost currency code** | Select the currency of the cost. |
| **Item sales tax group** | Select the tax code for the cost. |
| **Minimum cost** | <p>This field applies only if the **Broken by quantity** check box is selected. If the measurement doesn't reach this value, the minimum value is selected, regardless of the costs that are specified on the **Quantity breaks** page.<p>For example, quantities of 0–45 kg produce a charge of $6 per measurement (kg/m³). Quantities of 46–100 kg produce a charge of $5.50 per measurement (kg/m³). If 2 kg are shipped, the quantity break will create a cost value of $12. However, if the **Minimum cost** field is set to *$100*, the final cost will be $100.</p> |
| **Aggregate** | Select this check box to allow users to move this cost from the shipping container level to the voyage level. In this case, costs can automatically be calculated at the shipping container level. However, they can also be combined and apportioned across all items in all the containers on a voyage, instead of all items in the individual shipping containers. |
| **Linked cost type** | <p>Link the current line to another line in the same auto cost record by specifying the **Cost type code** value of the line that you want to link to. This functionality is available only when **Category** field for the current line is set to *Percent*. When the current line is linked to another line, the cost of the current line will be based on the cost of the other line.</p><p>For example, freight is $1,000, and you want the fuel surcharge to be 10 percent of the freight cost. In this case, the line must have a **Category** value of *Percent*, a **Cost value** value of *10%*, and a **Linked cost type** value of *Freight*.</p> |
| **Value adjustment** and **Adjustment amount** | <p>Use these fields to adjust the value and amount for various percentage values. They are available only when the **Cost area** field is set to *Item*.</p><p>Different costing can be set up for different components of an item. One component of an item might have a different cost percentage than the other components of that item. This approach is sometimes required to value a specific portion of the goods at different rates.</p><p>For example, duty for a watch is calculated at two rates: one component of the watch has a 10-percent duty rate, and a second component has a 2-percent duty rate. In this case, costing will be split between the two components.</p><p>The cost is calculated for the item, but the cost value is adjusted by the value of the components that have the different cost category. The cost of the remaining components can then be calculated by using the amount that the previous calculation was adjusted by.</p><p>For example, component A of the watch has a cost of $9.50 and a duty of 10 percent, and component B has a cost of $0.50 and a duty of 2 percent. Therefore, the total cost is $10.00. The first entry is for the 10-percent line. It uses the following values:</p><ul><li>**Category:** *Percent*</li><li>**Cost value:** *10*</li><li>**Value adjusted:** *Adjust by*</li><li>**Adjusted value:** *-0.50*</li></ul><p>This setup specifies that the cost of the item ($10) must be reduced by $0.50 (the price of component B) before a 10-percent duty charge is calculated. Therefore, 10 percent will be applied to $9.50.</p><p>The second entry is for the 2-percent line (the $0.50 that the previous entry was adjusted by). It uses the following values:</p><ul><li>**Category:** *Percent*</li><li>**Cost value:** *2*</li><li>**Value adjusted:** *Use*</li><li>**Adjustment:** *0.50*</li></ul><p>This setup calculates the remaining duty that is payable on component B.</p> |
