---
# required metadata

title: Configure app field names in Warehousing app
description: This topic describes how to define and configure warehouse app field names and priorities in Dynamics 365 for Operations. 
author: YuyuScheller
manager: AnnBe
ms.date: 2017-02-07 10 - 09 - 29
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

ms.search.form: WHSMobileAppField, WHSMobileAppFieldPriority
# ROBOTS: 
audience: Application User
# ms.devlang: 
# ms.reviewer: 121
ms.search.scope: Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 269434
ms.assetid: 6cf3d7da-29bb-4d3d-aaf5-544ca9cc2980
ms.search.region: global
ms.search.industry: Manufacturing
ms.author: mafoge
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611

---

# Configure app field names in Warehousing app

This topic describes how to define and configure warehouse app field names and priorities in Dynamics 365 for Operations. 

**Note:** This topic applies to features in Warehouse management. It doesn’t apply to features in Inventory management. Dynamics 365 for Operations - Warehousing is an application that you can use to perform warehouse tasks. You can define and configure the field names that are used in the app, as well as configure the priority to which the field names should be assigned. This topic explains how to define and configure these warehouse app field names and priorities, and how they are used in Dynamics 365 for Operations - Warehousing. For detailed information about how to configure the connection to Dynamics 365 for Operations  - Warehousing, refer to the tutorial [Install and configure Dynamics 365 for Operations - Warehousing](install-configure-warehousing-app.md).

Configure warehouse app field names
===================================

When you use Dynamics 365 for Operations - Warehousing on your mobile device, you can configure how metadata should be displayed on your device on the **Warehouse app field names** page. In a new company in Dynamics 365 for Operations, select **Create default setup** to generate all field names that will be used in the warehouse mobile device workflows, and then assign a preferred input mode and input type to them. After you have generated all field names, you can select the following input options.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Option</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Preferred input mode</td>
<td>This option defines whether a scanning field or a manual entry input field should be shown for the selected field name. This is useful to distinguish fields depending on if barcodes are used for the field. <strong>Note:</strong> For field names with preferred input mode set to <strong>Scanning</strong>, you can enter information manually if the barcode is unreadable or damaged.</td>
</tr>
<tr class="even">
<td>Input type</td>
<td>This option defines what input type should be used for the selected field name. Four options are available:
<ul>
<li><strong>Selection</strong> - Contains a list of options to choose from. Field names with this option are not editable.</li>
<li><strong>Date</strong> - Field names specified as date will show a date format with the label. This helps warehouse workers see in which format to enter the date. Field names with this option are not editable.</li>
<li><strong>Alpha</strong> - If selected, the device keyboard will be used when entering information manually in the app. The keyboard experience can be changed depending on which device is used.</li>
<li><strong>Numeric</strong> - For field names that use numeric input only, you can select this option to display a custom numeric keypad with the input field instead of the device keyboard.</li>
</ul></td>
</tr>
</tbody>
</table>

Configure warehouse app field priority
======================================

On the **Warehouse app field priority** page, you can put field names into different priority groups. This makes it possible to decide what information should be displayed on the main task page when warehouse workers perform tasks using the app. If you click **Create default setup**, a default set of priority groups will be generated. It is possible to create as many priority groups as needed, but only three priority groups will be shown on the task page. When Dynamics 365 for Operations sends metadata to the app, it will assign each field a relative priority depending on its priority group, and the app will display the first three priority groups contained in the metadata on the task page. The rest of the overflowing metadata will be displayed on a secondary details page. The following table shows an example of five priority groups.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Priority group</th>
<th>Assigned fields</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td> Priority 10</td>
<td><ul>
<li>Item</li>
<li>Quantity</li>
<li>Unit of measure</li>
</ul></td>
</tr>
<tr class="even">
<td> Priority 20</td>
<td><ul>
<li>Cluster position</li>
<li>Cluster</li>
</ul></td>
</tr>
<tr class="odd">
<td> Priority 30</td>
<td><ul>
<li>Item description</li>
</ul></td>
</tr>
<tr class="even">
<td> Priority 40</td>
<td><ul>
<li>Configuration</li>
<li>Color</li>
<li>Size</li>
<li>Style</li>
</ul></td>
</tr>
<tr class="odd">
<td> Priority 50</td>
<td><ul>
<li>Location</li>
<li>License plate</li>
</ul></td>
</tr>
</tbody>
</table>

For example, when a warehouse worker is performing a task on a mobile device, if the metadata that will be displayed in the app consists of the following fields:

-   Item
-   Quantity
-   Unit of measure
-   Item description
-   Size and Location

Based on the warehouse app field priority set up in the table above, the following 3 rows of information will be displayed on the task page:

-   Row 1: Item, Quantity, Unit of measure
-   Row 2: Item description
-   Row 3: Size

The remaining metadata, for example, Location, will not be displayed on the task page, but will be displayed on a details page. To learn more and see examples of the user interface, refer to the blog post [Announcing Dynamics 365 for Operations - Warehousing](https://blogs.msdn.microsoft.com/dynamicsaxscm/2017/01/20/announcing-dynamics-365-for-operations-warehousing/).

See also
--------

[Install and configure Microsoft Dynamics 365 for Operations – Warehousing](install-configure-warehousing-app.md)

