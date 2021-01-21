---
# required metadata

title: Manage folios
description: This topic describes how to work with folios. A folio typically consists of one vendor's goods for one entity/company per shipment. The goods in a folio can be in one container or spread among multiple containers.
author: RichardLuan
manager: tfehr
ms.date: 12/14/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: ITMFolioTable, ITMFolioTableListPage
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

# Manage folios

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

A folio is often determined by customs regulations. It can consist of one vendor's goods for one entity/company per shipment. The goods in a folio can be in one container or spread among multiple containers.

To open the **All folios** page, go to **Landed cost \> Folios \> All folios**. This page shows a list of current folios and provides Action Pane actions to create, delete, and work with listed folios. Select any listed folio to see its details on its **Folios** page.

## Action Pane commands

The Action Pane of the **All folios** and **Folios** page provides actions for working with a selected folio. Except where noted, all actions and tabs are available both for the the list view (the **All folios** page) and for the detailed view (the **All Folios** page).

### Actions directly on the Action Pane

The Action Pane includes both tabs, which open to show a collection of related actions, and buttons, each of which executes a single action. The following table describes the buttons that are directly on the Action Pane.

| **Setting** | **Description** |
| --- | --- |
| **New** | Create a folio. |
| **Delete** | Delete the open or selected folio. |
| **Voyage costs** | Opens the **Voyage costs** page, where you can view and add folio-level costs to all goods within the voyage. When folio costs are manually added to the voyage, they are automatically added to the costs inquiry screen and apportioned across to each good according to the method specified in the **Voyage costs** page. |

### The Manage tab of the Action Pane

The following table describes the actions available on the **Manage** tab of the Action Pane.

| **Action** | **Description** |
| --- | --- |
| **Post receipts list** | Post a receipts list for all purchase order lines within the folio. If multi-company shipments are used, a new receipts list posting dialog box will open for each company. |
| **Post product receipt** | Post a product receipt for all purchase order lines within the folio. If multi-company voyages are used, a new product receipt posting dialog box will open for each company. |
| **Post invoice** | Post an invoice for all purchase order lines within the folio. If multi-company voyages are used, a new invoice posting dialog box will open for each company |
| **Ship transfer order** | Post a transfer order for all transfer order lines related to the current folio within the related shipment. |
| **Receive transfer order** | Post a transfer order receipt for all transfer order lines related to the current folio within the related shipment. |
| **Receive goods in transit** | Receive all order lines that are in transit within the folio. |
| **Documents received** | Update **Documents received** to *Yes*. This can lock the item and/or purchase line for further updates. |
| **Find auto costs** | Finds relevant voyage costs. If these have already been found or updated, the system will ask "Un-invoiced cost lines exist. Do you want to overwrite them?" Note that voyage costs that are attached to a folio and invoiced will not be over written. |
| **Create arrival journal** | Generate an arrival journal for organizations using advanced warehouse features. You will be able to choose to **Initialize quantity** (recommended), **Create from goods in transit** and/or **Create from purchase orders**. This latter option will depend on whether the goods in transit process is being used. |
| **Accrue costs** | Accrue costs where a cost type has a ledger account specified for the debit. This is normally used when the stock is in transit or goods have been received and invoiced. |

### The General tab of the Action Pane

The following table describes the actions available on the **General** tab of the Action Pane.

| **Action** | **Description** |
| --- | --- |
| **Receipts list** | Post a receipts list for all purchase order lines within the folio. If multi-company voyages are used, a new receipts list posting form will open for each company. |
| **Product receipt** | View the product receipt record (where used). |
| **Item arrival** | View the item arrival journal (where used). |
| **Costs inquiry** | It is possible to view all the costs of a voyage including shipping container/folio/purchase order using the Inquiry form. The exact view of the form can be adjusted using the view action.View any of the areas + item and cost type code on the Inquiry form. Removing these will adjust the inquiry form by grouping costs together, this can be useful if using sizes and colors. Change the dimensions that can be seen on the Inquiry costs form.The costs form only shows cost type codes where the Dr entry on the posting tab is set to Item. |

## The Header view

To open the **Header** view, open a folio and then select the **Header** tab at the top-right part of the folio heading.

### The General FastTab of the Header view

The following table describes the settings available on the **General** FastTab of the **Header** view of a folio.

| **Setting** | **Description** |
| --- | --- |
| **Folio** | Shows the name of the folio. This was generated automatically when the folio was created.|
| **Voyage** | Shows the voyage associated with this folio. |
| **Customs Broker** | Select the customs broker for this folio. Customs brokers are defined on the vendor; this can determine created costs automatically. |
| **House air waybill/Bill of lading** | Specify the house air waybill or bill of lading that applies for the folio. |
| **Company** | The legal entity (company) associated with this folio. |
| **Cargo control number** | This is used by customs departments in certain countries. |
| **Measurement** | This allows for a measurement to be specified within the Landed cost module. This is often used by organizations that don't know the individual volume/weight of the goods, but they require a more accurate apportionment than amount or quantity. The freight forwarder will supply you with the weight or cubic measurement, which you place at either an item level or purchase order level. It can be automatically updated if the parameter is selected or manually input. |
| **Measurement unit** | The unit that applies to the specified **Measurement**. |
| **Number of cartons** | The number of cartons within this folio. This can be automatically updated depending on the parameter selection. |
| **Vendor account** | Select the vendor associated with this folio. This is for informational purposes only (does not affect any functionality). |
| **Name** | Shows the name of the selected **Vendor account**. |
| **Remarks** | Enter any additional information relating to the folio. |
| **Description of goods** | Select a goods description to assist in identifying the folio. For more information, see [Description of goods](shipping-information-setup.md#description-of-goods)
 |
| **Valuation date** | This relates to the duty entry form. The Landed cost module wiill use the customs exchange rate for the date set here. This defaults to the date on the duty entry form. |
| **Customs ID** | Certain countries customs departments give a customs ID, which you can store here. |
| **Tariff code** | Enter a tariff code to associate with folio. This is typically required (and defined) by the country you are shipping to. |

### The Delivery FastTab of the Header view

The following table describes the settings available on the **Delivery** FastTab of the **Header** view of a folio.

| **Setting** | **Description** |
| --- | --- |
| **Folio date** | Select a date to associate with the folio. It defaults to the created date of the voyage. |
| **ETA at shipping port** | This is the estimated time of arrival (ETA) date at the destination port or "To port" |
| **Estimated delivery date** | This is normally the date that the goods are due to arrive in the warehouse. This field is not used in the estimated delivery date calculation (the tracking control estimated delivery date is used instead). You can set this field to be equal to the tracking control estimated delivery date by using the  [Tracking control center](delivery-information-setup.md#tracking-control-center). |
| **Original Documents Received** | The date the original documents were received. |
| **Broker Advised** | The date the broker was advised. |
| **Original bill of landing sent** | The date the original bill of Lading was sent. |
| **Goods released** | The date goods were released. |
| **Customer appointment** | The customer appointment date. |
| **Delivered at warehouse** | The date goods were delivered to the warehouse. |
| **Verification date** | The verification date. |
| **Delivery instructions** | The date on which the delivery instructions were received. |
| **From port** | The port the voyage departs from. |
| **To port** | The port the voyage arrives at. It is possible that the shipping container could have a different port because the ship may stop at multiple ports. |

### The Export FastTab of the Header view

The following table describes the settings available on the **Export** FastTab of the **Header** view of a folio.

| **Setting** | **Description** |
| --- | --- |
| **Exporter** | The exporter can be stored on the folio. It is possible with international trade to send a purchase order to one company but receive the goods from another. This tracking and documentation are required by customs. The name and address of the exporter can be stored here. |
| **Name** | Shows the name of the selected **Exporter**. |

## Settings in Lines view

To open the **Lines** view, open a folio and then select the **Lines** tab at the top-right part of the folio heading.

### The Folio FastTab

This FastTab shows information about the folio. Most of this information is repeated from Header view, as described in the previous section.

### The Lines FastTab

This FastTab shows details about each of the purchase order lines (full or partial) included in the current folio.

The following table describes the commands available in the toolbar of the **Lines** section of the **Lines** view.

| **Action** | **Description** |
| --- | --- |
| **Remove** | Remove the selected purchase order line from the voyage. |
| **Inventory \> Transactions** | View inventory transactions for the selected line. Note that if you are using goods in transit, the original order and the goods in transit orders will also be displayed. |
| **Inventory \> Display dimensions** | Opens a dialog box where you can select the inventory dimensions that appear for the transactions that you view. |
| **Refresh** | Refresh information relating to the line amount, weight, or volume of the selected purchase order line. |

### The Lines details FastTab

This FastTab shows details about the line currently selected on the **Lines** FastTab.
