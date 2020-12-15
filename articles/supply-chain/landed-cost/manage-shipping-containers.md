---
# required metadata

title: Manage shipping containers
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

# Manage shipping containers

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

Shipping containers are used to group goods together that either are physically grouped together or are required to share costs only across those goods (normally because they are physically together).

The format of the shipping **container form** is very similar to the format of the **voyage form**. Shipping container and costing information can be found on the top half of the form. Folios, items and purchase orders or transfer orders attached to the container are found on the lines section of the form.

_To view and process goods through the shipping container form, navigate to__Landed cost \> Containers \> All Containers._

## Header view

### General

| **Setting** | **Description** |
| --- | --- |
| **Shipping Container type** | This must be entered and can determine the cost for freight for example by selecting the auto cost associated to the shipping container type. |
| **Vessel** | The vessel is selected or entered here. Even though it is a drop-down field it allows free text within it. If the vessel is not listed and the user decides to enter free text it does not update the main table for future selection. For more information, refer to [Vessels](#_Vessels). |
| **Unit type** | Unit types are used as an additional grouping and identification method against a shipping container. They are shown and selected on the shipping container form. For more information, refer to unit types. |
| **Refrigeration type** | Refrigeration types are used as an additional grouping and identification method against a shipping container, normally for refrigerated containers. They are shown and selected on the shipping container form. For more information, refer to refrigeration types. This field is optional. |
| **Measurement** | This allows for a measurement to be specified within the Landed cost module. This is often used by organizations that do not know the individual volume/weight of the goods, but they require a more accurate apportionment than amount or quantity. The freight forwarder will supply them with the kg&#39;s or cubic measurement which they place at either an item level or purchase order level. It can be automatically updated if the parameter is selected or manually input. |
| **Measurement unit** | Unit of measure relating to the number in the measurement field. |
| **Actual weight** | The actual weight can be recorded of the carton/container. This can be used to verify against the maximum weight allowed on a shipping container setup. |
| **Number of cartons** | The number of cartons is automatically updated if the parameter is selected. |
| **Description of goods** | Description of goods can be selected from the shipping container or folio header and is used to assist in identifying a voyage/shipping container/folio of goods. For more information, refer to description of goods. |
| **H.A.W.B/Bill of lading** | House air waybill or Bill of Lading can be specified against the shipping container. |
| **Remarks** | Additional information relating to the shipping container. |

### Delivery

| **Setting** | **Description** |
| --- | --- |
| **Created date and time** | Created date and time of the container. |
| **Ex-factory date** | This date is normally given to the factory/vendor to advise them when you expect the goods to leave their premises. Often dealing with a factory in Asia will require this date as opposed to the date that you expect the goods by which is normally the case for a local delivery. This field can be populated by the purchase order lines on the shipping container list or by manual entry on this form. |
| **Ship date** | This date can be printed on the purchase order document. It normally advises the factory/vendor when the goods should be delivered to the port by. This is an informational field only and is not used to estimate the expected delivery date of the goods within the shipping container. This field can be set to automatically update when the tracking control form is updated. |
| **Estimated delivery date** | This is normally the date that the goods are due to arrive in the warehouse. This field is informational only and is not used to calculate master planning on the purchase order lines within the shipping container. The expected delivery date on the Purchase lines is updated through tracking control. This field can be set to update when the tracking control form is updated. |
| **Departure date** | The departure date is normally the date the plane or vessel actually leaves the overseas port. |
| **Estimated time of arrival at port** | This is the estimated arrival date at the destination port or &quot;To port&quot;. |
| **Original documents received** | Optionally, update the date original documents were received. |
| **Broker advised** | Optionally, update the date broker was advised. |
| **Original bill of lading sent** | Optionally, update the date original Bill of Lading send. |
| **Goods released** | Optionally, update the date goods were released. |
| **Customer appointment** | Optionally, update the customer appointment date. |
| **Delivered at warehouse** | Optionally, update the date goods were delivered to the warehouse. |
| **Verification date** | Optionally, update the verification date. |
| **Delivery instructions** | Optionally, update the date delivery instructions.
 |
| **Local forwarder** | This is for informational purposes; the local forwarder should be selectable from the vendor table. |
| **Local transport date** | Store the date the local transport is booked for. This can assist the warehouse in their planning. |
| **Local transport time** | Store the time slot, again this can assist the warehouse in their planning |
| **Journey template** | The journey template specified for the voyage. The journey template will provide the details of the to and from port as well as the lead times associated to the tracking control of the shipping container. |

### Action descriptions

| **Action** | **Description** |
| --- | --- |
| **New** | Create a voyage. The voyage creation process will be outlined further in the scenarios documentation. |
| **Delete** | Delete a voyage. Only voyages that are in the confirmed status can be deleted. Once a voyage has begun the goods in transit process, it can no longer be deleted. |
| **Voyage Costs** | View/add voyagecosts to all goods within the shipping container. When the voyage costs are added at the shipping container form manually, they will only pertain to the items within the shipping container and not to the voyage as a whole. This will allow users to add shipping container level costs to a voyage that were missed in the auto cost creation. All voyage costs associated to the shipping container will be shown, with no dependency on the cost code type definition. |

### Manage

| **Action** | **Descriptions** |
| --- | --- |
| **Post receipts list** | Post a receipts list View the product receipts lists for all purchase order lines within the shipping container. If multi-company shipments are used a new receipts list posting form will open per company. |
| **Product receipt** | View the product receipt record (where used). |
| **Invoice** | Post an invoice for all purchase order lines within the shipping container. If multi-company shipments are used a new invoice posting form will open per company. |
| **Ship transfer order** | Post a transfer order shipment for all transfer order lines within the shipping container. Only those lines within the shipping container that are a type of transfer order will appear in the form. |
| **Receive** | Post a transfer order receipt for all transfer order lines within the shipping container. The receive form is the simplest way to receive goods within a shipping container or voyage and is one of three options available. The other two options are to receive via arrival journals or via mobile device processing. |
| **Receive in transit** | Receive all order lines that are in transit within the shipping container. The receive form is the simplest way to receive goods within a shipping container or voyage and is one of three options available. The other two options are to receive via arrival journals or via mobile device processing. |
| **Find auto costs** | Click this option to find relevant voyage costs for the shipping container. If these have already been found or updated Dynamics 365 Finance and Operations, Enterprise Edition will ask the question &quot;Un-invoiced cost lines exist. Do you want to overwrite them?&quot;. Note: Voyage costs that are attached to a shipping container and invoiced will not be over written |
| **Create arrival journal** | An arrival journal for organizations using advanced warehouse features can be generated. The options are _initialize quantity_ (recommended), and one of either _create__from goods in transit_ or _create from purchase orders_. This latter option will depend on whether goods in transit process is being used. |
| **Accrue costs** | It is possible to accrue costs where a Cost type has a Ledger account specified for the Dr. This is normally used when the stock is in transit or goods have been received and invoiced. |
| **Rename** |
 |
| **Change journey template** | To change a journey template, it is necessary to choose this option. It may be necessary to _find auto costs_ or manually add costs once again as the shipment costs will be deleted. |

### General

| **Action** | **Descriptions** |
| --- | --- |
| **Receipts list** | Post a receipts list for all purchase order lines within the shipping container. If multi-company voyages are used a new receipts list posting form will open per company. |
| **Product Receipt** | View the product receipt record (where used) The product receipt process will only be used if the goods are not using goods in transit functionality. |
| **Item arrival** | View the Item arrival journal (where used) for the shipping container. |
| **Legs** | Legs are used to identify separate parts of a journey. Each leg can have lead times associated which can assist with shipment tracking. For more information, refer to [Legs](#_Legs). |
| **Tracking** | View/Update shipment tracking |
| **Costs inquiry** | It is possible to view all the costs of a shipping container including container/folio/purchase order using the Inquiry form. The exact view of the form can be adjusted using the view action.View any of the areas + item and cost type code on the Inquiry form. Removing these will adjust the inquiry form by grouping costs together, this can be useful if using sizes and colors. Change the dimensions that can be seen on the Inquiry costs form.The costs form only shows cost type codes where the Dr entry on the posting tab is set to Item. |
| **Goods in transit orders** | It is possible to open the Goods in Transit form directly from the container. The form will display the Goods in Transit records for the selected shipping container only. |
| **Over/under transactions** | It is possible to open the Over/Under Transactions form directly from the shipping container. The form will display the Over/Under records for the selected shipping container only. The over and under transactions will only be available once the goods have been received into the warehouse and the goods in transit order has been closed for further receiving. The over/under transactions process will be defined further in the over/under transactions scenario. |

## Line view

### Field descriptions

| **Setting** | **Description** |
| --- | --- |
| **Measurement** | This allows for a measurement to be specified within the Landed cost module. This is often used by organizations that do not know the individual volume/weight of the goods, but they require a more accurate apportionment than amount or quantity. The freight forwarder will supply them with the KG&#39;s or cubic measurement which they place at either an item level or purchase order level. It can be automatically updated if the parameter is selected or manually input. |
| **Measurement Unit** | Unit of measure relating to the number in the measurement field. |
| **Number of cartons** | The number of cartons is automatically updated if the parameter is selected. |

### Actions

| **Action** | **Description** |
| --- | --- |
| **Remove** | Remove purchase order line from the shipping container. Only lines that have not been invoiced can be removed from the shipping container and voyage |
| **Transactions** | View inventory transactions for the selected line. **Note** : Where goods in transit is used, the original order and the goods in transit orders will also be displayed. This is where users can see the estimated and actual costs of the goods update as the overhead costs are invoiced for a voyage. |
| **Display dimensions** | Use this form to select the inventory dimensions that appear for the transactions that you view. If you clear check boxes, the transactions appear with fewer inventory dimensions, and therefore with less detail. |
| **Refresh** | Refresh information relating to the line amount, weight, or volume of the purchase order line |