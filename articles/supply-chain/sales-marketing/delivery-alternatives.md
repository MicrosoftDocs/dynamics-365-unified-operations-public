---
title: Delivery alternatives
description: Learn how sales order takers can use the Delivery alternatives page to discover alternative order fulfillment options, including a step-by-step process.
author: kamaybac
ms.author: adpattanaik
ms.topic: article
ms.date: 04/10/2017
ms.reviewer: kamaybac
ms.search.form: SalesLineDeliveryDetails
ms.assetid: 527f6084-44fe-41bb-924f-4386e926358a
---

# Delivery alternatives

[!include [banner](../includes/banner.md)]

Sales order takers can use the **Delivery alternatives** page to discover alternative order fulfillment options.

The **Delivery alternatives** page layout gives an overview of all alternative options. It also lets order takers look beyond the current company for fulfillment opportunities. They can now view both intercompany opportunities and opportunities from external vendors. By sorting the options by delivery date, sales order takers can view an intelligent list of delivery alternatives. In addition, parameters help them better manage the suggested deliveries. Because transport time can affect delivery dates, sales order takers can explore the various transportation choices that carriers offer. Because detailed information is shown for each suggestion, order takers can make informed decisions directly from the **Delivery alternatives** page.

## Open the Delivery alternatives page

You can open the **Delivery alternatives** page from the sales order line.

1. Select **Products and supply \> Delivery alternatives**.
1. Select **Line details \> Delivery \> Delivery alternatives.**

You can also open the **Delivery alternatives** page by opening the **Sales order processing and inquiry** workspace, and then selecting **Orders and favorites \> Delayed order lines \> Delivery alternatives** **Note:** You can open the **Delivery alternatives** page only if both the following conditions are met:

- All mandatory sales line information is filled in.
- The **Delivery date control** field is set to a value other than **None**.

## Delivery date control methods

The delivery date control method determines how the system establishes delivery dates, how delivery alternatives are calculated, and what information is shown. Note that delivery date control takes calendars into consideration. Therefore, the following calendars can affect the suggested receipt date: Warehouse calendar, Transport calendar, Vendor calendar, and Customer calendar. The following table describes each method for delivery date control.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><strong>Method</strong></td>
<td><strong>Description</strong></td>
</tr>
<tr class="even">
<td><strong>None</strong></td>
<td><ul>
<li>Delivery alternatives for sales lines aren't supported. This option turns off delivery date control.</li>
</ul></td>
</tr>
<tr class="odd">
<td><strong>Sales lead time</strong></td>
<td><ul>
<li>Delivery alternatives are calculated based on the predefined sales lead time. The transport days are calculated based on the mode of delivery.</li>
<li>Delivery alternatives include warehouses that have on-hand inventory, and supply/demand orders.</li>
</ul></td>
</tr>
<tr class="even">
<td><strong>ATP</strong></td>
<td><ul>
<li>Delivery alternatives are calculated based on available to promise (ATP) logic. The current availability and expected future availability are considered. The transport days are calculated based on the mode of delivery.</li>
<li>Delivery alternatives include warehouses that have on-hand inventory, and supply/demand orders.</li>
</ul></td>
</tr>
<tr class="odd">
<td><strong>ATP + Issue margin</strong></td>
<td><ul>
<li>Delivery alternatives are calculated as for the ATP method, but the issue margin is included in the calculation.</li>
</ul></td>
</tr>
<tr class="even">
<td><strong>CTP</strong></td>
<td><ul>
<li>Delivery alternatives are calculated based on the capable to promise (CTP) logic. MRP explosion is used to determine availability. Note that, at a minimum, CTP offsets delivery dates to the sales lead time. The transport days are calculated based on the mode of delivery.</li>
<li>Delivery alternatives include suggestions for the following warehouses:
<ul>
<li>Current warehouse</li>
<li>Default warehouse</li>
<li>All warehouses that have available on-hand inventory</li>
<li>All warehouses that have supply orders</li>
<li>All warehouses that have active bill of materials (BOM) versions</li>
</ul></li>
</ul></td>
</tr>
</tbody>
</table>

## View information about delivery alternatives

This section describes the information about delivery alternatives that is available on each FastTab of the **Delivery alternatives** page.

### The Product FastTab

This FastTab shows a summary of the product and details of the current sales line.

### The Delivery alternatives FastTab

This FastTab shows a list of delivery alternatives that is sorted by receipt date. Above the list, you can select which options to base the suggestions on. You can also select the mode of delivery, which determines the transport days. The following options are available:

- **Include other product variants** - This option is available for products that have product variants. It will include delivery alternatives for other variants of the product. This option isn't available for CTP.
- **Include partial quantity** - By default, only suggestions that fulfill the full quantity of the sales line are included. Select this option to include suggestions that only partially fulfill the order line. This option is useful when the customer requests an earlier delivery date and accepts partial delivery.
- **Include later dates** - By default, only suggestions that are better (earlier) than the current dates on the sales line are shown. Select this option to include later dates. This option can be useful in situations where parameters other than the date have priority. For example, a specific vendor or warehouse might be preferred.
- **Mode of delivery** - Select the preferred mode of delivery to optimize transport time and cost. You will immediately see the effect on the suggested delivery alternatives. Therefore, it's easy to compare the alternatives.
- **Include procurement** - When procurement is selected, the suggested delivery alternatives include options to procure from both external vendors and other companies in the enterprise (intercompany). The **Include procurement** option is supported for ATP and ATP + Issue margin delivery date control. Procurement options from the default purchase vendor for the product and all approved vendors for the product are included.
- For external vendors, the calculation is based on the purchase lead time.
- For intercompany, the calculation considers what is available from the sourcing company, based on delivery date control in the sourcing company.
- **Delivery type** (Relevant for procurement)
  - **Stock** - Products are shipped from the sourcing warehouse to the site/warehouse on the sales line. They are then shipped from that warehouse to the customer.
  - **Direct delivery** - Products are shipped directly from the sourcing warehouse to the customer.

### The Availability information FastTab

Information on this FastTab is related to the delivery alternative line that is selected. The following information is shown, depending on the delivery date control for the sales line:

- **Sales lead time**
  - **Available today** - Show the current physical on-hand, physical reserved, and available physical inventory.
  - **Parameters** - Show the inventory unit and sales lead time.

- **ATP and ATP + Issue margin**
  - **Available today** - Show the current physical on-hand, physical reserved, and available physical inventory.
  - **Parameters** - Show the inventory unit and sales lead time.
  - **Future availability** - Show a graphical representation of current and future availability for the selected site and warehouse under **Delivery alternatives**. You can select the chart columns to see more detailed information about the future availability of the product. The slider shows a list of relevant demand and supply orders within the ATP time fence.

- **CTP**
  - **Available today** - Show the current physical on-hand, physical reserved, and available physical inventory.
  - **Parameters** - Show the inventory unit and sales lead time.
  - **Explosion** - Show a supply explosion of the selected delivery alternative. You can use **Setup** to change the fields and inventory dimensions that are shown in the explosion.

### The Impact of selected alternative FastTab

This FastTab highlights the impact of the selected delivery alternative. If you select **OK**, the sales line is updated with the highlighted values in the SELECTED columns. Note that, if the quantity on the selected delivery alternative is less than quantity on the sales line, a delivery schedule is created, and the order line is split into two lines: one line for the selected quantity and one line for the remaining quantity. You can also update the commercial line so that it matches the schedule lines and affects the pricing.

## Related information

[Order promising](delivery-dates-available-promise-calculations.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]