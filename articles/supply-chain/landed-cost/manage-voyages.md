---
# required metadata

title: Manage voyages
description: Shipping containers are used to group goods together that either are physically grouped together or are required to share costs only across those goods (normally because they are physically together).
author: mkirknel
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
ms.author: mkirknel
ms.search.validFrom: 2020-12-14
ms.dyn365.ops.version: Release 10.0.17
---

# Manage voyages

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

The **All voyages** page provides voyage details, delivery, costing, and item/purchase-order/transfer-order information. The header section of the page relates to the voyage details and costing information that applies at a voyage level.

On the **Lines** the shipping containers, folios and items attached to the voyage are visible and available for review. Additionally, the price and quantity of the items on the voyage are visible within the lines section of the voyage form.

To open the **All voyages** page, go to **Landed cost \> Voyages \>All voyages**.

Shipping containers and folios can be viewed by selecting the shipping container or folio hyperlink listed on each item line within the lines view of the voyage.

- The actions (in the functions group on the manage action pane) enables the user to find auto costs, aggregate costs, accrue costs, create arrival journals and change journey templates.
- The Costs Inquiry Action (in the Inquiries group on the general action pane), shows all the import costs for all cost levels and can be broken down into a per item cost view. This same form is available from the Inquiries on the purchase order, folio, and shipping container levels.
  - To view click on the general action pain, under inquiries, select Costs Inquiry.
  - All import costs for this cost area are listed. The costs can be broken down to the per item ID level for auto costs, depending upon the dimensions display setup.
  - Click on the view action to change the way this form is viewed.
  - Tick the cost areas that shipment costs must be grouped by on the Shipment costs form.

A voyage is typically one vessel, however depending on your own practices and procedures it could be one vendor or one purchase order, there really is no limitation for its use.

> [!NOTE]
> Shipping containers and folios link to a voyage and purchase lines link to a shipping container or should shipping containers and folios be switched off they can be linked directly to a voyage. In addition, costs entered here are apportioned to all attached purchase lines.

### Header view

#### General

| **Setting** | **Description** |
| --- | --- |
| **Voyage** | Voyage number |
| **Vessel** | The vessel is selected or entered in this field. Even though it is a drop-down field it allows free text within it. If the vessel is not listed in the drop-down and the user must enter free text for the vessel ID, it does not update the main table for future selection. |
| **Voyage** | The voyage/flight number should be specified here. |
| **Master air waybill** | Master air waybill number, you can specify this here if the shipment is by air. |
| **House air waybill** | House air waybill or bill of lading can be specified against the shipping container. |
| **Description** | This is an optional field and can be used to describe the voyage for simple recognition. There is no right or wrong for this field and no suggestion can be made for its use as it is different per company. |
| **Status** | Options include created, in transit, documents received, and costed. There is no logic to this field and updating is only via the posting action. The costed option means that an invoice for the stock and all shipment costs has been received. Without an invoice for a shipment cost will not allow a shipment to get the status costed. |
| **Shipping company** | Select the shipping company for this voyage, this can be used to determine auto-costs |
| **Measurement** | The measurement can be selected or automatically updated depending on the parameter setting. |
| **Measurement unit** | Unit of measure relating to the measurement |
| **Number of pallets** | The number of cartons is automatically updated if the parameter is selected. |

#### Delivery

| **Setting** | **Description** |
| --- | --- |
| **Created date** | The date that the voyage record is created. |
| **Ex-factory date** | This date selects the earliest ex-factory from the purchase orders that are linked to the voyage. The ex-factory date field is available from the purchase order header and is set up for update using the tracking control feature. |
| **Voyage date** | The voyage date is an estimated date that the plane or vessel leaves the point of origin. |
| **Departure date** | The departure date is normally the date the plane or vessel actually leaves the overseas port. The shipment date and departure date do not have to be the same date ~~.~~ This date is informational only and is not used to estimate the expected delivery date. The tracking control feature is used to estimate the expected delivery date and this field can be set up to populate automatically from the tracking control feature. |
| **Into store date** | This date selects the earliest into store date from the purchase orders that are linked to the voyage. |
| **Estimated delivery date** | This is normally the date that the goods are due to arrive in the warehouse. This date is informational only and is not used in master planning for goods. The expected delivery date on the purchase order line is used for master planning for goods on a voyage and is updated using the tracking control feature. This field can be set up to populate by the tracking control feature. |
| **Actual delivery date** | This date selects the earliest delivery date from the goods that are linked to the voyage. |
| **Original documents received** | Optionally, update the date original documents were received |
| **Broker advised** | Optionally, update the date broker was advised |
| **Original bill of lading sent** | Optionally, update the date original Bill of Lading send |
| **Goods released** | Optionally, update the date goods were released from customs. |
| **Customer appointment** | Optionally, update the customer appointment date |
| **Delivered at warehouse** | Optionally, update the date goods were delivered to the warehouse |
| **Verification date** | Optionally, update the verification date |
| **Delivery instructions** | Optionally, update the date delivery instructions |
| **Mode of delivery** | This field serves two purposes, it provides information regarding the method of delivery of the voyage and cost selection of auto costs associated with the type of transit of the goods |
| **From port** | The port the ship departs from. |
| **To port** | The port the ship arrives at. It is possible for the shipping containers to have different ports because the ship may stop at multiple ports. By verifying the to port at the shipping container level, it will provide an accurate port detail for each shipping container on a voyage. It is the combination of the shipping container type and the to and from port of the shipping container that identifies the auto cost associated with freight for the goods. |
| **Local forwarder** | This is for informational purposes; the local forwarder should be selectable from the vendor table. |
| **Local transport date** | Store the date the local transport is booked for. This can assist the warehouse in their planning. |
| **Local transport time** | Store the time slot, again this can assist the warehouse in their planning. |
| **Journey template** | The journey template specified for the voyage. The journey template is what is used to populate the to and from port of the shipping container and voyage, which then assists with identifying the auto costs associated with the voyage. |

#### Other

| **Setting** | **Description** |
| --- | --- |
| **Remarks** | Additional information relating to the container |
| **Valuation date** | This date selects the earliest ex-factory from the purchase orders that are linked to the voyage. |

#### Action descriptions

| **Action** | **Description** |
| --- | --- |
| **New** | Create a voyage. The process of voyage creation will be outlined further in the scenarios documentation. |
| **Delete** | Delete a voyage. Only a voyage that is in the confirmed status can be deleted. Once a voyage begins the sailing process and processes goods in transit, it can no longer be deleted. |
| **Voyage costs** | View/Add voyage costs to all goods within the voyage. When voyage costs are manually added to the voyage, they are automatically added to the costs inquiry screen and apportioned across to each good according to the method specified in the voyage costs form. |

#### Manage

| **Action** | **Description** |
| --- | --- |
| **Documents received** | Click this to update the voyage status to documents received, this can lock the Item and/or purchase line for further updates |
| **In transit** | Click this to update the voyage status to In-transit. There is no further logic on this process. Additionally, a voyage can be automatically updated to the goods in transit status by updating the legs of a journey in the tracking control form. |
| **Ready for costing** | Use this to determine if a voyage can be costed. A voyage can be costed when all the invoices have been processed, both stock invoices and voyage cost invoices and the goods have been received. If the estimated costs associated to a voyage have not been costed, an error will occur when attempting to process the costing of a voyage. |
| **Costed** | This can be selected when there is an invoice for all purchase orders and voyage costs. It is recommended that this is run. It cleans up any costing irregularities. There is no limit to the number of times it is run._Note: It is a good idea to run the ready for costing periodic process._ |
| **Post receipts list** | Post a receipts list for all purchase order lines within the shipment. If multi-company voyages are used a new receipts list posting form will open per company and must be processed within each legal entity. |
| **Product receipt** | Post a product receipt for all purchase order lines within the voyage. The product receipt process for the purchase order lines associated to a voyage will be used ONLY if the goods will NOT be going through the goods in transit process. If the goods are to go through the goods in transit process, the system will error out when attempting to post the product receipt for a purchase order line. If multi-company voyages are used a new delivery note posting form will open per company |
| **Invoice** | Post an invoice for all purchase order lines within the voyage. If the goods on the voyage are to go through goods in transit processing, the purchase order lines will be invoiced before the receiving process is done. Invoicing the original purchase order will create the goods in transit orders associated to the original purchase order lines, which can then be received by the warehouse. If multi-company shipments are used a new invoice posting form will open per company |
| **Ship transfer order** | Post a transfer order voyage for all transfer order lines within the voyage Transfer orders are identified on the lines section of the voyage and only transfer orders will be available for update when this option is selected. |
| **Receive** | Post a transfer order receipt for all transfer order lines within the voyage |
| **Receive in transit** | Receive all order lines that are in transit within the voyage. This is one of three available options for receiving goods in transit on a voyage. This is the most simple option, and will process the goods in transit goods out of the goods in transit warehouse and into the final destination warehouse. If the user would like greater control of the process, they can use the arrival journal or a mobile device to process the receipt of goods. |
| **Find auto costs** | Click this option to find relevant voyage costs. If these have already been found or updated Dynamics 365 Finance and Operations, Enterprise Edition will ask the question &quot;Un-invoiced cost lines exist. Do you want to overwrite them?&quot;. This will find any costs that were not associated to the voyage at the time of creation.Note: Voyage costs that are attached to a voyage and invoiced will not be over written |
| **Create arrival journal** | An arrival journal for organizations using needing to specify a location can be generated. The options are _initialize quantity_ (recommended), and one of either _create__from goods in transit_ or _create from purchase orders_. This latter option will depend on whether goods in transit process is being used When this option is selected, an arrival journal form will open up and allow users to process a standard Supply Chain Management arrival journal for the goods in transit associated to the voyage. If the item has already been received into the final destination warehouse, it will not be added to the arrival journal lines. This is one of three available options for receiving goods on a voyage. The other options are the receive in transit action on the voyage action pane or via a mobile device. |
| **Accrue costs** | It is possible to accrue costs where a cost type has a Ledger account specified for the Debit. This is normally used when the stock is in transit or goods have been received and invoiced |
| **Aggregate costs** | This is used to move costs from the shipping container level to the voyage level. A typical example is in a shared services/shipping scenario where multiple entities are sharing a shipping container/carton space. Assume the voyage has a 40&#39; shipping container and a 20&#39; shipping container, the apportionment method is volume. The goods/entities that are sharing or using the space in the 20&#39; shipping container may be being penalized. To fairly distribute some organizations may want to transfer the costs to the voyage and distribute |
| **Change journey template** | To change a journey template, it is necessary to choose this option. It may be necessary to _find auto costs_ or manually add costs once again as the voyage shipment costs will be deleted |

#### General

| **Action** | **Description** |
| --- | --- |
| **Receipts list** | This provides of product receipts lists for all purchase order lines within the voyage. If multi-company voyages are used, a new receipts list posting form will open per company. If no product receipts lists have been processed, this form is greyed out. |
| **Product receipt** | View the product receipt record (where used) for the purchase order lines associated to the voyage. This field will be greyed out if no product receipts have been posted. The product receipt process will not be used if goods in transit processing is used. |
| **Item arrival** | View the Item arrival journal (where used) |
| **Tracking** | View/update Voyage Tracking form. From the voyage tracking form, users can update the expected arrival date of goods within a shipping container and voyage and subsequently update the purchase order lines expected delivery dates. |
| **Costs inquiry** | It is possible to view all the costs of a voyage including shipping container/folio/purchase order using the Inquiry form. The exact view of the form can be adjusted using the view action.View any of the levels + item and cost type code on the Inquiry form are shown Only those cost type codes that directly relate to inventory transactions will show in this cost inquiries form. Removing these will adjust the inquiry form by grouping costs together, this can be useful if using sizes and colors. Change the dimensions that can be seen on the Inquiry costs form.The costs form only shows cost type codes where the Debit entry on the posting tab is set to Item. |
| **Goods in transit orders** | It is possible to open the Goods in Transit form directly from the voyage. The form will display the Goods in Transit records for the selected voyage only. |

### Line view

#### Field descriptions

| **Setting** | **Description** |
| --- | --- |
| **Measurement** | This allows for a measurement to be specified within Landed cost. This is often used by organizations that do not know the individual volume/weight of the goods but they require a more accurate apportionment than amount or quantity. The freight forwarder will supply them with the KG&#39;s or cubic measurement which they place at either an item level or purchase order level. It can be automatically updated if the parameter is selected or manually input |
| **Measurement unit** | Unit of measure relating to the number in the measurement field |
| **Number of cartons** | The number of cartons is automatically updated if the parameter is selected |
| **Amount** | Purchase order value for the selected line. This value cannot be updated from the voyage lines. Depending on the parameters set for Landed cost, this line will automatically update as the purchase order line amount is adjusted in the purchase order form. |