---
# required metadata

title: Generate fiscal documents for a load
description: This topic explains how to generate fiscal documents for a load for Brazil.
author: ShylaThompson
ms.date: 06/05/2018
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form:  
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Brazil
# ms.search.industry: 
ms.author: roschlom
ms.search.validFrom: 2017-12-31
ms.dyn365.ops.version: 7.3

---

# Generate fiscal documents for a load 

[!include [banner](../includes/banner.md)]

You can create a load that has multiple load lines. Each load line is created for a specific quantity of items from a sales order line. You can create one or more load lines or loads for one or more sales order lines or sales orders.

> [!NOTE]
> This topic applies to features in the **Transportation management** module. It doesn't apply to features in the Inventory management  module.

You can generate one or more fiscal documents for a load, depending on the sales orders that the load is created for. The quantity on a fiscal document line is the pick-up quantity for the load line, not the quantity from the sales order line.

The following example shows how you can create load lines and loads for sales order lines and sales orders, and how fiscal documents are generated for each load.

### Sales orders and sales order lines

1. Sales order 1 for customer C1 has the following sales order lines:

    1. Sales order line 1.1, which has 50 units of item A
    2. Sales order line 1.2, which has 20 units of item B

2. Sales order 2 for customer C2 has the following sales order lines:

    1. Sales order line 2.1, which has 200 units of item C
    2. Sales order line 2.2, which has 100 units of item D

### Loads and load lines

1. You create load 1 that has the following load lines:

    1. Load line 1.1 for sales order line 1.1. This load line has 30 units of item A.
    2. Load line 1.2 for sales order line 1.2. This load line has 10 units of item B.
    3. Load line 1.3 for sales order line 2.1. This load line has 100 units of item C.

2. You create load 2 that has the following load lines:

    1. Load line 2.1 for sales order line 1.1. This load line has the remaining 20 units of item A.
    2. Load line 2.2 for sales order line 2.1. This load line has 50 units of item C.

### Fiscal documents

1. The following fiscal documents are generated for load 1:

    1. A fiscal document for customer C1 that has one fiscal document line for 30 units of item A and another line for 10 units of item B
    2. A fiscal document for customer C2 that has a fiscal document line for 100 units of item C

2. The following fiscal documents are generated for load 2:

    1. A fiscal document for customer C1 that has a fiscal document line for 20 units of item A
    2. A fiscal document for customer C2 that has a fiscal document line for 50 units of item C

Follow the steps in this topic to generate fiscal documents for a load.

## Prerequisites

The following table shows the prerequisites that must be in place before you start.

<table>
<thead>
<tr>
<th>Category</th>
<th>Prerequisite</th>
</tr>
</thead>
<tbody>
<tr>
<td>Country/region</td>
<td>The primary address for the legal entity must be in Brazil.</td>
</tr>
<tr>
<td>Related setup tasks</td>
<td>
<ul>
<li>Create a fiscal establishment group and a fiscal establishment. </li>
<li>Set up a fiscal document type, and then assign it to customers, vendors, or inventory items.</li>
<li>Set up a transportation management shipping carrier that has the same vendor that you specified in the <strong>Vendor account</strong> field in the <strong>Carrier</strong> form in the <strong>Sales and Marketing</strong> module.</li>
</ul>
</td>
</tr>
<tr>
<td>Related task</td>
<td>Create an outbound load for a shipment.</td>
</tr>
</tbody>
</table>

## Generate fiscal documents for a load

Use the **Loads** form to view the loads, and then select a load that has a confirmed shipment. You can then use the **Posting invoice** form to post sales orders and generate fiscal documents for that load.

Follow these steps to complete this task.

1. Click **Accounts receivable** \> **Periodic** \> **Sales update** \> **Loads**.
2. In the **Loads** form, select a load that has a confirmed shipment, and verify the identification code, status, direction, site, warehouse, and shipment of the load.

    | Field                                 | Description |
    |---------------------------------------|-------------|
    | Load ID                               | The identification code of the shipment. |
    | Load status                           | The status of the load. The status can be **Shipped**. |
    | Direction                             | The direction of the load. The direction can be **Outbound**. |
    | Site                                  | The site that the load is picked up from. |
    | Warehouse                             | The warehouse that the load is picked up from. |
    | Shipment ID                           | The identification code of the load shipment. |
    | Scheduled load shipping date and time | The scheduled date and time of the load shipment. |

3. Click **Invoice** to open the **Posting invoice** form, where you can view the sales order lines that the load is created for. The lines have only the load line quantities.
4. Select the **Posting** check box to post the sales orders for the load to generate fiscal documents.
5. Specify any additional details that are required. 
6. Click **OK** to post the sales orders for the load and generate the fiscal documents.

## Technical information for system administrators

If you don't have access to the pages that are used to complete this task, contact your system admin, and provide the information in the following table.

| Category                      | Prerequisite |
|-------------------------------|--------------|
| Configuration keys            | Click **System administration** &gt; **Setup** &gt; **Licensing** &gt; **License configuration**. Expand the **Trade** license key, and then select the **Warehouse and Transportation management** configuration key. |
| Security roles and duties     | To perform this task, you must be a member of a security role that includes the **Maintain customer invoice transactions** (CustInvoiceCustomerInvoiceTransMaintain) duty. |
| Security roles and privileges | To perform this task, you must be a member of a security role that includes the **Loads** (WHSLoadTableInvoicePost\_BR) privilege. |


[!INCLUDE[footer-include](../../includes/footer-banner.md)]