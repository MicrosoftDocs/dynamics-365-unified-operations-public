---
title: Configure fields for the Warehouse Management mobile app
description: Learn how to define and configure names and priorities of fields shown in the Warehouse Management mobile app, with an outline on warehouse app field names. 
author: Mirzaab
ms.author: mirzaab
ms.topic: article
ms.date: 06/20/2017
ms.reviewer: kamaybac
ms.search.form: WHSMobileAppField, WHSMobileAppFieldPriority
ms.assetid: 6cf3d7da-29bb-4d3d-aaf5-544ca9cc2980
---

# Configure fields for the Warehouse Management mobile app

[!include [banner](../includes/banner.md)]

This article describes how to define and configure names and priorities of fields shown in the Warehouse Management mobile app.

> [!NOTE]
> This article applies to features in Warehouse management. It doesn’t apply to features in Inventory management. The Warehouse Management mobile app is an application that you can use to perform warehouse tasks. You can define and configure the field names that are used in the app, as well as configure the priority to which the field names should be assigned. This article explains how to define and configure these Warehouse Management mobile app field names and priorities, and how they are used.

## Configure warehouse app field names

When you use Warehousing on your mobile device, you can configure how metadata should be displayed on your device on the **Warehouse app field names** page. In a new company, select **Create default setup** to generate all field names that will be used in the warehouse mobile device workflows, and then assign a preferred input mode and input type to them. After you have generated all field names, you can select the following input options.

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
<td>This option defines whether a scanning field or a manual entry input field should be shown for the selected field name. This is useful to distinguish fields depending on if bar codes are used for the field. <strong>Note:</strong> For field names with preferred input mode set to <strong>Scanning</strong>, you can enter information manually if the bar code is unreadable or damaged.</td>
</tr>
<tr class="even">
<td>Input type</td>
<td>This option defines what input type should be used for the selected field name. Four options are available:
<ul>
<li><strong>Selection</strong> - Contains a list of options to choose from. Field names with this option aren't editable.</li>
<li><strong>Date</strong> - Field names specified as date will show a date format with the label. This helps warehouse workers see in which format to enter the date. Field names with this option aren't editable.</li>
<li><strong>Alpha</strong> - If selected, the device keyboard will be used when entering information manually in the app. The keyboard experience can be changed depending on which device is used.</li>
<li><strong>Numeric</strong> - For field names that use numeric input only, you can select this option to display a custom numeric keypad with the input field instead of the device keyboard.</li>
</ul></td>
</tr>
</tbody>
</table>

## Configure warehouse app field priority

On the **Warehouse app field priority** page, you can put field names into different priority groups. This makes it possible to decide what information should be displayed on the main task page when warehouse workers perform tasks using the app. If you select **Create default setup**, a default set of priority groups will be generated. It's possible to create as many priority groups as needed, but only three priority groups will be shown on the task page. When the system sends metadata to the app, it will assign each field a relative priority depending on its priority group, and the app will display the first three priority groups contained in the metadata on the task page. The rest of the overflowing metadata will be displayed on a secondary details page. The following table shows an example of five priority groups.

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
<td> Priority 10</td>
<td><ul>
<li>Item</li>
<li>Quantity</li>
<li>Unit of measure</li>
</ul></td>
</tr>
<tr class="even">
<td> Priority 20</td>
<td><ul>
<li>Cluster position</li>
<li>Cluster</li>
</ul></td>
</tr>
<tr class="odd">
<td> Priority 30</td>
<td><ul>
<li>Item description</li>
</ul></td>
</tr>
<tr class="even">
<td> Priority 40</td>
<td><ul>
<li>Configuration</li>
<li>Color</li>
<li>Size</li>
<li>Style</li>
</ul></td>
</tr>
<tr class="odd">
<td> Priority 50</td>
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

Based on the warehouse app field priority set up in the table above, the following three rows of information will be displayed on the task page:

-   Row 1: Item, Quantity, Unit of measure
-   Row 2: Item description
-   Row 3: Size

The remaining metadata, for example, Location, won't be displayed on the task page, but will be displayed on a details page. To learn more and see examples of the user interface, refer to the blog post [Announcing Dynamics 365 Supply Chain Management - Warehousing](https://blogs.msdn.microsoft.com/dynamicsaxscm/2017/01/20/announcing-dynamics-365-for-operations-warehousing/).

## Related information

[Install the Warehouse Management mobile app](../warehousing/install-configure-warehouse-management-app.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
