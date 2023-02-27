---
# required metadata

title: Invoice capture solution configuration groups
description: This article provides general information about configuration groups in the Invoice capture solution.
author: sunfzam
ms.date: 09/28/2022
ms.topic: overview
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: VendorInvoiceWorkspace, VendInvoiceInfoListPage
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
ms.custom: ["13971", "intro-internal"]
ms.assetid: 0ec4dbc0-2eeb-423b-8592-4b5d37e559d3
ms.search.region: Global
# ms.search.industry: 
ms.author: zezhangzhao
ms.search.validFrom: 2022-09-28
ms.dyn365.ops.version: 

---

# Invoice capture solution configuration groups

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

Users can manage the list of invoice fields and the manual review setting for legal entities by using configuration groups. Users can set up invoice configurations for different legal entities in groups. All the legal entities in the same configuration group use the same invoice fields and manual review setting.

## Manage configuration groups

To manage configuration groups by using the app, go to **Setup**, and then select **System setup \> Define configuration groups component**.

On the **Define configuration groups** page, the main tab shows the list of configuration groups that have been defined. It also shows a default configuration group. For each configuration group, the following actions are available:

- **Copy a configuration group** – You can create a new configuration group by duplicating an existing group. The new group has the same values as the original group for all the fields except **Group name** and **Group description**. After the configuration group is duplicated, select **OK**.
- **Delete configuration groups** – To delete a configuration group, select it, and then select **Delete**.

    > [!NOTE]
    > The default configuration group can't be deleted.

- **Edit a configuration group's ID** – To edit the ID of a configuration group, select the **Group ID** field, and update the value. The group ID should not contain spaces or special characters, and it should not exceed 20 characters.

    > [!NOTE]
    > The value of the **Group ID** field can be updated only once.

- **Edit a configuration group's description** – To edit the description of a configuration group, select the **Description** field, and update the value.
- **Change the manual review setting** – Users can decide whether an invoice must be manually reviewed. To change the manual review setting, select the **Need manual review** option. The following options are available:

    - **Always manual review** – Select this option if invoices in the configuration group always require manual review.
    - **For errors and warnings** – Select this option if invoices that contain error messages or warning messages require manual review.
    - **For errors** – Select this option if invoices that contain error messages require manual review.

- **Change the confidence score setting** – The confidence score is metadata that the Invoice capture solution provides to report the accuracy of recognized invoice data. The higher the score is, the more accurate the recognized data might be. The configuration lets users define when manual review is required, based on the confidence score. Users can change the confidence score threshold for invoices. To update the confidence score setting, select the **Confidence score** field, and update the value.

    There are two alert types for confidence scores:

    - **Warning** – Invoice fields that have confidence scores over the warning threshold are considered correct. The warning threshold must be more than the error threshold and less than 100.
    - **Error** – Invoice fields that have confidence scores under the error threshold are considered failed. Error messages will be shown to the user. The error threshold must be more than 0 (zero) and less than the warning threshold. Warning messages will be shown for invoice fields that have confidence scores between the warning threshold and the error threshold.

- **Manage invoice fields** – Users can manage the list of invoice fields that is shown in the side-by-side viewer. On the **Invoice field management** tab, select the gear symbol, select the invoice fields to add, and then select **Save**. The selected fields will be added to the list. To remove an invoice field from the list, select **Remove** on the field.

### Manage file filters (optional)

Manage file filters lets users define additional filters for incoming invoice files. Files that don't meet the filter criteria will be received and will appear in the **Received files** list, but they will show file validation errors. This behavior differs from the behavior for filters that are defined in the channel. For those filters, files that don't meet the criteria won't be received at all. Users can review the incoming files and decide whether each file is a non-valid invoice, and they can obsolete the file or manually include it for recognition and inclusion in captured invoices.

When the Invoice capture solution is installed, a default file filter is defined. This file filter is global. If you want different filter settings, you can update the default filter. If a field is mandatory, select **Required**. 

### Accepted file size

You can choose the accepted file size.

> [!NOTE]
> Files that are larger than 20,480 kilobytes (KB) aren't supported.

### Supported file types

The following file types are currently supported:

- PDF
- PNG
- JPG
- JPEG
- TIF
- TIFF
