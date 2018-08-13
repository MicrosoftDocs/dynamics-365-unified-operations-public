---
# required metadata

title: Generate fiscal documents for a load
description: This topic provides information on how to generate fiscal documents for a load for Brazil.
author: ShylaThompson
manager: AnnBe
ms.date: 6/5/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  
audience: Application User
# ms.devlang: 
ms.reviewer: shylaw
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Brazil
# ms.search.industry: 
ms.author: shylaw
ms.search.validFrom: 2017-12-31
ms.dyn365.ops.version: 7.3

---

# Generate fiscal documents for a load 

You can create a load that contains multiple load lines. Each load line is created for a specific quantity of items from a sales order line. You can create one or more load lines or loads for one or more sales order lines or sales orders.


> [!NOTE]
> This topic applies to features in the <STRONG>Transportation management</STRONG> module. It does not apply to features in the <A href="inventory-management.md">Inventory management</A> module.



You can generate one or more fiscal documents for a load depending on the sales orders that the load is created for. The quantity on a fiscal document line is the load line pick up quantity, instead of the sales order line quantity.

The following table describes an example of how you can create load lines and loads for sales order lines and sales orders, and how fiscal documents are generated for each load.

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Sales order and sales order lines</p></th>
<th><p>Load and load lines</p></th>
<th><p>Fiscal documents</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><ol>
<li><p>Sales order 1 for customer C1 that contains the following sales order lines:</p>
<ol>
<li><p>Sales order line 1.1 that contains 50 units of item A.</p></li>
<li><p>Sales order line 1.2 that contains 20 units of item B.</p></li>
</ol></li>
<li><p>Sales order 2 for customer C2 that contains the following sales order lines:</p>
<ol>
<li><p>Sales order line 2.1 that contains 200 units of item C.</p></li>
<li><p>Sales order line 2.2 that contains 100 units of item D.</p></li>
</ol></li>
</ol></td>
<td><ol>
<li><p>You can create a load 1 that contains the following load lines:</p>
<ol>
<li><p>Load line 1.1 for the sales order line 1.1 that contains 30 units of item A.</p></li>
<li><p>Load line 1.2 for sales order line 1.2 that contains 10 units of item B.</p></li>
<li><p>Load line 1.3 for sales order line 2.1 that contains 100 units of item C.</p></li>
</ol></li>
<li><p>You can create a load 2 that contains the following load lines:</p>
<ol>
<li><p>Load line 2.1 for the sales order line 1.1 that contains the remaining 20 units of item A.</p></li>
<li><p>Load line 2.2 for sales order line 2.1 that contains 50 units of item C.</p></li>
</ol></li>
</ol></td>
<td><ol>
<li><p>The following two fiscal documents are generated for load 1:</p>
<ol>
<li><p>A fiscal document is generated for customer C1 that contains a fiscal document line for 30 units of item A and another for 10 units of item B.</p></li>
<li><p>A fiscal document is generated for customer C2 that contains a fiscal document line for 100 units of item C.</p></li>
</ol></li>
<li><p>The following two fiscal documents are generated for load 2:</p>
<ol>
<li><p>A fiscal document is generated for customer C1 that contains a fiscal document line for 20 units of item A.</p></li>
<li><p>A fiscal document is generated for customer C2 that contains a fiscal document line for 50 units of item C.</p></li>
</ol></li>
</ol></td>
</tr>
</tbody>
</table>


Follow the steps in this topic to generate fiscal documents for a load.

## Prerequisites

The following table shows the prerequisites that must be in place before you start.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Category</p></th>
<th><p>Prerequisite</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Version</strong></p></td>
<td><p>Microsoft Dynamics AX 2012 R3</p></td>
</tr>
<tr class="even">
<td><p><strong>Country/region</strong></p></td>
<td><p>The primary address for the legal entity must be in the following countries/regions: Brazil</p></td>
</tr>
<tr class="odd">
<td><p><strong>Related setup tasks</strong></p></td>
<td><ul>
<li><p>Create a fiscal establishment group and a fiscal establishment. For more information, see <a href="bra-create-a-fiscal-establishment-group.md">(BRA) Create a fiscal establishment group</a> and <a href="bra-create-a-fiscal-establishment.md">(BRA) Create a fiscal establishment</a>.</p></li>
<li><p>Set up a fiscal document type, and then assign it to customers, vendors, or inventory items. For more information, see <a href="bra-set-up-fiscal-document-types.md">(BRA) Set up fiscal document types</a> and <a href="bra-assign-fiscal-document-types-for-customers-or-vendors.md">(BRA) Assign fiscal document types for customers or vendors</a>.</p></li>
<li><p>Set up a transportation management shipping carrier that contains the same vendor as the one that you specified in the <strong>Vendor account</strong> field in the <strong>Carrier</strong> form in the Sales and Marketing module. For more information, see <a href="set-up-shipping-carriers-and-carrier-groups.md">Set up shipping carriers and carrier groups</a> and <a href="https://technet.microsoft.com/en-us/library/jj710592(v=ax.60)">(BRA) Carrier (modified form)</a>.</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p><strong>Related task</strong></p></td>
<td><p>Create an outbound load for a shipment.</p></td>
</tr>
</tbody>
</table>


## Generate fiscal documents for a load

Use the **Loads** form to view the loads, and then select a load that has a confirmed shipment to generate the fiscal documents for. You can then use the **Posting invoice** form to post sales orders and generate fiscal documents for a load.

To perform this task, follow these steps:

1.  Click **Accounts receivable** \> **Periodic** \> **Sales update** \> **Loads**.

2.  In the **Loads** form, select a load that contains a confirmed shipment, and then verify the identification code, status, direction, site, warehouse, and shipment of the load.
    
    <table>
    <colgroup>
    <col style="width: 50%" />
    <col style="width: 50%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th><p>Field</p></th>
    <th><p>Description</p></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p><strong>Load ID</strong></p></td>
    <td><p>The identification code of the shipment.</p></td>
    </tr>
    <tr class="even">
    <td><p><strong>Load status</strong></p></td>
    <td><p>The status of the load. The status can be <strong>Shipped</strong>.</p></td>
    </tr>
    <tr class="odd">
    <td><p><strong>Direction</strong></p></td>
    <td><p>The direction of the load. The direction can be <strong>Outbound</strong>.</p></td>
    </tr>
    <tr class="even">
    <td><p><strong>Site</strong></p></td>
    <td><p>The site from which the load is picked up.</p></td>
    </tr>
    <tr class="odd">
    <td><p><strong>Warehouse</strong></p></td>
    <td><p>The warehouse from which the load is picked up.</p></td>
    </tr>
    <tr class="even">
    <td><p><strong>Shipment ID</strong></p></td>
    <td><p>The identification code of the load shipment.</p></td>
    </tr>
    <tr class="odd">
    <td><p><strong>Scheduled load shipping date and time</strong></p></td>
    <td><p>The scheduled date and time for the load shipment.</p></td>
    </tr>
    </tbody>
    </table>


3.  Click **Invoice** to open the **Posting invoice** form, where you can view the sales order lines for which the load is created. The lines contain only the load line quantities.

4.  Select the **Posting** check box to post the sales orders for the load to generate fiscal documents.

5.  Specify additional details, if required. 

6.  Click **OK** to post the sales orders for the load and generate the fiscal documents.


## Technical information for system administrators

If you don't have access to the pages that are used to complete this task, contact your system administrator and provide the information that is shown in the following table.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Category</p></th>
<th><p>Prerequisite</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Configuration keys</strong></p></td>
<td><p>Click <strong>System administration</strong> &gt; <strong>Setup</strong> &gt; <strong>Licensing</strong> &gt; <strong>License configuration</strong>. Expand the <strong>Trade</strong> license key, and then select the <strong>Warehouse and Transportation management</strong> configuration key.</p></td>
</tr>
<tr class="even">
<td><p><strong>Security roles and duties</strong></p></td>
<td><p>To perform this task, you must be a member of a security role that includes the <strong>Maintain customer invoice transactions</strong> (CustInvoiceCustomerInvoiceTransMaintain) duty.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Security roles and privileges</strong></p></td>
<td><p>To perform this task, you must be a member of a security role that includes the <strong>Loads</strong> (WHSLoadTableInvoicePost_BR) privilege.</p></td>
</tr>
</tbody>
</table>
