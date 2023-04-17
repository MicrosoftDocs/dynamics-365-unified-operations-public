---
# required metadata

title: Configure the Invoice capture solution
description: This article explains how to configure the Invoice capture solution.
author: sunfzam
ms.date: 04/04/2023
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

# Configure the Invoice capture solution

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

After the Invoice capture solution is installed, default configurations for using it are provided. These default configurations might not fully meet the customer's requirements. In Invoice capture, configurations can be found in **System preference**.

## System preference

1. **AI Builder model** – The default model is set to **Invoice processing model**. This is a prebuilt model that can handle the most common invoices with various languages. To update the default model, select one in the drop-down list and additional mapping will be required to map the model fields to the invoice files. 
2. **Channel for file upload** – A default channel is provided for directly uploading the invoice files.
3. **File filter** – Select the file filter to apply additional filtering to incoming files at the application level.
4. **Configuration group** – The configuration group that will be used if a configuration group isn't set at the legal entity or vendor level during invoice processing.
5. **Use continuous learning** – Select this option to turn on the continuous learning feature.

### Manage file filters (optional)

Manage file filters lets users define additional filters for incoming invoice files. Files that don't meet the filter criteria will be received and will appear in the **Received files** list, but they will show file validation errors. This behavior differs from the behavior for filters that are defined in the channel. For those filters, files that don't meet the criteria won't be received at all. Users can review the incoming files and decide whether each file is a non-valid invoice, and they can obsolete the file or manually include it for recognition and inclusion in captured invoices.

When the Invoice capture solution is installed, a default file filter is defined. This file filter is global. If you want different filter settings, you can update the default filter. If a field is mandatory, select **Required**. 


### Definition of master data

Invoice capture supports two data types for vendor invoice processing: legal entities and vendors.

**Legal entities** are organizations that are registered with legal authorities and defined in Microsoft Dynamics 365 Finance. Business activities are performed and recorded separately for each legal entity. In Microsoft Power Platform, business units, security roles, and users are linked to conform to the role-based security model. This link controls data access through business units and security roles, and allows Accounts payable clerks to view only the invoices that are assigned to their users.

**Vendors** are supplier organizations or sole proprietors that supply goods or services to a business, as defined in Dynamics 365 Finance. The vendor master data is used to automatically derive the vendor account. Therefore, it helps increase the touchless rate in invoice processing.

The Invoice capture solution provides a configuration space where you can load basic information from existing legal entities and vendors in Finance. When a supplier invoice arrives, the legal entity and vendor account must be correctly determined before the invoice is transferred to the target system. The use of master data to derive legal entities and vendor accounts can help reduce maintenance of mapping rules.

### Sync master data

The **Manage legal entities** and **Manage vendors** processes work in the same way. In the **Manage legal entities** process, users can't manually create legal entities. Instead, you must sync the legal entities from Finance by following these steps.

1. Go to **Setup \> System setup \> Manage legal entities**.
2. Select **Sync**.
3. In the confirmation message box, select **OK**.

After synchronization is completed, a message shows the number of new legal entities. The list view is automatically refreshed to show the new legal entities.

An Accounts payable administrator will manually trigger synchronization.
