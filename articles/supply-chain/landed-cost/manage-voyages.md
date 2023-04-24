---
title: Manage voyages
description: This article describes how to work with voyages. A voyage typically represents a vessel. However, depending on your practices and procedures, it can represent a vendor, a purchase order, or some other item that makes sense for your organization.
author: Weijiesa
ms.author: weijiesa
ms.reviewer: kamaybac
ms.search.form: ITMTableListPage, ITMTable
ms.topic: how-to
ms.date: 04/20/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Manage voyages

[!include [banner](../../includes/banner.md)]

A voyage typically represents a vessel. However, depending on your practices and procedures, it can represent a vendor, a purchase order, or some other item that makes sense for your organization.

The **All voyages** page provides voyage details, delivery and costing information, and information about items, purchase orders, and transfer orders. To open the **All voyages** page, go to **Landed cost \> Voyages \> All voyages**. This page shows a list of all current voyages. You can use the buttons on the Action Pane to create, delete, and work with voyages. Select any voyage in the list to view its details.

> [!NOTE]
> Shipping containers and folios are linked to a voyage. Purchase lines are linked to a shipping container. In addition, costs that are entered here are apportioned to all attached purchase lines.
>
> Project purchase orders aren't supported in Landed cost.

## Action Pane

The Action Pane of the **Voyages** page provides buttons that let you work with a selected voyage. Each button performs a single action. The Action Pane also includes tabs, each of which, in turn, provides a set of related buttons. Except where noted, all buttons and tabs are available both in the list view of the **All voyages** page and in the detailed view for a single selected voyage.

### Buttons that appear directly on the Action Pane

The following table describes the buttons that are available directly on the Action Pane.

| Button | Description |
|---|---|
| New | [Create a voyage](/training/modules/work-with-landed-cost-supply-chain-management/create-voyage). |
| Delete | Delete the current voyage. Only voyages that have a voyage status of *Confirmed* can be deleted. After a voyage leaves port and processes goods in transit, it can no longer be deleted. |
| Voyage editor | Open the **Voyage editor** page, where you can add or remove purchase lines for the voyage, create new containers, and modify details of the voyage itself. |
| Voyage costs | Open the **Voyage costs** page, where you can view and add voyage costs to all goods in the voyage. When voyage costs are manually added to the voyage, they are automatically added to the **Costs inquiry** page and apportioned to each good according to the method that is specified on the **Voyage costs** page. |

### Buttons on the Voyage tab

The following table describes the buttons that are available on the **Voyage** tab of the Action Pane. This tab is available only when you're working in the list view of the **All voyages** page.

| Button | Description |
|---|---|
| Shipping container | Open a page that shows all the shipping containers that are associated with the selected voyage. There might be one container or many containers. |
| Folio | Open a page that shows all the folios that are associated with the selected voyage. There might be one folio or many folios. |

### Buttons on the Manage tab

The following table describes the actions that are available on the **Manage** tab of the Action Pane.

| Button | Description |
|---|---|
| Documents received | Update the voyage so that the **Documents received** option is set to *Yes*. You can use this button to lock the item and/or purchase line so that it can't be updated further. |
| In transit | Update the **Voyage status** field to the in-transit status that is established on the **[Landed cost parameters](landed-cost-parameters.md)** page. There is no further logic on this process. A voyage can also be automatically updated to the in-transit status, based on settings in the [Tracking control center](delivery-information-setup.md).
| Ready for costing | Update the **Voyage status** field to the ready for costing status that is established on the **[Landed cost parameters](landed-cost-parameters.md)** page. A voyage can be costed when all the invoices have been processed (both stock invoices and voyage cost invoices) and the goods have been received. If the estimated costs that are associated with a voyage haven't been costed, an error occurs when you try to process the costing of a voyage. |
| Costed | Clean up any costing irregularities after an invoice exists for all purchase orders and voyage costs. When you select this button, the **Voyage update - Costed** dialog box appears. There, you can select to post on the standard financial date or specify a posting date, and then run the action. You can rerun the action as many times as you want. You can also use the **Voyage update - Costed** dialog box to establish a schedule to run the action as a periodic task (batch job). We recommend that you regularly run the action by setting it up as a batch job. |
| Post receipts list | Post a receipt list for all purchase order lines in the voyage.  |
| Post product receipt | Post a product receipt for all purchase order lines in the voyage. The product receipt process for the purchase order lines that are associated with a voyage will be used only if the goods will **not** go through goods-in-transit processing. If the goods will go through goods-in-transit processing, you receive an error when you try to post the product receipt for a purchase order line.  |
| Post invoice | Post an invoice for all purchase order lines in the voyage. If the goods on the voyage will go through goods-in-transit processing, the purchase order lines will be invoiced before the receiving process is done. When the original purchase order is invoiced, the goods-in-transit orders that are associated with the original purchase order lines will be created. Those orders can then be received by the warehouse.  |
| Ship transfer order | Post a transfer order voyage for all transfer order lines in the voyage. When this button is selected, only transfer orders will be available for update. |
| Receive transfer order | Post a transfer order receipt for all transfer order lines in the voyage. |
| Receive goods in transit | Receive all order lines that are in transit in the voyage. This button is one of three options that are available for receiving goods in transit on a voyage. (The other two options are the **Create arrival journal** button that is described later in this table, and the Warehouse Management mobile app.) This option is the simplest option, and will process the goods in transit out of the goods-in-transit warehouse and into the final destination warehouse. If you want more control over the process, use the arrival journal or a mobile device to process the receipt of goods. |
| Find auto costs | Find any relevant voyage costs. If these costs have already been found or updated, you receive the following message: "Un-invoiced cost lines exist. Do you want to overwrite them?" Any costs that weren't associated with the voyage at the time of creation will be found. Voyage costs that are attached to a voyage and that have been invoiced won't be overwritten. |
| Create arrival journal | <p>Open the **Create arrival journal** dialog box, where you can create an arrival journal that specifies a location. The dialog box provides the following options:</p><ul><li>**Create from goods in transit** or **Create from transfer order** – The label for this option changes depending on whether you're using the goods-in-transit process. Set it to *Yes* to open an arrival journal page that lets you process a standard arrival journal for the goods in transit that are associated with the voyage. If the item has already been received in the final destination warehouse, it won't be added to the arrival journal lines.</li><li>**Initialize quantity** – Set this option to *Yes* to initialize the quantity that will be received, based on the quantity of goods that is specified on the voyage line. If the voyage line has been partially received, this quantity will be the remaining quantity. We recommend that you set this option to *Yes*.</li><li>**Create from order lines** – Set this option to *Yes* to take the value from the order lines.</li></ul><p>This button is one of three options that are available for receiving goods on a voyage. (The other options are the **Receive goods in transit** button that was described earlier in this table, and the Warehouse Management mobile app.)</p> |
| Accrue costs | You can accrue costs where a cost type has a ledger account specified for the debit. This button is typically used when the stock is in transit, or when goods have been received and invoiced. |
| Aggregate costs | Move costs from the shipping container level to the voyage level. You might use this button in a shared services/shipping scenario, where multiple entities share a shipping container or carton space. For example, the voyage has a 40-foot shipping container and a 20-foot shipping container, and the apportionment is done by volume. In this case, the goods/entities that share or use the space in the 20-foot shipping container might be penalized. To fairly distribute the costs, some organizations might want to transfer the costs to the voyage and distribute them based on the voyage-level apportionment method. |
| Change journey template | Open a dialog box where you can change the journey template. After you change the template, the voyage costs will be deleted. Therefore, you might have to select **Find auto costs** (see the description earlier in this table) or manually add costs again. |

### Buttons on the General tab

The following table describes the buttons that are available on the **General** tab of the Action Pane.

| Button | Description |
|---|---|
| Receipts list | Open a list of product receipts for all purchase order lines in the voyage.  If no product receipt lists have been processed, this button is unavailable. |
| Product receipt | Open the product receipt record for the purchase order lines that are associated with the voyage, if that record is used. If no product receipts have been posted, this button is unavailable. The product receipt process won't be used if you're using goods-in-transit processing. |
| Item arrival | Open the item arrival journal, if it's used. |
| Tracking | Open the **Inbound tracking** page, where you can update the expected arrival date of goods in a shipping container and a voyage, and subsequently update the expected delivery dates of purchase order lines. |
| Costs inquiry | <p>Open the **Costs inquiry** page, which shows all the costs of a voyage.</p><p>Select **View** on the Action Pane to adjust the view. You can view any of the levels, plus the item and cost type code.</p><p>Only cost type codes that are directly related to inventory transactions appear on the **Costs inquiry** page. By removing cost type codes, you can adjust the page by grouping costs together. This capability can be useful if you're using sizes and colors.</p><p>The **Costs inquiry** page shows only cost type codes where the **Debit** field is set to *Item*.</p> |
| Goods in transit orders | Open the **Goods in Transit orders** page, which shows the goods-in-transit records for the selected voyage only. |

## Lines view

To open the **Lines** view, open a voyage, and then select the **Lines** tab in the upper right of the voyage heading.

### Information on the Voyage header FastTab

The **Voyage header** FastTab in the **Lines** view of a voyage contains basic information that describes the voyage. Many of the fields that appear on this FastTab also appear in the **Header** view, as described later in this article.

### Information on the Voyage lines FastTab

The **Voyage lines** FastTab in the **Lines** view of a voyage is related to the voyage details and costing information that apply at the voyage level. Here, you can review the shipping containers, folios, and items that are attached to the voyage. The price and quantity of the items on the voyage are also shown. You can view any shipping container or folio that is listed by selecting the relevant link.

### Information on the Line details FastTab

The **Line details** FastTab in the **Lines** view of a voyage provides more information about the line that is currently selected on the **Voyage lines** FastTab. Note that this FastTab includes details about the position that each line occupies in the container, and its declared quantity.

## Header view

To open the **Header** view, open a voyage, and then select the **Header** tab in the upper right of the voyage heading.

### Settings on the General FastTab

The following table describes the fields that are available on the **General** FastTab in the **Header** view of a voyage.

| Field | Description |
|---|---|
| Voyage | Enter the voyage or flight number. |
| Booking reference | If your shipper or shipping center provides a reference number to identify the voyage (that is, the shipper's or shipping center's internal reference), enter it here. |
| Vessel | Enter or select the vessel. If the vessel isn't listed as a value, you can enter the vessel ID as free text. In that case, the main table isn't updated so that the vessel ID can be selected in this field later. |
| External voyage ID | Enter the publicly available ID for the voyage (such as the flight number). |
| Master air waybill/Bill of lading | Enter the master air waybill or bill of lading number. You can specify this value when you ship by air. |
| House air waybill/Bill of lading | Enter the house air waybill or bill of lading for the shipping container. |
| Rental | Select this check box to indicate that the container is a rental container that must be returned. |
| Description | Enter a description of the voyage to make it easier to recognize. |
| Voyage status | The status of the voyage. Values include *Created*, *In transit*, *Documents received*, and *Costed*. This field isn't calculated based on logic. It's updated only via the posting action. The *Costed* value indicates that an invoice for the stock and all voyage costs has been received. Unless an invoice is received, a voyage can't reach a status of *Costed*. |
| Purchase order status | The highest status that has been reached among all the purchase orders that are associated with the voyage. |
| Documents received | A value that indicates whether your company has received all the documents that are associated with the voyage. To change the value, select **Documents received** in the **Voyage update** group on the **Manage** tab of the Action Pane. |
| Shipping company | Select the shipping company for this voyage. This field can be used to determine auto costs. |
| Name | The name of the company that is selected in the **Shipping company** field. |
| Measurement | This field enables a measurement to be specified in an auto cost. Measurements are often used by organizations that don't know the individual volume or weight of the goods, but that require a more accurate apportionment than the amount or quantity provides. The freight forwarder will provide the weight or cubic measurement, and you can put it at the level of either an item or the purchase order. It can be automatically updated if the parameter is selected, or it can be manually entered. |
| Measurement unit | The unit of measure that applies to the number in the **Measurement** field. |
| Number of pallets | Specify the number of pallets on the voyage line. This field is automatically updated if the **Automatically update number of cartons** option is set to *Yes* on the **General** tab of the **Landed cost parameters** page. |

### Settings on the Delivery FastTab

The following table describes the fields that are available on the **Delivery** FastTab in the **Header** view of a voyage.

| Field | Description |
|---|---|
| Created date and time | The date and time when the voyage record was created. |
| Ex-factory date | This field selects the earliest ex-factory date among the purchase orders that are linked to the voyage. The ex-factory date is available on the purchase order header and is updated by using the tracking control feature. |
| Ship date | The estimated date when the plane or vessel leaves the point of origin. |
| Departure date | The departure date is usually the date when the plane or vessel actually leaves the overseas port. The ship date and departure date don't have to match. The **Departure date** field is for informational purpose only. It isn't used to estimate the expected delivery date. The tracking control feature is used to estimate the expected delivery date, and this field can be set up so that it's automatically filled in by the tracking control feature. |
| In to store date | This field selects the earliest date when the goods from the purchase orders that are linked to the voyage will be available for sale. |
| Estimated delivery date | The estimated delivery date is usually the date when the goods are due to arrive in the warehouse. This field is for informational purposes only. It isn't used for master planning for goods. The expected delivery date on the purchase order line is used for master planning for goods on a voyage and is updated by using the tracking control feature. This field can be set up so that it's filled in by the tracking control feature. |
| Actual delivery date | The earliest delivery date, based on the goods that are linked to the voyage. |
| ETA at shipping port | Enter the date when you expect the voyage to arrive at the shipping port, based on the information that was provided by your shipping agent. |
| Original documents received | Enter the date when the original documents were received. |
| Broker advised | Enter the date when the broker was advised. |
| Original bill of lading sent | Enter the date when the original bill of lading was sent. |
| Goods released | Enter the date when the goods were released from customs. |
| Customer appointment | Enter the customer appointment date, which is the date when you expect the customer to take ownership of the goods. |
| Delivered at warehouse | Enter the date when the goods were delivered to the warehouse. |
| Verification date | Enter the verification date. |
| Delivery instructions | Enter the date when the delivery instructions were received. |
| Mode of delivery | This field provides information about the method that is used to deliver the voyage and the cost selection of auto costs that are associated with that delivery method. |
| From port | The shipping port that the voyage departs from. |
| To port | The shipping port where the voyage arrives. The shipping containers can have different ports, because the ship might stop at multiple ports. By verifying the "to" port at the shipping container level, you provide accurate port details for every shipping container on a voyage. The auto cost that is associated with the freight is determined based on the combination of the shipping container type, the "to" port, and the "from" port. |
| Local forwarder | This field is for informational purposes only. The local forwarder should be selectable from the vendor table. |
| Local transport date | The date that the local transport is booked for. This field can help the warehouse do its planning. |
| Local transport time | The time slot that the local transport is booked for. This field can help the warehouse do its planning. |
| Journey template | The journey template that is specified for the voyage. The journey template is used to enter the "to" port and "from" port of the shipping container and voyage. Those values, in turn, help identify the auto costs that are associated with the voyage. |

### Settings on the Other FastTab

The following table describes the fields that are available on the **Other** FastTab in the **Header** view of a voyage.

| Field | Description |
|---|---|
| Remarks | Enter additional information that is related to the voyage. |
| Valuation date | Select the earliest ex-factory date for the purchase orders that are linked to the voyage. |
| Pending voyage | You can use this to indicate whether your shipment or voyage has left yet. It is for informational purposes only.  |
| Renaming shipping containers | For voyages that have more than one container, the number of containers that haven't yet been received. |

## Voyage update periodic tasks

The **Landed cost** module includes several voyage-related periodic tasks that can bulk-update several aspects of voyages. To run or schedule these periodic tasks, go to **Landed cost \> Periodic tasks \> Voyage updates**, and then select one of the following task types:

- **Documents received** – This task lets you set **Documents received** to *Yes* for several voyages at the same time. Use the **Filter** settings to define the set of voyages that you want to update.
- **In transit** – This task lets you set the **Voyage status** field to the in-transit status that is established on the **[Landed cost parameters](landed-cost-parameters.md)** page for several voyages at the same time. Use the **Filter** settings to define the set of voyages that you want to update.
- **Ready for costing** – This task lets you set the **Voyage status** field to the ready for costing status that is established on the **[Landed cost parameters](landed-cost-parameters.md)** page for several voyages at the same time. You will typically set up this task to run on a regular schedule.
- **Costed**  – This task lets you set the **Voyage status** field to the costed status that is established on the **[Landed cost parameters](landed-cost-parameters.md)** page for several voyages at the same time, provided that they have been costed but haven't yet been updated on the voyage. You will typically set up this task to run on a regular schedule.

## <a name="source-doc-post"></a>Show landed costs in the accounting distribution of product receipts

[!INCLUDE [preview-banner-section](../../includes/preview-banner-section.md)]

<!-- KFM: Preview until further notice -->

When a product receipt is posted against a purchase order, Landed cost creates a source document line for each landed cost amount. The amount from Landed cost is shown on the **Account distributions** page, which is available from the product receipt.

The following illustration shows an example of accounting distributions that include landed costs.

[<img src="media/accounting-distributions.png" alt="Example of accounting distributions that include landed costs." title="Example of accounting distributions that include landed costs" width="720" />](media/accounting-distributions.png#lightbox)

This feature enables landed costs to be included in the accounting distribution of purchased product receipts. Therefore, users can more easily identify and track these costs. This feature doesn't affect the product receipt accounting logic that's used in other places in Microsoft Dynamics 365 Supply Chain Management.

To use this feature, you must be running Supply Chain Management 10.0.34 or higher and the *(Preview) Source document and accounting distribution support for Landed Cost* feature must be turned on in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).
