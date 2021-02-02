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

To sort or filter the grid according to the values of any column, select the column header to open a drop-down dialog box and then choose a filter or sorting option.

To add or remove extra dimensions to the grid, select **Inventory \> Dimensions display** on the Action Pane. This opens the **Dimension display** dialog box, where you can select or deselect check boxes for each available dimension as needed.

<!-- KFM: What about the "Cost inquiry" action? What about the other two tabs here? -->

## Cost estimate inquiries

<!-- KFM: This section does not describe the UI at all. What is this? -->

<!-- KFM: Start by summarizing the purpose of the page. -->

The overview tab shows the cost estimates; the costs tab shows the breakdown of a cost estimate. The cost estimate inquiry form can additionally be used to modify cost estimates and used as a worksheet before the cost price is updated for the items within the estimate.

The open the **Cost estimates** page, go to **Landed cost \> Inquiries \> Cost estimates**.

To populate or update the **Cost estimates** page, run the periodic cost estimates process. <!-- KFM: how do I do this? -->

| Setting | Description |
| --- | --- |
| **Cost Estimate Number** | The Id for this cost estimate |
| **Cost Template** | The template that was used to derive this cost |
| **Estimate Date** | The date that the exchange rate used, if applicable |
| **From Port** | The from port used to derive the cost |
| **To Port** | The to port used to derive the cost |
| **Measurement** | The measurement used to derive the cost |
| **Estimated Landed Cost** | The total landed cost value in the system currency |
| **The Cost Tab** | The costs tab shows all the costs that have been found to determine the price |
| **Cost Area** | 1 of 5 areas where the auto-cost was found |
| **Code Type Code** | The name of the cost |
| **Apportionment Method** | How the cost is apportioned – see apportionment methods section above to understand these |
| **Category** | What category the cost has – see category section above to understand these |
| **Cost Value** | The cost value in the expected currency for this cost |
| **Estimated Cost** | The estimated cost for this cost type, this is shown in the system currency |
| **Currency** | The currency of the cost value |
| **Exchange Rate** | If the currency is not the same as the system currency the exchange rate will be useful and is shown here |
| **Vendor Account** | The vendor account used, if applicable |
| **Item Number** | The item number is shown here |
| **Site** | The site is shown here |
| **Quantity** | The number of items used to determine the cost |
| **Cost Price** | The cost price (trade agreement) shown in local currency |
| **Measurement** | The individual measurement is shown here |
| **Estimated Landed Cost** | The estimated landed cost for the total quantity |
| **Per Unit** | The estimated landed cost divided by the quantity |
| **Cost Tab** | Costs tab shows all the purchase line shipment costs that have been found to determine the landed cost. |

## Landed inquiry

<!-- KFM: I don't understand any of this. What is going on here? -->

Select the **Cost inquiries** form to review the voyage costs associated to the inventory items on this estimate. Only those voyage costs that are associated to the debit transaction type of *Item* will be listed in the voyage costs on the estimate costs form. The cost type codes that do not have a debit type of *Item* will not be listed, as they are not included in the inventory cost associated to the item. Rather they are an additional overhead landed cost that is posted to a ledger account. The item cost type codes associated to the debit of ledger are managed through the auto costs form and can be viewed by going directly to the voyage form.

## Item tracking

Use the **Item tracking** page to view open purchase lines and their current status. They do not need to be attached to a voyage to appear here. If the item is associated to a voyage, the voyage ID will show in the item tracking record line. The item tracking form can be viewed by navigating to _Landed cost \> Inquiries \> Tracking \> Item tracking._

A filter option is selected and standard wildcards can be used in the value field. For example, if all purchase lines for items with the word television contained within it, select the Item name filter and enter \*DVD\* in the value field.

The customer account can be selected to show only those items which are on backorder for a particular customer. The backorders tab will show all other customers in addition to the filtered customer.

Note: Currently a backorder are only sales orders, sales quotations are not shown or considered a back order as they are within standard Dynamics 365 Finance and Operations, Enterprise Edition.

### Overview tab

| Setting | Description |
| --- | --- |
| **To Port** | This refers to the final destination. |
| **Confirmed** | The confirmed date field from the purchase order line. |
| **Delivery Date** | The delivery date field from the purchase order line. |
| **Voyage** | <!-- KFM: Description needed --> |
| **Shipping Container** | If the line is attached to a shipping container, the container Id will be shown here. |
| **Shipping port** | This is the current port as per the first leg within the tracking form that does not have an actual date set for this shipping container. |
| **Activity** | This is the current activity as per the first leg within the tracking form that does not have an actual date set for this shipping container. |
| **Estimated end date** | <!-- KFM: Description needed --> |
| **Name** | The name of the vendor. |
| **Voyage Status** | The shipment status which is attached to the purchase order line. |
| **Item number** | The item ID. |
| **External** | The vendor's item name. |
| **Product Name** | The name of the Item. |
| **Quantity** | The purchase order line quantity for this item. |
| **Unit** | The unit of measure for this purchase order line. |
| **Reference** | <!-- KFM: The purchase order number? --> |
| **Reference number** | <!-- KFM: This is seal number entered on the shipping container? --> |
| **H.A.W.B/Bill of Lading** | This is the number entered on the shipping container. |
| **Backorder** | If this shows an icon, it is indicating that there are sales backorders for this item. |

### Backorders tab

This tab shows any sales orders that are open. The sales Id, customer account number, quantity (Shown as a negative as this information is seen from the inventory point of view, i.e. A sale is a negative), expected date of delivery.
