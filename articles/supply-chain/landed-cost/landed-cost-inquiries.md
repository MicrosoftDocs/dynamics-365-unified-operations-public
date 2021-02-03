---
# required metadata

title: Landed cost inquiries
description: This topic describes how to find and use the various types of inquiries available for the Landed cost module.
author: RichardLuan
manager: tfehr
ms.date: 02/01/2021
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
ms.search.validFrom: 2021-02-21
ms.dyn365.ops.version: Release 10.0.17
---

# Landed cost inquiries

[!include [banner](../includes/banner.md)]

## Voyage line inquiries

This inquiry shows all voyage lines as they pertain to inventory. This can be useful as a filter to locate an item, purchase order, or other useful piece of information. It can also be used to identify the expected delivery date of an item that may be on one or more voyages, which can help you to manage expected inventory receiving.

To open the **Voyage lines** inquiry page, go to **Landed cost \> Inquiries \> Voyage lines**.

<!-- KFM: What about the "Cost inquiry" action? -->

### The Overview tab

The **Overview** tab shows a grid with basic information about each relevant voyage line. The following table describes each column shown here.

| Column | Description |  
| --- | --- |
| **Item number** | Identifies the item for this voyage line. |
| **Reference** | Identifies the type of order (purchase order or transfer order) |
| **Number** | The order number (purchase order or transfer order).  |
| **Folio** | Identifies the folio associated with the voyage line. |
| **Shipping container** | Identifies the shipping container associated with the voyage line. |
| **Voyage** | Identifies the voyage associated with the voyage line. |
| **Quantity** | The quantity of the item for this voyage line. |
| Other dimensions | You can choose to show columns for additional dimensions as needed, such as batch number, inventory status, warehouse, and more. On the Action Pane, select **Inventory \> Display dimensions** to open a dialog box where you can choose which dimensions to include. |

### The General tab

Open the **General** tab to see more information about the line currently selected on the **Overview** tab.

### The Dimensions tab

Open the **Dimensions** tab to see values for all available dimensions for the line currently selected on the **Overview** tab, regardless of which dimensions you have chosen to show on that tab.

## Cost estimate inquiries

Each time you generate a cost estimate, the estimate gets added to the **Cost estimates** inquiry page. For complete details about how to generate, view, and work with cost estimates (including on the inquiries page), see [Estimate and manage landed costs](estimate-manage-landed-costs.md).

## Item tracking

Use the **Item tracking** page to view open purchase orders lines and their current status. They do not need to be attached to a voyage to appear here. If an item is associated with a voyage, the voyage ID will show in the item tracking record line. To open this page, go to **Landed cost \> Inquiries \> Tracking \> Item tracking**.

Because your system probably contains a very large number of purchase order lines, this page initally shows now records. Start by using the filter fields at the top of the page to define the set of puchase order lines you are looking for. Then select **Update** on the Action Pane to generate the list. You can use an asterisk (\*) as a wildcard character in any of these fields. For example, to find all purchase order lines for items with the word "DVD" in their name, set **Type** to **Product name** and enter *\*DVD\** in the **FIeld value** field.

> [!NOTE]
> Currently backorders only include only sales orders. Sales quotations are not shown or considered backorders.

The following table describes each column shown on the **Item tracking** page.

| Column | Description |
| --- | --- |
| **To port** | The final destination. |
| **Confirmed** | The confirmed date of the purchase order line. |
| **Delivery Date** | The delivery date of the purchase order line. |
| **Voyage** | Identifies the voyage associated with this line (if any). |
| **Shipping Container** | If the line is attached to a shipping container, the container ID will be shown here. |
| **Shipping port** | This is the current port as per the first leg within the tracking form that does not have an actual date set for the shipping container associated with this purchase order line. |
| **Activity** | This is the current activity as per the first leg within the tracking form that does not have an actual date set for the shipping container associated with this purchase order line. |
| **Estimated end date** | Shows the date that the voyage is expected to be received at the destination warehouse. |
| **Name** | The name of the vendor. |
| **Voyage Status** | The shipment status attached to the purchase order line. |
| **Item number** | The item number for this purchase order line. |
| **External** | The vendor's item name. |
| **Product Name** | The name of the item for this purchase order line. |
| **Quantity** | The purchase order line quantity for this purchase order line. |
| **Unit** | The unit of measure for this purchase order line. |
| **Reference** | Identifies the type of order (purchase order or transfer order) |
| **Reference number** | The order number (purchase order or transfer order).  |
| **Backorder** | If this shows an icon, that indicates that there are sales backorders for this item. |
| Other dimensions | You can choose to show columns for additional dimensions as needed, such as batch number, inventory status, warehouse, and more. On the Action Pane, select **Display dimensions** to open a dialog box where you can choose which dimensions to include. |

### Related information about backorders

To see more information about backorders, expand the **Related information** tab on the right side and then select **Backorders**. You can select a row here and then select the **More** link to see even more information about a backorder 

## Individual shipping container tracking

This inquiry provides a filter that enables you to find a shipping container and then identify all of the voyage lines within that container.

To open this inquiry, go to **Landed cost \> Inquiries \> Tracking \> Individual shipping container tracking**.

## Multiple shipping container tracking

This inquiry provides a filter that enables you to find a collection of shipping containers and then identify all of the voyage lines within those containers.

To open this inquiry, go to **Landed cost \> Inquiries \> Tracking \> Multiple shipping container tracking**.

