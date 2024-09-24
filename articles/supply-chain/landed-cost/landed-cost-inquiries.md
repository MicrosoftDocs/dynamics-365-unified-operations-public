---
title: Landed cost inquiries
description: Learn how to find and use the various types of inquiries that are available for the Landed cost module with a table that defines various columns.
author: Weijiesa
ms.author: weijiesa
ms.topic: article
ms.date: 02/01/2021
ms.custom:
ms.reviewer: kamaybac
ms.search.form: ITMLine, ITMItemTracking, ITMContainerActivityTracking, ITMContainerTracking
---

# Landed cost inquiries

[!include [banner](../../includes/banner.md)]

## Voyage line inquiries

The **Voyage lines** inquiry shows all voyage lines as they pertain to inventory. This inquiry can be used as a filter to help you find an item, purchase order, or other useful piece of information. It can also be used to identify the expected delivery date of an item that might be on one or more voyages. In this way, it can help you manage expected inventory receiving.

To open this inquiry, go to **Landed cost \> Inquiries \> Voyage lines**.

### Overview tab

The **Overview** tab of the **Voyage lines** inquiry page includes a grid that shows basic information about each relevant voyage line. The following table describes the columns in the grid.

| Column | Description |
|---|---|
| **Item number** | The item for the voyage line. |
| **Reference** | The type of order (purchase order or transfer order). |
| **Number** | The purchase order number or transfer order number. |
| **Folio** | The folio that is associated with the voyage line. |
| **Shipping container** | The shipping container that is associated with the voyage line. |
| **Voyage** | The voyage that is associated with the voyage line. |
| **Quantity** | The quantity of the item for the voyage line. |
| (Other dimensions) | You can show columns for additional dimensions as you require. Those dimensions include batch number, inventory status, and warehouse. On the Action Pane, select **Inventory \> Display dimensions** to open a dialog box where you can select the dimensions to include. |

### General tab

Select the **General** tab to view more information about the line that is currently selected on the **Overview** tab.

### Dimensions tab

Select the **Dimensions** tab to view values for all available dimensions for the line that is currently selected on the **Overview** tab, regardless of the dimensions that you've selected to show on that tab.

## Cost estimate inquiries

Every time that you generate a cost estimate, the estimate is added to the **Cost estimates** inquiry page. For complete details about how to generate, view, and work with cost estimates (including estimates on the inquiry page), see [Estimate and manage landed costs](estimate-manage-landed-costs.md).

## Item tracking

Use the **Item tracking** page to view open purchase orders lines and their current status. Lines don't have to be associated with a voyage to appear here. However, if an item is associated with a voyage, the item tracking record line shows the voyage ID.

To open this page, go to **Landed cost \> Inquiries \> Tracking \> Item tracking**.

Because your system probably contains a very large number of purchase order lines, the **Item tracking** page initially shows no records. Start by using the filter fields at the top of the page to define the set of purchase order lines that you're looking for. Then select **Update** on the Action Pane to generate the list. You can use an asterisk (\*) as a wildcard character in any of the filter fields. For example, to find all purchase order lines for items that include the word "DVD" in their name, set the **Type** field to **Product name**, and enter *\*DVD\** in the **Field value** field.

> [!NOTE]
> Currently, backorders include only sales orders. Sales quotations aren't shown or considered backorders.

The following table describes the columns in the grid on the **Item tracking** page.

| Column | Description |
|---|---|
| **To port** | The final destination. |
| **Confirmed** | The confirmed date of the purchase order line. |
| **Delivery Date** | The delivery date of the purchase order line. |
| **Voyage** | If the line is associated with a voyage, the voyage ID. |
| **Shipping Container** | If the line is attached to a shipping container, the container ID. |
| **Shipping port** | The current port, based on the first leg in the tracking form where no actual date is set for the shipping container that is associated with the purchase order line. |
| **Activity** | The current activity, based on the first leg in the tracking form where no actual date is set for the shipping container that is associated with the purchase order line. |
| **Estimated end date** | The date when the voyage is expected to be received at the destination warehouse. |
| **Name** | The name of the vendor. |
| **Voyage Status** | The shipment status that is attached to the purchase order line. |
| **Item number** | The item number for the purchase order line. |
| **External** | The vendor's item name. |
| **Product Name** | The name of the item for the purchase order line. |
| **Quantity** | The purchase order line quantity for the purchase order line. |
| **Unit** | The unit of measure for the purchase order line. |
| **Reference** | The type of order (purchase order or transfer order) |
| **Reference number** | The purchase order number or transfer order number. |
| **Backorder** | A symbol indicates that there are sales backorders for the item. |
| (Other dimensions) | You can show columns for additional dimensions as you require. Those dimensions include batch number, inventory status, and warehouse. On the Action Pane, select **Display dimensions** to open a dialog box where you can select the dimensions to include. |

### Related information about backorders

To view more information about backorders, select the **Related information** tab on the right side of the page, and then select **Backorders**. To view even more information about a specific backorder, select the row for it, and then select the **More** link.

## Individual shipping container tracking

The **Individual shipping container tracking** inquiry provides a filter that lets you find a shipping container and then identify all the voyage lines in that container.

To open this inquiry, go to **Landed cost \> Inquiries \> Tracking \> Individual shipping container tracking**.

## Multiple shipping container tracking

The **Multiple shipping container tracking** inquiry provides a filter that lets you find a collection of shipping containers and then identify all the voyage lines in those containers.

To open this inquiry, go to **Landed cost \> Inquiries \> Tracking \> Multiple shipping container tracking**.
