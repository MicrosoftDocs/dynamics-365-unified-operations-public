---
# required metadata

title: Quality associations
description: This article describes how you can use quality associations in Microsoft Dynamics 365 Supply Chain Management to automatically generate quality orders that are related to your sales, purchase, and production processes.
author: yufeihuang
ms.date: 03/23/2021
ms.topic: article
ms.prod:
ms.technology:

# optional metadata

ms.search.form: InventTestAssociationTable
# ROBOTS:
audience: Application User
# ms.devlang:
ms.reviewer: kamaybac
# ms.tgt_pltfrm:
ms.assetid: a1d9417b-268f-4334-8ab6-8499d6c3acf0
ms.search.region: Global
ms.search.industry: Distribution
ms.author: yufeihuang
ms.search.validFrom: 2020-06-18
ms.dyn365.ops.version: AX 7.0.0

---

# Quality associations

[!include [banner](../includes/banner.md)]

This article describes how you can use quality associations in Microsoft Dynamics 365 Supply Chain Management to automatically generate quality orders that are related to your sales, purchase, and production processes.

A quality association defines all the following information for a quality order that is generated:

- The transaction event
- The set of tests that must be performed on the items
- The acceptable quality level (AQL)
- The sampling plan

You must define a quality association for each variation in a business process that requires automatic generation of quality orders. For example, a quality order can be generated in the business processes for purchase orders, quarantine orders, sales orders, and production orders.

## Working with quality associations

The business process that uses a quality association can be related to various source documents, such as purchase orders, sales orders, or production orders.

Each quality association record defines the set of tests, the AQL, and the sampling plan that applies to the quality orders that are generated. You must define a quality association record for each variation in a business process. For example, you can set up a quality association that generates a quality order when a purchase order product receipt is updated. Depending on the setup of the execution plan, the triggering process itself can be blocked while there is an open quality order. Alternatively, subsequent processes, such as purchase order invoicing, can be blocked.

> [!NOTE]
> While there are open quality orders, inventory quantities are automatically blocked from being issued. Depending on the setting of the **Full blocking** field on the **Item samplings** page, the quantity is either the quantity on the quality order or the quantity on the source document line. For more information, see [Quality management item sampling](quality-item-sampling.md).

For a given business process, the quality association record identifies the event and conditions that a quality order is generated for. The conditions can be specific to either a site or a legal entity. A quality order that involves destructive tests can be generated only when on-hand inventory exists for the event.

To work with quality associations, go to **Inventory management \> Setup \> Quality control \> Quality associations**. The following examples show how a quality association record is defined for the variations in each business process. For each example, the following table summarizes the events and conditions that are defined by a quality association record.

<table>
<thead>
<tr>
<th>Reference type</th>
<th>Event type</th>
<th>Execution</th>
<th>Event blocking</th>
<th>Document reference</th>
</tr>
</thead>
<tbody>
<tr>
<td>Inventory</td>
<td>Not applicable</td>
<td>Not applicable</td>
<td>None</td>
<td>All</td>
</tr>
<tr>
<td rowspan="7">Sales</td>
<td rowspan="4">Picking process is scheduled</td>
<td rowspan="4">Before</td>
<td>None</td>
<td rowspan="22">Specific ID, Group, or All only</td>
</tr>
<tr>
<td>Picking process</td>
</tr>
<tr>
<td>Packing slip</td>
</tr>
<tr>
<td>Invoice</td>
</tr>
<tr>
<td rowspan="3">Packing slip</td>
<td rowspan="3">Before</td>
<td>None</td>
</tr>
<tr>
<td>Packing slip</td>
</tr>
<tr>
<td>Invoice</td>
</tr>
<tr>
<td rowspan="15">Purchase</td>
<td rowspan="7">Receipt list</td>
<td rowspan="4">Before</td>
<td>None</td>
</tr>
<tr>
<td>Receipt list</td>
</tr>
<tr>
<td>Product receipt</td>
</tr>
<tr>
<td>Invoice</td>
</tr>
<tr>
<td rowspan="3">After</td>
<td>None</td>
</tr>
<tr>
<td>Product receipt</td>
</tr>
<tr>
<td>Invoice</td>
</tr>
<tr>
<td rowspan="3">Registration</td>
<td rowspan="3">Not applicable</td>
<td>None</td>
</tr>
<tr>
<td>Product receipt</td>
</tr>
<tr>
<td>Invoice</td>
</tr>
<tr>
<td rowspan="5">Product receipt</td>
<td rowspan="3">Before</td>
<td>None</td>
</tr>
<tr>
<td>Product receipt</td>
</tr>
<tr>
<td>Invoice</td>
</tr>
<tr>
<td rowspan="2">After</td>
<td>None</td>
</tr>
<tr>
<td>Invoice</td>
</tr>
<tr>
<td rowspan="8">Production</td>
<td rowspan="3">Registration</td>
<td rowspan="3">Not applicable</td>
<td>None</td>
<td rowspan="12">All</td>
</tr>
<tr>
<td>Report as finished</td>
</tr>
<tr>
<td>End</td>
</tr>
<tr>
<td rowspan="5">Report as finished</td>
<td rowspan="3">Before</td>
<td>None</td>
</tr>
<tr>
<td>Report as finished</td>
</tr>
<tr>
<td>End</td>
</tr>
<tr>
<td rowspan="2">After</td>
<td>None</td>
</tr>
<tr>
<td>End</td>
</tr>
<tr>
<td rowspan="4">Quarantine</td>
<td rowspan="3">Report as finished</td>
<td rowspan="2">Before</td>
<td>Report as finished</td>
</tr>
<tr>
<td>End</td>
</tr>
<tr>
<td>After</td>
<td>End</td>
</tr>
<tr>
<td>End</td>
<td>Before</td>
<td>End</td>
</tr>
<tr>
<td rowspan="3">Route operation</td>
<td rowspan="3">Report as finished</td>
<td rowspan="2">Before</td>
<td>None</td>
<td rowspan="3">Specific ID, Group, or All, and specific Resource, Group, or All</td>
</tr>
<tr>
<td>Report as finished</td>
</tr>
<tr>
<td>After</td>
<td>None</td>
</tr>
<tr>
<td rowspan="3">Co-product production</td>
<td>Registration</td>
<td>Not applicable</td>
<td rowspan="3">None</td>
<td rowspan="3">All</td>
</tr>
<tr>
<td rowspan="2">Report as finished</td>
<td>Before</td>
</tr>
<tr>
<td>After</td>
</tr>
</tbody>
</table>

> [!NOTE]
> The *Quality management for warehouse processes* feature adds capabilities for quality order processing for production where the **Event type** field is set to *Report as finished* and the **Execution** field is set to *After*, and for purchases where the **Event type** field is set to *Registration*. For more information, see [Quality management for warehouse processes](quality-management-for-warehouses-processes.md).

The following table provides more information about how quality orders can be generated for specific types of processes.

<div class="tableSection">
<table>
<thead>
<tr>
<th>Type of process</th>
<th>When quality orders can be automatically generated</th>
<th>When quality orders can be generated if destructive testing is required</th>
<th>Condition information</th>
<th>Manual generation information</th>
</tr>
</thead>
<tbody>
<tr>
<td>Purchase order</td>
<td>Before or after a receipts list or product receipt for the material that is received is posted</td>
<td>After the product receipt for the material that is received is posted, because the material must be available for destructive testing</td>
<td>The requirement for a quality order can reflect a specific site, item, or vendor, or a combination of these conditions.</td>
<td>A manually generated quality order that refers to a purchase order can use information in a quality association record, such as the test sampling plan.</td>
</tr>
<tr>
<td>Quarantine order</td>
<td>Before or after the quarantine order is reported as finished or ended</td>
<td>Quality orders that require destructive tests can't be generated. It's assumed that the quarantine order functionality handles the disposition of the material that is destroyed.</td>
<td>The requirement for a quality order can reflect a specific site, item, or vendor, or a combination of these conditions.</td>
<td>A manually generated quality order that refers to a quarantine order can use information in a quality association record, such as the test sampling plan.</td>
</tr>
<tr>
<td>Sales order</td>
<td>Before a scheduled picking process or packing slip update for the items that are being shipped</td>
<td>At any step</td>
<td>The requirement for a quality order can reflect a specific site, item, or customer, or a combination of these conditions.</td>
<td>A manually generated quality order that refers to a sales order can use information in a quality association record, such as the test sampling plan.</td>
</tr>
<tr>
<td>Production order</td>
<td>Before or after the finished quantity for the production order is reported</td>
<td>After the finished quantity for the production order is reported</td>
<td>The requirement for a quality order can reflect a specific site or item, or a combination of these conditions.</td>
<td>A manually generated quality order that refers to a production order can use information in a quality association record, such as the test sampling plan.</td>
</tr>
<tr>
<td>Production order that has a route operation</td>
<td>Before or after the report is finished for an operation</td>
<td>After the reporting production is finished for the last operation</td>
<td>The requirement for a quality order can reflect a specific site, item, or operations resource, or a combination of these conditions.</td>
<td>A manually generated quality order that refers to a route operation can use information in a quality association record, such as the test sampling plan.</td>
</tr>
<tr>
<td>Inventory</td>
<td>A quality order can't be automatically generated for a transaction in an inventory journal or for transfer order transactions.</td>
<td></td>
<td></td>
<td>A quality order must be manually created for an item's inventory quantity. Physical on-hand inventory is required.</td>
</tr>
</tbody>
</table>
</div>

## Examples of automatic generation of quality orders

### Purchasing

In purchasing, if you set the **Event type** field to *Product receipt* and the **Execution** field to *After* on the **Quality associations** page, you get the following results:

- If the **Per updated quantity** option is set to *Yes*, a quality order is generated for every receipt against the purchase order, based on the received quantity and settings in the item sampling. Every time that a quantity is received against the purchase order, new quality orders are generated based on the newly received quantity.
- If the **Per updated quantity** option is set to *No*, a quality order is generated for the first receipt against the purchase order, based on the received quantity. Additionally, one or more quality orders are created based on the remaining quantity, depending on the tracking dimensions. Quality orders aren't generated for subsequent receipts against the purchase order.

### Production

In production, if you set the **Event type** field to *Report as finished* and the **Execution** field to *After* on the **Quality associations** page, you get the following results:

- If the **Per updated quantity** option is set to *Yes*, a quality order is generated based on every finished quantity and settings in the item sampling. Every time that a quantity is reported as finished against the production order, new quality orders are generated based on the newly finished quantity. This generation logic is consistent with purchasing.
- If the **Per updated quantity** option is set to *No*, a quality order is generated the first time that a quantity is reported as finished, based on the finished quantity. Additionally, one or more quality orders are created based on the remaining quantity, depending on the tracking dimensions of the item sampling. Quality orders aren't generated for subsequent finished quantities.

<table>
<thead>
<tr>
<th>Quality specification</th>
<th>Per updated quantity</th>
<th>Per tracking dimension</th>
<th>Result</th>
</tr>
</thead>
<tbody>
<tr>
<td>Percentage: 10%</td>
<td>Yes</td>
<td>
<p>Batch number: No</p>
<p>Serial number: No</p>
</td>
<td>
<p>Order quantity: 100</p>
<ol>
<li>Report as finished for 30
<ul>
<li>Quality order 1 for 3 (10% of 30)</li>
</ul>
</li>
<li>Report as finished for 70
<ul>
<li>Quality order 2 for 7 (10% of the remaining order quantity, which is 70 in this case)</li>
</ul>
</li>
</ol>
</td>
</tr>
<tr>
<td>Fixed quantity: 1</td>
<td>No</td>
<td>
<p>Batch number: No</p>
<p>Serial number: No</p>
</td>
<td>Order quantity: 100
<ol>
<li>Report as finished for 30
<ul>
<li>Quality order 1 for 1 (for the first reported-as-finished quantity, which has a fixed value of 1)</li>
<li>Quality order 2 for 1 (for the remaining quantity, which still has a fixed value of 1)</li>
</ul>
</li>
<li>Report as finished for 10
<ul>
<li>No quality orders are created.</li>
</ul>
</li>
<li>Report as finished for 60
<ul>
<li>No quality orders are created.</li>
</ul>
</li>
</ol>
</td>
</tr>
<tr>
<td>Fixed quantity: 1</td>
<td>Yes</td>
<td>
<p>Batch number: Yes</p>
<p>Serial number: Yes</p>
</td>
<td>
<p>Order quantity: 10</p>
<ol>
<li>Report as finished for 3: 1 for batch number b1, serial number s1; 1 for batch number b2, serial number s2; and 1 for batch number b3, serial number s3
<ul>
<li>Quality order 1 for 1 of batch number b1, serial number s1</li>
<li>Quality order 2 for 1 of batch number b2, serial number s2</li>
<li>Quality order 3 for 1 of batch number b3, serial number s3</li>
</ul>
</li>
<li>Report as finished for 2: 1 for batch number b4, serial number s4; and 1 for batch number b5, serial number s5
<ul>
<li>Quality order 4 for 1 of batch number b4, serial number s4</li>
<li>Quality order 5 for 1 of batch number b5, serial number s5</li>
</ul>
</li>
</ol>
<p><strong>Note:</strong> The batch can be reused.</p>
</td>
</tr>
<tr>
<td>Fixed quantity: 2</td>
<td>No</td>
<td>
<p>Batch number: Yes</p>
<p>Serial number: Yes</p>
</td>
<td>
<p>Order quantity: 10</p>
<ol>
<li>Report as finished for 4: 1 for batch number b1, serial number s1; 1 for batch number b2, serial number s2; 1 for batch number b3, serial number s3; and 1 for batch number b4, serial number s4
<ul>
<li>Quality order 1 for 1 of batch number b1, serial number s1</li>
<li>Quality order 2 for 1 of batch number b2, serial number s2</li>
<li>Quality order 3 for 1 of batch number b3, serial number s3</li>
<li>Quality order 4 for 1 of batch number b4, serial number s4</li>
</ul>
<ul>
<li>Quality order 5 for 2, without a reference to a batch number and a serial number</li>
</ul>
</li>
<li>Report as finished for 6: 1 for batch number b5, serial number s5; 1 for batch number b6, serial number s6; 1 for batch number b7, serial number s7; 1 for batch number b8, serial number s8; 1 for batch number b9, serial number s9; and 1 for batch number b10, serial number s10
<ul>
<li>No quality orders are created.</li>
</ul>
</li>
</ol>
</td>
</tr>
</tbody>
</table>

## Additional resources

- [Quality management processes](quality-management-processes.md)
- [Enable quality and nonconformance management](enable-quality-management.md)
- [Quality management for warehouse processes](quality-management-for-warehouses-processes.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
