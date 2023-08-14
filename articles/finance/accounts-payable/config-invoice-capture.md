---
# required metadata

title: Configure the Invoice capture solution
description: This article explains how to configure the Invoice capture solution.
author: sunfzam
ms.date: 07/19/2023
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
ms.collection: get-started
ms.assetid: 0ec4dbc0-2eeb-423b-8592-4b5d37e559d3
ms.search.region: Global
# ms.search.industry: 
ms.author: zezhangzhao
ms.search.validFrom: 2022-09-28
ms.dyn365.ops.version: 

---

# Configure the Invoice capture solution

[!include [banner](../includes/banner.md)]

After the Invoice capture solution is installed, default configurations for using it are provided. These default configurations might not fully meet the customer's requirements. In Invoice capture, configurations can be found in **System preference**.

## System preference

1. **AI Builder model** – The default model is set to **Invoice processing model**. This prebuilt model can handle the most common invoices in various languages.

    For invoices that have more complex layouts, customers can create their own custom prebuilt models. After a model is published, it appears in the dropdown list, and additional mapping is required to map the model fields to the invoice files. This feature will be supported in a future release.

2. **Channel for file upload** – A default channel is provided for directly uploading the invoice files.
3. **File filter** – Select the file filter to apply additional filtering to incoming files at the application level.
4. **Configuration group** – The configuration group that is used if a configuration group isn't set at the legal entity or vendor account level during invoice processing.
5. **Use continuous learning** – Select this option to turn on the continuous learning feature.
6. **Auto invoice cleanup** - Select this option if you want to enable the daily job to automatically clean up the transferred invoices and voided invoices longer than 180 days.

## Manage file filters (optional)

**Manage file filters** lets administrators define additional filters for incoming invoice files. Files that don't meet the filter criteria are received, but they appear in the **Received files (Pending)** list with a status of **Canceled**. Clerks can review the files and decide whether to void and obsolete them. This behavior differs from the behavior that is defined in the flow behind the channel. In that flow, files that don't meet the criteria aren't received.

After the Invoice capture solution is installed, a default file filter is provided. This file filter is global. If you want a different filter setting, you can create a file filter and update the default filter.

File filters are flexible and can be applied at different channel levels. When an invoice document is received, the channel is checked first for a file filter. If no file filter is assigned to the channel level, the file filter at the system level is used.

### File filter settings

Configure the following settings in the file filter:

1. **Accepted file size** – Define the minimum and maximum accepted file sizes for invoice documents. The maximum file size can't exceed 5 megabytes (MB).
2. **Supported file types** – Select at least one of the following file types that are currently supported for AI Builder recognition service:

    - PDF
    - PNG
    - JPG
    - JPEG
    - TIF
    - TIFF

3. **Supported file names** – Use file name rules to filter out files that aren't relevant to invoices. Different rules can be applied to accept files only when the name contains predefined strings, or to exclude files that contain the defined strings.

## Definition of master data

Invoice capture processing requires two data types: legal entities and vendors.

**Legal entities** are organizations that are registered with legal authorities and defined in Microsoft Dynamics 365 Finance. Business activities are performed and recorded separately for each legal entity. In Microsoft Power Platform, business units, security roles, and users are linked to conform to the role-based security model. This link controls data access through business units and security roles, and allows Accounts payable clerks to view only the invoices that are assigned to their users.

**Vendors** are individuals or organizations that supply goods or services to a business. In Dynamics 365 Finance, if a vendor provides services or product to multiple legal entities, a vendor account has to be created for each legal entity and business activity can be recorded. In Invoice capture, the vendor master data is used to automatically derive the vendor account and helps increase the touchless rate in invoice processing.

### Sync legal entities

In the **Manage legal entities** process, users can't manually create legal entities. Instead, you must sync the legal entities by following these steps.

1. Go to **Setup \> System setup \> Manage legal entities**.
2. Select **Sync**.
3. In the confirmation message box, select **OK**.

After synchronization is completed, a message shows the number of new legal entities. The list view is automatically refreshed to show the new legal entities.

### Sync vendors
 In **Manage vendors**, there are three options to sync the vendor accounts:
 1. **Sync all** - all vendor accounts are synced. This will potentially cause a performance issue.
 2. **Sync by legal entity** - The administrator can select one or multiple legal entities and sync the vendors in the selected legal entities.
 3. **Sync by selection** - Administrators can search and select one or multiple vendors and sync the selected vendor. 
 
An Accounts payable administrator needs manually trigger synchronization. 
>[!NOTE]
>Automatic synchronization is under development that could let the system automatically sync the data in a scheduled time in a recurring way.
