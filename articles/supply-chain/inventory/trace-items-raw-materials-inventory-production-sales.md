---
# required metadata

title: Item and raw material tracing in inventory, production, and sales
description: This article describes how you can use item tracing to identify where items or raw materials have been used, are being used, or will be used in production and sales processes. 
author: yufeihuang
ms.date: 11/02/2017
ms.topic: article
ms.prod:
ms.technology:

# optional metadata

ms.search.form: InventTrackingDimTracing, InventTrackingDimTracingCriteria
# ROBOTS:
audience: Application User
# ms.devlang:
ms.reviewer: kamaybac
# ms.tgt_pltfrm:
ms.assetid: fdd0939a-855c-430f-a684-94f3baea1df4
ms.search.region: Global
# ms.search.industry:
ms.author: yufeihuang
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Item and raw material tracing in inventory, production, and sales

[!include [banner](../includes/banner.md)]

This article describes how you can use item tracing to identify where items or raw materials have been used, are being used, or will be used in production and sales processes.

Item tracing functionality is available on the **Item tracing** page. The following sections describe how you can use item tracing, and what the options and limitations are.

## What is item tracing?
Item tracing is a business intelligence (BI) tool that provides visibility into the source and destination of items and raw materials in the supply chain. Manufacturers can trace items, raw materials, or ingredients back to the vendor, and forward through the production and sale of the finished product. Item tracing helps manufacturers comply with regulatory requirements, and also helps quality officers and production managers analyze and take action to address variances in the quality of products and materials. Here of some examples of the ways that manufacturers can use item tracing:

-   Identify the amount of an item or raw material that is currently in inventory, and where it's stored.
-   Determine how much of the item or raw material has been shipped, and which customers it was shipped to.
-   Identify any planned shipments that include the item or raw material.
-   Locate production orders that use the item or raw material, and that are planned, in progress, or reported as finished.
-   Find out where the item or raw material was purchased.
-   Investigate where an item or raw material was consumed in the production of another item.

## What can I trace, and are there any limitations?
You can trace historical inventory transactions for items and raw materials, based on an item number and a tracking dimension, such as a serial number, batch number, or vendor batch number. You can trace an item or raw material only if a tracking dimension is assigned to it. Because tracing is based on inventory transactions, there are some limitations when you trace items. For example, there are limitations that are related to transactions for projects, fixed assets, and commerce. Additionally, co-products are shown in the trace details, but by-products aren't included. The trace includes all warehouse transactions from one location to another. Therefore, users might find the amount of information overwhelming. The trace is displayed for one legal entity at a time. There are no cross-company capabilities in an intercompany context. You must start a new trace for each company where an item is received or issued.

## What criteria can I specify for an item trace?
The criteria that are required for an item trace are the item number, a tracking dimension (such as a batch number or serial number), and the direction. The following table describes the criteria that you can use in an item trace.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Field group</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Item number</td>
<td>Enter the identifier for the item or raw material that you’re tracing.</td>
</tr>
<tr class="even">
<td>Product dimensions</td>
<td>Optional: Trace specific aspects of the product definition, such as a configuration, size, color, or style.</td>
</tr>
<tr class="odd">
<td>Tracking dimensions</td>
<td>Enter a batch number, vendor batch number, or serial number tracking dimension. When you use the batch number as a criterion, the vendor batch number is displayed if you’ve captured that information.</td>
</tr>
<tr class="even">
<td>Storage dimensions</td>
<td>Optional: Trace items that have been stored in a specific location.</td>
</tr>
<tr class="odd">
<td>Period</td>
<td>Optional: Enter dates to limit the trace to a specific period. The trace details will show only documents and transactions that were created between these dates.</td>
</tr>
<tr class="even">
<td>Forward or backward</td>
<td>Select the direction for the trace. You can trace forward or backward:
<ul>
<li><strong>Backward</strong> – Trace downstream to identify the source, the quantity that remains on hand, and any production orders that are at least partially reported as finished.</li>
<li><strong>Forward</strong> – Trace upstream to identify the destination. You can find the sales orders, and the customers that the traced item or raw material has been at least partially shipped to.</li>
</ul></td>
</tr>
</tbody>
</table>

## What information is included in the trace details?
The results of a trace appear in chronological order in the tree on the **Details** FastTab of the **Item tracing** page. The order varies, depending on the trace direction. The details include all transactions from the purchase of the item from the vendor to the sale of the item to the customer. Trace results also include interim products that are related to the item or the tracking dimension that was specified in the trace criteria. The top node shows the quantity of the item, in the inventory unit, that remains on hand, based on the storage dimensions that were specified in the trace criteria. **Note:** The trace details provide a snapshot of the information that was available when the trace was done. The trace details aren't updated if the information changes after the trace is done.

## Why don’t some nodes contain any details?
To reduce the amount of information in the trace details, only the node for the first instance of the item or raw material includes details. If a selected node doesn’t contain details, you can view the node that does contain details by clicking **Go to traced line**. You can then return to the node that you left by clicking **Go back**.

## Can I view only a particular type of document? For example, can I view only production orders, customers, or vendors?
Yes, from the trace details, you can open list pages that include only a particular type of document or transaction. You can access these pages from the **Tracing** menu item on the Action Pane, in the **Item**, **Sales**, **Purchase**, **Production**, and **Quality** groups. For example, to view a list of the vendors in the trace details, click **Tracing** &gt; **Purchase** &gt; **Vendors**. The list pages summarize the documents or transactions from the trace details. The **Pending transactions**, **Pending orders**, and **Not shipped sales orders** list pages also show other information that isn't included in the trace details. Additionally, they always show results as of the current date, even if a date range was specified. The following table describes the additional details that these pages can include.

| Lists                    | Description                                                                                                                                                                                                                                                                                                                   |
|--------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Not shipped sales orders | View sales order lines that haven’t been picked, and that therefore aren't shown in the trace details.                                                                                                                                                                                                                        |
| Pending orders           | View all pending production orders for the traced item, regardless of the tracking dimensions that were used in the trace criteria. You can also view pending production orders where the traced item is an ingredient, and where no registrations have been made and no transactions are reported as finished for the order. |
| Pending transactions     | View pending inventory transactions for the traced item that includes the specified tracking dimensions or a blank tracking dimension. You can also view pending inventory transactions for items and tracking dimension combinations, or a blank value, in the trace details.                                                |

## How many levels can I trace up or down in a BOM or formula?
You can trace one level up or down in a bill of materials (BOM) or formula. For example, if you run a trace on raw materials, you can see the finished product and any co-products. However, if you trace a co-product, the trace details don't include the finished product.

## How can I view more details about a document or transaction in the trace details?
On the **Details** FastTab, there are two ways to view more information about a selected document or transaction in the trace details:

-   When you select a node in the trace details on the **Details** FastTab, the other FastTabs on the page display information about the document or transaction in the node.
-   Open the details page for the document in a selected node by clicking **View details**. For example, if you select a node that describes a production order, and you click **View details**, the **Production orders details** page appears.

Some FastTabs give you access to additional information about the selected node. For example, on the **Non conformances** FastTab, you can click **Inquiries** to investigate whether there is a history of non-conformance. On the **Batch** FastTab, you can click **On-hand list** to view the amount of physical inventory that is currently on hand and any inventory transactions that involve the batch.

## Can I run more than one trace and then compare the details?
After you run the trace, you can use the following options on the **Trace from node** button to run a new trace on the transaction in the selected node:

-   **Backward** or **Forward** – Start a new trace for the selected node, and overwrite the details of the current trace.
-   **New backward** or **New forward** – Start a new trace in a new window, and keep the details of the current trace.

If you want to use the **New backward** or **New forward** option, you must use the **Open in a new window** functionality to have a new trace appear in a new window.

## Can I save the trace details?
You can save the information on the <strong>Details</strong> tab as an XML file by clicking <strong>Export</strong> below the *<strong><em>Tracing</em></strong>* action on the Action Pane. In addition to the trace details, the XML file includes the trace criteria, parent node, and on-hand quantity. The capability to save the details of a trace is useful if, for example, you want to attach the information to a quality order or other compliance documentation. You can specify where the file is saved. To view the file immediately, select the <strong>Show document</strong> option. <strong>Note:</strong> The file is always saved, even if you only want to view it. By default, the XML file opens in a browser window. However, you can right-click the file, select <strong>Open with</strong>, and then select the program to use to display the contents.

## Can I calculate a balance for a particular item or ingredient?
You can export the information from the summary pages to Microsoft Excel. Open the relevant page, click the **Open in Microsoft Office** icon, and then select **Export to Microsoft Excel**. This functionality is especially useful when you want to calculate a mass balance for an item or ingredient from the **Transactions summary** page. On the **Transactions summary** page, you can filter on the item or ingredient, and optionally on the batch, and then export the information to Excel. In Excel, you can isolate, for example, the on-hand quantity, the quantity that was sold, and the amount that was used in production.

## Can I investigate whether there is a history of issues with items or raw materials?
The trace details include information about quality orders and nonconformances that involve the item or raw material. To view a summary of quality orders and nonconformances, click **Quality orders** or **Non conformances** on the Action Pane. **Note:** Destructive quality orders can appear more than one time in the trace details. When a destructive quality order is created for a document, such as a purchase order, it appears for each transaction for that document.

## Are there any reporting capabilities that are related to item tracing?
You can generate the **Shipped to customers** report to identify the amount of the item or raw material that has been shipped and the customers that it was shipped to. For an inquiry that is related to compliance, you can generate the report for all customers. For an inquiry that is related to customer service, you can generate the report for a selected customer. If the product was a raw material that was used in the production of a finished item, the finished item is also included. **Note:** If you’re using the features for deleting or archiving sales orders, the report results also include any sales orders that have been deleted or archived.

## Can I trace coproducts and byproducts?
You can trace co-products, but you can’t trace a by-product, because tracking dimensions aren't typically assigned to by-products. When you trace an item, the trace details include any related co-products. A node that contains a co-product includes the word “co-product” in the details. You can also view details about a co-product by selecting the node in the trace details and then clicking the **Production** FastTab.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]