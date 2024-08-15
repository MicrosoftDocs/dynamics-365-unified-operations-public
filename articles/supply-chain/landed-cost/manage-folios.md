---
title: Manage folios
description: Learn how to work with folios, which typically consist of one vendor's goods for one entity or company per shipment, including an outline on action panes.
author: Weijiesa
ms.author: weijiesa
ms.reviewer: kamaybac
ms.search.form: ITMFolioTable, ITMFolioTableListPage
ms.topic: how-to
ms.date: 07/30/2024
ms.custom: 
  - bap-template
---

# Manage folios

[!include [banner](../../includes/banner.md)]

A folio is often determined by customs regulations. It can consist of one vendor's goods for one entity or company per shipment. The goods in a folio are managed in one container.

To open the **All folios** page, go to **Landed cost \> Folios \> All folios**. This page shows a list of all current folios. You can use the buttons on the Action Pane to create, delete, and work with folios. Select any folio in the list to view its details on the **Folios** page.

## Action Pane

The Action Pane on the **All folios** and **Folios** pages provides buttons that let you work with a selected folio. Each button performs a single action. The Action Pane also includes tabs, each of which, in turn, provides a set of related buttons. Except where noted, all buttons and tabs that are described in the following subsections are available both in the list view (that is, on the **All folios** page) and in the detailed view (that is, on the **Folios** page).

### Buttons that appear directly on the Action Pane

The following table describes the buttons that are available directly on the Action Pane.

| Button | Description |
|---|---|
| New | Create a folio. |
| Delete | Delete the open or selected folio. |
| Voyage costs | Open the **Voyage costs** page, where you can view and add folio-level costs to all the goods in the voyage. When folio costs are manually added to the voyage, they're automatically added to the cost inquiry page and apportioned to every good according to the method that is specified on the **Voyage costs** page. |

### Buttons on the Manage tab

The following table describes the buttons that are available on the **Manage** tab of the Action Pane.

| Button | Description |
|---|---|
| Post receipts list | Post a receipt list for all purchase order lines in the folio.  |
| Post product receipt | Post a product receipt for all purchase order lines in the folio. |
| Post invoice | Post an invoice for all purchase order lines in the folio.  |
| Ship transfer order | Post a transfer order for all transfer order lines that are related to the current folio in the related shipment. |
| Receive transfer order | Post a transfer order receipt for all transfer order lines that are related to the current folio in the related shipment. |
| Receive goods in transit | Receive all order lines that are in transit in the folio. |
| Documents received | Update the setting of the **Documents received** option to *Yes*. You can use this button to lock the item and/or purchase line so that it can't be updated further. |
| Find auto costs | Find relevant voyage costs. If these costs have already been found or updated, you receive the following message: "Un-invoiced cost lines exist. Do you want to overwrite them?" Voyage costs that are attached to the folio and that have been invoiced won't be overwritten. |
| Create arrival journal | Generate an arrival journal for organizations by using advanced warehouse features. You can select **Initialize quantity** (recommended), **Create from goods in transit**, and/or **Create from purchase orders**. The last option depends on whether goods-in-transit processing is being used. |
| Accrue costs | Accrue costs where a cost type has a ledger account specified for the debit. This button is typically used when the stock is in transit, or when goods have been received and invoiced. |

### Buttons on the General tab

The following table describes the buttons that are available on the **General** tab of the Action Pane.

| Button | Description |
|---|---|
| Receipts list | Post a receipt list for all purchase order lines in the folio.  |
| Product receipt | View the product receipt record, if it's used. |
| Item arrival | View the item arrival journal, if it's used. |
| Costs inquiry | Open the cost inquiry page to view all the costs of a voyage, including the shipping container, folio, and purchase order. You can adjust the exact view of the page by using the View action. On the cost inquiry page, you can view any of the areas, plus the item and cost type code. By removing these items, you can adjust the page by grouping together costs. This capability can be useful if you're using sizes and colors. You can change the dimensions that are shown on the page. The **Costs** page shows only cost type codes where the **Dr** entry on the **Posting** tab is set to *Item*. |

## Header view

To open the **Header** view, open a folio, and then select the **Header** tab in the upper right of the folio heading.

### Settings on the General FastTab

The following table describes the fields that are available on the **General** FastTab of the **Header** view of a folio.

| Field | Description |
|---|---|
| Folio | The name of the folio. This name is automatically generated when the folio is created.|
| Voyage | The voyage that is associated with the folio. |
| Customs broker | Select the customs broker for the folio. Customs brokers are defined on the vendor. They enable created costs to be determined automatically. |
| House air waybill/Bill of lading | Specify the house air waybill or bill of lading that applies to the folio. |
| Company | The legal entity (company) that is associated with the folio. |
| Cargo control number | This field is used by customs departments in some countries/regions. |
| Measurement | This field enables a measurement to be specified in the **Landed cost** module. Measurements are often used by organizations that don't know the individual volume or weight of goods, but that require a more accurate apportionment than the amount or quantity provides. The freight forwarder will provide the weight or cubic measurement, and you can put it at the level of either an item or the purchase order. It can be automatically updated if the parameter is selected or manually entered. |
| Measurement unit | The unit that applies to the specified measurement. |
| Number of cartons | The number of cartons in the folio. This field can be automatically updated, depending on the parameter selection. |
| Vendor account | Select the vendor that is associated with the folio. This field is for informational purposes only. It doesn't affect any functionality. |
| Name | The name of the selected vendor account. |
| Remarks | Enter any additional information that is related to the folio. |
| Description of goods | Select a goods description to help identify the folio. Learn more in [Description of goods](shipping-information-setup.md#description-of-goods). |
| Valuation date | This field is related to the duty entry page. The **Landed cost** module will use the customs exchange rate for the date that you set here. The default value is the date on the duty entry page. |
| Customs ID | Enter the customs ID. The customs departments in countries/regions provide this ID. |
| Tariff code | Enter a tariff code to associate with the folio. This code is typically required (and defined) by the country/region that you're shipping to. |

### Settings on the Delivery FastTab

The following table describes the settings that are available on the **Delivery** FastTab of the **Header** view of a folio.

| Field | Description |
|---|---|
| Folio date | Select a date to associate with the folio. The default value is the creation date of the voyage. |
| ETA at shipping port | The estimated time of arrival (ETA) date at the destination port ("to" port). |
| Estimated delivery date | Usually, the date when the goods are due to arrive in the warehouse. This field isn't used when the estimated delivery date is calculated. (The tracking control estimated delivery date is used instead.) To set this field so that the value matches the tracking control estimated delivery date, use the [Tracking control center](delivery-information-setup.md#tracking-control-center). |
| Original documents received | The date when the original documents were received. |
| Broker advised | The date when the broker was advised. |
| Original bill of landing sent | The date when the original bill of lading was sent. |
| Goods released | The date when goods were released. |
| Customer appointment | The customer appointment date. |
| Delivered at warehouse | The date when goods were delivered to the warehouse. |
| Verification date | The verification date. |
| Delivery instructions | The date when the delivery instructions were received. |
| From port | The port that the voyage departs from. |
| To port | The port where the voyage arrives. The shipping container might have a different port, because the ship might stop at multiple ports. |

### Settings on the Export FastTab

The following table describes the settings that are available on the **Export** FastTab of the **Header** view of a folio.

| Field | Description |
|---|---|
| Exporter | The exporter can be stored on the folio. In international trade, you might send a purchase order to one company but receive the goods from another company. Tracking and documentation are required by customs. The name and address of the exporter can be stored here. |
| Name | The name of the selected exporter. |

## Lines view

To open the **Lines** view, open a folio, and then select the **Lines** tab in the upper right of the folio heading.

### Information on the Folio FastTab

The **Folio** FastTab in the **Lines** view shows information about the folio. Most of this information also appears in the **Header** view, as described earlier in this article.

### Information and buttons on the Lines FastTab

The **Lines** FastTab in the **Lines** view shows details about each full or partial purchase order line that is included in the current folio.

The following table describes the buttons that are available on the **Lines** FastTab in the **Lines** view.

| Button | Description |
|---|---|
| Remove | Remove the selected purchase order line from the voyage. |
| Inventory \> Transactions | View inventory transactions for the selected purchase order line. If you're using goods in transit, the original order and the goods-in-transit orders are also shown. |
| Inventory \> Display dimensions | Open a dialog box where you can select the inventory dimensions that appear for the transactions that you view. |
| Refresh | Update information that is related to the line amount, weight, or volume of the selected purchase order line. |

### Information on the Lines details FastTab

The **Lines details** FastTab in the **Lines** view shows details about the purchase order line that is currently selected on the **Lines** FastTab.
