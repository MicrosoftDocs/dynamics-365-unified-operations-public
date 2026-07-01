---
title: Configure fields for the Warehouse Management mobile app
description: Learn how to define and configure names and priorities of fields shown in the Warehouse Management mobile app, with an outline on warehouse app field names. 
author: Mirzaab
ms.author: mirzaab
ms.topic: article
ms.date: 05/20/2026
ms.reviewer: kamaybac
ms.search.form: WHSMobileAppField, WHSMobileAppFieldPriority
ms.assetid: 6cf3d7da-29bb-4d3d-aaf5-544ca9cc2980
---

# Configure fields for the Warehouse Management mobile app

[!include [banner](../includes/banner.md)]

This article describes how to define and configure the names and priorities of fields shown in the Warehouse Management mobile app.

> [!NOTE]
> This article applies to features in Warehouse management. It doesn't apply to features in Inventory management. The Warehouse Management mobile app is an application that you can use to perform warehouse tasks. You can define and configure the input type for the field names that the app uses, as well as configure the priority for the field names. You can't rename mobile app fields. This article explains how to define and configure Warehouse Management mobile app field names and priorities, and how they're used.

## Configure warehouse app field names

When you use Warehousing on your mobile device, you can configure how metadata displays on your device on the **Warehouse app field names** page. In a new company, select **Create default setup** to generate all field names that the warehouse mobile device workflows use. Then, assign a preferred input mode and input type to them. After you generate all field names, select the following input options.

| Option | Description |
| --- | --- |
| Preferred input mode | This option defines whether a scanning field or a manual entry input field should show for the selected field name. This option is useful to distinguish fields depending on if bar codes are used for the field. **Note:** For field names with preferred input mode set to **Scanning**, you can enter information manually if the bar code is unreadable or damaged. |
| Input type | This option defines what input type should be used for the selected field name. Four options are available: **Selection** - Contains a list of options to choose from. Field names with this option aren't editable. **Date** - Field names specified as date show a date format with the label. This format helps warehouse workers see in which format to enter the date. Field names with this option aren't editable. **Alpha** - If selected, the device keyboard is used when entering information manually in the app. The keyboard experience can be changed depending on which device is used. **Numeric** - For field names that use numeric input only, select this option to display a custom numeric keypad with the input field instead of the device keyboard. |

## Configure warehouse app field priority

On the **Warehouse app field priority** page, you can organize field names into different priority groups. This priority system helps you decide what information appears on the main task page when warehouse workers perform tasks using the app. If you select **Create default setup**, a default set of priority groups is generated. You can create as many priority groups as you need, but the task page shows only three priority groups. When the system sends metadata to the app, it assigns each field a relative priority based on its priority group. The app displays the first three priority groups contained in the metadata on the task page. The app displays the rest of the overflowing metadata on a secondary details page. The following table shows an example of five priority groups.

| Priority group | Assigned fields |
| --- | --- |
| Priority 10 | Item, Quantity, Unit of measure |
| Priority 20 | Cluster position, Cluster |
| Priority 30 | Item description |
| Priority 40 | Configuration, Color, Size, Style |
| Priority 50 | Location, License plate |

For example, when a warehouse worker is performing a task on a mobile device, if the metadata that will be displayed in the app consists of the following fields:

- Item
- Quantity
- Unit of measure
- Item description
- Size and Location

Based on the warehouse app field priority set up in the table above, the following three rows of information will be displayed on the task page:

- Row 1: Item, Quantity, Unit of measure
- Row 2: Item description
- Row 3: Size

The remaining metadata, such as Location, doesn't appear on the task page, but it appears on a details page. To learn more and see examples of the user interface, refer to the blog post [Announcing Dynamics 365 Supply Chain Management - Warehousing](https://blogs.msdn.microsoft.com/dynamicsaxscm/2017/01/20/announcing-dynamics-365-for-operations-warehousing/).

## Related information

- [Install the Warehouse Management mobile app](../warehousing/install-configure-warehouse-management-app.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
