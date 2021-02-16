---
# required metadata

title: Manage shipping containers
description: This topic describes how to work with shipping containers. Shipping containers are used to group together goods that are physically grouped together. They are also used in cases where costs must be shared only across those goods, usually because they are physically together.
author: RichardLuan
manager: tfehr
ms.date: 12/14/2020
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
ms.author: riluan
ms.search.validFrom: 2020-12-14
ms.dyn365.ops.version: Release 10.0.17
---

# Manage shipping containers

[!include [banner](../includes/banner.md)]

Shipping containers are used to group together goods that are physically grouped together. They are also used in cases where costs must be shared only across those goods, usually because they are physically together.

To view and process goods through the shipping container page, go to **Landed cost \> Shipping containers \> All shipping containers**. The **All shipping containers** page shows a list of all available shipping containers. Select a container to view its details.

The upper part of the shipping container details page shows shipping container and costing information. The **Lines** section shows the folios, items, and purchase orders or transfer orders that are attached to the container.

## Header view

### Settings on the General FastTab

| Field | Description |
|---|---|
| Shipping container type | Enter the shipping container type. This field must be set. You can use it to determine the cost for freight, for example, by selecting the auto cost that is associated with the shipping container type. |
| Vessel | Enter or select the vessel. If the vessel isn't listed as a value, you can enter the vessel ID as free text. In that case, the main table isn't updated so that the vessel ID can be selected in this field later. For more information, see [Vessels](shipping-information-setup.md#vessels). |
| Unit type | Unit types are used as an additional means of grouping and identifying shipping containers. They are shown and selected on the shipping container page. For more information, see [Set up unit types](shipping-container-setup.md#unit-types). |
| Refrigeration type | Refrigeration types are used as an additional means of grouping and identifying shipping containers, usually refrigerated containers. They are shown and selected on the shipping container page. For more information, see [Set up refrigeration types](shipping-container-setup.md#refrigeration-types). |
| Measurement | This field enables a measurement to be specified in the **Landed cost** module. Measurements are often used by organizations that don't know the individual volume or weight of goods, but that require a more accurate apportionment than the amount or quantity provides. The freight forwarder will provide the weight in kilograms or the cubic measurement, and you can put it at the level of either an item or the purchase order. It can be automatically updated if the parameter is selected, or it can be manually entered. |
| Measurement unit | The unit of measure that applies to the number in the **Measurement** field. |
| Actual weight | You can record the actual weight of the carton or container. This value can be used for verification against the maximum weight that is allowed in the setup of a shipping container. |
| Number of cartons | The number of cartons is automatically updated if the parameter is selected. |
| Description of goods | A description of goods can be selected on the shipping container or folio header. It's used to help identify a voyage, shipping container, or folio of goods. For more information, see [Description of goods](shipping-information-setup.md#description-of-goods). |
| H.A.W.B/Bill of lading | You can specify the house air waybill or bill of lading for the shipping container. |
| Remarks | Additional information that is related to the shipping container. |

### Settings on the Delivery FastTab

| Field | Description |
|---|---|
| Created date and time | The date and time when the container was created. |
| Ex-factory date | This date is usually provided to the factory/vendor to indicate when you expect the goods to leave its premises. When you work with a factory in Asia, this date is often required instead of the date that you expect the goods by. (By contrast, for a local delivery, the date that you expect the goods by is required.) This field can be filled in from the purchase order lines in the shipping container list. You can also manually enter it here. |
| Ship date | This date can be printed on the purchase order document. It usually informs the factory/vendor about the date that the goods should be delivered to the port by. This field is for informational purposes only. It isn't used to estimate the expected delivery date of the goods in the shipping container. This field can be set to that it's automatically updated when the tracking control page is updated. |
| Estimated delivery date | Usually, the date when the goods are due to arrive in the warehouse. This field is for informational purposes only. It isn't used to calculate master planning on the purchase order lines in the shipping container. The expected delivery date on the purchase order lines is updated through tracking control. This field can be set up so that it's updated when the tracking control page is updated. |
| Departure date | Usually, the date when the plane or vessel actually leaves the overseas port. |
| Estimated time of arrival at port | The estimated arrival date at the destination port ("to" port). |
| Original documents received | Optional: Update the date when the original documents were received. |
| Broker advised | Optional: Update the date when the broker was advised. |
| Original bill of lading sent | Optional: Update the date when the original bill of lading was sent. |
| Goods released | Optional: Update the date when the goods were released. |
| Customer appointment | Optional: Update the customer appointment date. |
| Delivered at warehouse | Optional: Update the date when the goods were delivered to the warehouse. |
| Verification date | Optional: Update the verification date. |
| Delivery instructions | Optional: Update the date of the delivery instructions. |
| Local forwarder | This field is for informational purposes only. The local forwarder should be selectable from the vendor table. |
| Local transport date | Enter the date that the local transport is booked for. This field can help the warehouse do its planning. |
| Local transport time | Enter the time slot. This field can help the warehouse do its planning. |
| Journey template | The journey template that is specified for the voyage. The journey template provides the details of the "to" and "from" ports, and the lead times that are associated with the tracking control of the shipping container. |

### Buttons

| Button | Description |
|---|---|
| New | Create a voyage. <!-- KFM: For more information about the voyage creation process, see the scenario documentation. --> |
| Delete | Delete a voyage. Only voyages that have a status of *Confirmed* can be deleted. After a voyage has begun the goods-in-transit process, it can no longer be deleted. |
| Voyage costs | View or add voyage costs to all the goods in the shipping container. Voyage costs that are manually added on the shipping container page apply only to the items in the shipping container, not to the whole voyage. Therefore, users can add shipping container–level costs to a voyage if they were missed during auto cost creation. All voyage costs that are associated with the shipping container will be shown, regardless of the cost code type definition. |

### Buttons on the Manage tab

| Button | Descriptions |
|---|---|
| Post receipts list | Post a receipt list, or view the product receipt lists for all purchase order lines in the shipping container. If multi-company shipments are used, a new receipts list posting dialog box is opened for each company. |
| Product receipt | View the product receipt record, if it's used. |
| Invoice | Post an invoice for all purchase order lines in the shipping container. If multi-company shipments are used, a new invoice posting dialog box is opened for each company. |
| Ship transfer order | Post a transfer order shipment for all transfer order lines in the shipping container. Only those lines in the shipping container that are a type of transfer order appear in the dialog box. |
| Receive | Post a transfer order receipt for all transfer order lines in the shipping container. The receive dialog box is the simplest way to receive goods in a shipping container or voyage, and is one of three available options. You can also receive via arrival journals or mobile device processing. |
| Receive in transit | Receive all order lines that are in transit in the shipping container. The receive dialog box is the simplest way to receive goods in a shipping container or voyage, and is one of three available options. You can also receive via arrival journals or mobile device processing. |
| Find auto costs | <p>Find relevant voyage costs for the shipping container. If the voyage costs have already been found or updated, you receive the following message: "Un-invoiced cost lines exist. Do you want to overwrite them?"</p><p>**Note:** Voyage costs that are attached to a shipping container and that have been invoiced won't be overwritten.</p> |
| Create arrival journal | You can generate an arrival journal for organizations by using advanced warehouse features. The options are _Initialize quantity_ (recommended), and either _Create from goods in transit_ or _Create from purchase orders_. The last two options depend on whether goods-in-transit processing is being used. |
| Accrue costs | You can accrue costs where a cost type has a ledger account specified for the debit. This button is typically used when the stock is in transit, or when goods have been received and invoiced. |
| Rename | Select this button to open a dialog box where you can rename a selected shipping container. |
| Change journey template | Change the journey template. After you change the journey template, you might have to select **Find auto costs** or manually add costs again, because the shipment costs will be deleted. |

### Buttons on the General tab

| Button | Descriptions |
|---|---|
| Receipts list | Post a receipt list for all purchase order lines in the shipping container. If multi-company voyages are used, a new receipt list posting dialog box is opened for each company. |
| Product Receipt | View the product receipt record, if it's used. The product receipt process will be used only if the goods don't use goods-in-transit functionality. |
| Item arrival | View the item arrival journal for the shipping container, if that journal is used. |
| Legs | Legs are used to identify separate parts of a journey. Lead times can be associated with each leg to help with shipment tracking. For more information, see [Multi-leg journey setup](multi-leg-journey-setup.md). |
| Tracking | View or update shipment tracking. |
| Costs inquiry | You can use the **Costs inquiry** page to view all the costs of a shipping container, including the container, folio, and purchase order. You can adjust the exact view of the page by using the **View** button. On the **Costs inquiry** page, you can view any of the areas, plus the item and cost type code. By removing these items, you can adjust the page by grouping together costs. This capability can be useful if you're using sizes and colors. You can change the dimensions that are shown on the **Costs inquiry** page. The costs page shows only cost type codes where the **Dr** entry on the **Posting** tab is set to *Item*. |
| Goods in transit orders | You can open the **Goods in transit** page directly from the container. That page shows the goods-in-transit records for the selected shipping container only. |
| Over/under transactions | You can open the **Over/Under transactions** page directly from the shipping container. That page shows the over/under records for the selected shipping container only. The over/under transactions will be available only after the goods have been received in the warehouse and the goods-in-transit order has been closed for further receiving. |

## Line view

### Settings

| Field | Description |
|---|---|
| Measurement | This field enables a measurement to be specified in the **Landed cost** module. Measurements are often used by organizations that don't know the individual volume or weight of goods, but that require a more accurate apportionment than the amount or quantity provides. The freight forwarder will provide the weight in kilograms or the cubic measurement, and you can put it at the level of either an item or the purchase order. It can be automatically updated if the parameter is selected, or it can be manually entered. |
| Measurement unit | The unit of measure that is related to the number in the **Measurement** field. |
| Number of cartons | The number of cartons is automatically updated if the parameter is selected. |

### Buttons

| Button | Description |
|---|---|
| Remove | Remove the purchase order line from the shipping container. Only lines that haven't been invoiced can be removed from the shipping container and voyage. |
| Transactions | <p>View inventory transactions for the selected purchase order line.</p><p>**Note:** If goods-in-transit functionality is used, the original order and the goods-in-transit orders are also shown. The estimated and actual costs of the goods will be updated as the overhead costs are invoiced for a voyage.</p> |
| Display dimensions | Select the inventory dimensions that appear for the transactions that you view. If you clear check boxes, fewer inventory dimensions are shown for the transactions. Therefore, less detail is shown. |
| Refresh | Update information that is related to the line amount, weight, or volume of the purchase order line. |
