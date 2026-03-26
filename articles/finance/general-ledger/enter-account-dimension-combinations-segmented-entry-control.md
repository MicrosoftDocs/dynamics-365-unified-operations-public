---
title: Enter account and dimension combinations (segmented entry control)
description: Learn how to enter account and dimension combinations or ledger accounts. The entry experience is often referred to as segmented entry control.
author: aprilolson
ms.author: aolson
ms.topic: article
ms.date: 10/24/2022
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.search.form: DimensionConfigureAccountStructure
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: e6fce826-c403-4d91-a78b-e9a58c44ac03
---

# Enter account and dimension combinations (segmented entry control)

[!include [banner](../includes/banner.md)]

This article describes how to enter account and dimension combinations or ledger accounts. The entry experience is often referred to as segmented entry control.

Users enter account and dimension combinations on various pages, such as pages for general journals, budgeting, and posting definitions. The valid account and dimension combinations depend on the account structures that are assigned to the ledger and the advanced rules that are assigned to the account structures. When users enter a combination, they can either manually type the values or take advantage of a rich, lookup experience. When you enter the field, you can start to type and it will search the value and the description. For example, if you type 180 it will search any value that begins with that number combination. Or you may type Cash and it will search any value that has a description that begins with Cash. You can also use a wildcard, such as \*Cash or \*180 to search if the value or description contain the search criteria. 

## When dimensions are validated

The segmented entry control allows you to freely type account and dimension values while you're entering them in the field. The control doesn't block your input as you type, even if the values don't match your account structures or derived dimensions.

Validation happens when you leave the field. When you move to another field, press Tab, or take an action on the page, the system checks what you entered against your account structures and derived dimensions list. If the values aren't valid, you'll receive an error at that point.

This is different from the **Financial dimensions** FastTab, where dimensions that are marked to prevent changes can't be edited at all. In the segmented entry control, you can edit all dimensions, but the system verifies your entries after you move on.

## Keyboard shortcuts

The following table describes the keyboard shortcuts that can be used when the lookup is closed.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Keyboard shortcut</th>
<th>Action</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Alt+Down Arrow</td>
<td>Open the lookup. If you press Alt+Down Arrow a second time, the focus moves to the segments in the flyout.</td>
</tr>
<tr class="even">
<td><ul>
<li>Enter and Shift+Enter</li>
<li>Chart of accounts delimiter</li>
<li>Right Arrow and Left Arrow</li>
</ul></td>
<td>Move to the next or previous segment.</td>
</tr>
<tr class="odd">
<td>Tab</td>
<td>Move to the next field in the grid.</td>
</tr>
</tbody>
</table>

The following table describes the keyboard shortcuts that can be used when the lookup is open.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Keyboard shortcut</th>
<th>Action</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Esc</td>
<td>Close the lookup.</td>
</tr>
<tr class="even">
<td><ul>
<li>Up Arrow and Down Arrow</li>
<li>Page Up and Page Down</li>
<li>Home and End</li>
</ul></td>
<td>Move to the previous or next value in the lists, to the previous or next group of values, or to the first or last element in the lookup.</td>
</tr>
<tr class="odd">
<td><ul>
<li>Chart of accounts delimiter</li>
<li>Right Arrow and Left Arrow</li>
</ul></td>
<td>Move to the next or previous segment.</td>
</tr>
<tr class="even">
<td>Tab</td>
<td>Move to the next field in the grid.</td>
</tr>
<tr class="odd">
<td>Alt+W</td>
<td>Switch between <strong>Show all</strong> and <strong>Show valid</strong>.</td>
</tr>
</tbody>
</table>

## Copy and paste limitations

Copy and paste isn't supported for Account and Offset Account columns in General Journal lines. These columns use segmented entry controls that validate each dimension segment separately, which isn't compatible with standard paste operations. This is a known limitation.

If you need to enter account and dimension values in bulk, use one of the following alternatives:

- **Data Management Framework (DMF)** — Export the General Journal lines from the **Data Management** workspace, make your changes in Excel or another tool, and then import the updated data back. This is the recommended approach for large data entry tasks.
- **Excel add-in** — Open the General Journal, select **Open in Excel**, edit the journal lines directly in the spreadsheet, and publish the changes back to Dynamics 365. For more information, see [Exporting and editing dimensions data in Excel via OData plug-in](/dynamics365/finance/general-ledger/financial-dimension-values-export-excel-odata).




[!INCLUDE[footer-include](../../includes/footer-banner.md)]
