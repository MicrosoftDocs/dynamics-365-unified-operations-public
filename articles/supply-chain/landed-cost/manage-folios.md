---
# required metadata

title: Manage folios
description: The folio form has the same structure as the shipment and container forms. It contains information regarding costing, customs broker and items and containers that it is attached to.
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

# Manage folios

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

The folio form has the same structure as the shipment and container forms. It contains information regarding costing, customs broker and items and containers that it is attached to.

You can use the folio form by going to **Landed cost \> Folios \> All folios**.

## Settings in header view

### General

| **Setting** | **Description** |
| --- | --- |
| **Customs Broker** | Customs brokers are defined on the vendor; this can determine automatically created costs. |
| **H.A.W.B/ Bill of lading** | House Air Waybill or Bill of Lading can be specified against the folio |
| **Cargo control number** | Used by customs departments in certain countries. |
| **Measurement** | This allows for a measurement to be specified within the Landed cost module. This is often used by organizations that do not know the individual volume/weight of the goods, but they require a more accurate apportionment than amount or quantity. The freight forwarder will supply them with the KG&#39;s or cubic measurement which they place at either an item level or purchase order level. It can be automatically updated if the parameter is selected or manually input. |
| **Number of cartons** | The number of cartons within this folio. This can be automatically updated depending on the parameter selection |
| **Vendor account** | The vendor can be optionally selected. No logic is contained, and it is stored here only for informational purposes. |
| **Remarks** | Additional information relating to the shipping container. |
| **Description of goods** | Description of goods can be selected from the folio header and is used to assist in identifying a folio of goods. For more information, refer too [description of goods](#_Description_of_goods)
 |
| **Valuation date** | This relates to the duty entry form and the module uses the customs exchange rate for the date set here. This defaults the date on the duty entry form. |
| **Customs ID** | Certain countries customs departments give a customs ID; this can be stored per folio. |

### Delivery

| **Setting** | **Description** |
| --- | --- |
| **Folio date** | This can be specified; it defaults to the created date of the voyage. |
| **ETA port** | This is the estimated arrival date at the destination port or &quot;To port&quot; |
| **Estimated delivery date** | This is normally the date that the goods are due to arrive in the warehouse. This field is not used in the estimated delivery date calculation; rather the tracking control estimated delivery date is used. Users can set this field to be equal to the tracking control estimated delivery date through the tracking control form. |
| **Original Documents Received** | Optionally, update the date original documents were received. |
| **Broker Advised** | Optionally, update the date broker was advised. |
| **Original BoL sent** | Optionally, update the date original Bill of Lading was sent. |
| **Goods released** | Optionally, update the date goods were released. |
| **Customer appointment** | Optionally, update the customer appointment date. |
| **Delivered at warehouse** | Optionally, update the date goods were delivered to the warehouse. |
| **Verification date** | Optionally, update the verification date. |
| **Delivery instructions** | Optionally, update the date delivery instructions. |
| **From port** | The port the voyage departs from. |
| **To port** | The port the voyage arrives at. It is possible on the shipping container to have a different port because the ship may stop at multiple ports. |

### Export

| **Setting** | **Description** |
| --- | --- |
| **Exporter** | The exporter can be stored on the folio. It is possible with international trade to send a purchase order to one company but receive the goods from another. This tracking and documentation are required by customs. The name and address of the exporter can be stored here. |

## Actions in header view

| **Setting** | **Description** |
| --- | --- |
| **New** | Create a voyage |
| **Delete** | Delete a voyage. Only those voyages that are in the confirmed status can be deleted. Once transactions exist against a voyage, the voyage cannot be deleted. |
| **Voyage costs** | View/add Voyage costs to all goods within the Voyage. |

### Manage

| **Action** | **Description** |
| --- | --- |
| **Post receipts list** | Post a receipts list for all purchase order lines within the folio. If multi-company shipments are used a new receipts list posting form will open per company. |
| **Product receipt** | Post a product receipt for all purchase order lines within the folio. If multi-company voyages are used a new delivery NOTE posting form will open per company. |
| **Invoice** | Post an invoice for all purchase order lines within the folio. If multi-company voyages are used a new invoice posting form will open per company |
| **Ship transfer order** | Post a transfer order voyage for all transfer order lines within the shipment |
| **Receive** | Post a transfer order receipt for all transfer order lines within the shipment. |
| **Receive in transit** | Receive all order lines that are in transit within the folio. |
| **Documents received** | Click this to update the voyage status to documents received, this can lock the Item and/or purchase line for further updates. |
| **Find auto costs** | Click this option to find relevant voyage costs. If these have already been found or updated Dynamics 365 Finance and Operations, Enterprise Edition will ask the question &quot;Un-invoiced cost lines exist. Do you want to overwrite them?&quot; **Note** : Voyage costs that are attached to a folio and invoiced will not be over written. |
| **Create arrival journal** | An arrival journal for organizations using advanced warehouse features can be generated. The options are _initialize quantity_ (recommended), and one of either _create__from goods in transit_ or _create from purchase orders_. This latter option will depend on whether goods in transit process is being used. |
| **Accrue costs** | It is possible to accrue costs where a cost type has a Ledger account specified for the Debit. This is normally used when the stock is in transit or goods have been received and invoiced. |

### General

| **Action** | **Description** |
| --- | --- |
| **Receipts list** | Post a receipts list for all purchase order lines within the folio. If multi-company voyages are used a new receipts list posting form will open per company. |
| **Product receipt** | View the product receipt record (where used). |
| **Item arrival** | View the Item arrival journal (where used). |
| **Costs inquiry** | It is possible to view all the costs of a voyage including shipping container/folio/purchase order using the Inquiry form. The exact view of the form can be adjusted using the view action.View any of the areas + item and cost type code on the Inquiry form. Removing these will adjust the inquiry form by grouping costs together, this can be useful if using sizes and colors. Change the dimensions that can be seen on the Inquiry costs form.The costs form only shows cost type codes where the Dr entry on the posting tab is set to Item. |
| **Goods in transit orders** | It is possible to open the Goods in Transit form directly from the folio. The form will display the Goods in Transit records for the selected folio only. |

## Settings in line view

| **Setting** | **Description** |
| --- | --- |
| **Measurement** | This allows for a measurement to be specified within the Landed cost module. This is often used by organizations that do not know the individual volume/weight of the goods but they require a more accurate apportionment than amount or quantity. The freight forwarder will supply them with the KG&#39;s or cubic measurement which they place at either an item level or purchase order level. It can be automatically updated if the parameter is selected or manually input. |
| **Measurement unit** | Unit of measure relating to the number in the measurement field. |
| **Number of cartons** | The number of cartons within this folio. This can be automatically updated depending on the parameter selection. |

## Actions in line view

| **Action** | **Description** |
| --- | --- |
| **Remove** | Remove purchase order line from the voyage. |
| **Transactions** | View inventory transactions for the selected line. **Note** : Where Goods in Transit is used, the original order and the Goods in Transit orders will also be displayed_._ |
| **Display dimensions** | Use this form to select the inventory dimensions that appear for the transactions that you view. If you clear check boxes, the transactions appear with fewer inventory dimensions, and therefore with less detail. |
| **Refresh** | Refresh information relating to the line amount, weight, or volume of the purchase order line |