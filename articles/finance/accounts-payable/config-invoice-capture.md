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
4. **Configuration group** – The configuration group that will be used if a configuration group isn't set at the legal entity or vendor acount level during invoice processing.
5. **Use continuous learning** – Select this option to turn on the continuous learning feature.

### Manage file filters (optional)

Manage file filters lets admins define additional filters for incoming invoice files. Files that don't meet the filter criteria will be received and appear in the **Received files (Pending)** list with state "Cancelled". Clerks can review them and decide whether to void and obsolete them. This behavior differs from the one defined in the flow behind the channel. In the flow, files that don't meet the criteria won't be received at all. 

After the Invoice capture solution is installed, a default file filter is provided. This file filter is global. If you want to have different filter settings, you can creat a own file filter and update the value in default filter.  


### Definition of master data

Invoice capture processing requires two types of master data: legal entities and vendors.

**Legal entities** are organizations that are registered with legal authorities and defined in Microsoft Dynamics 365 Finance. Business activities are performed and recorded separately for each legal entity. In Microsoft Power Platform, business units, security roles, and users are linked to conform to the role-based security model. This link controls data access through business units and security roles, and allows Accounts payable clerks to view only the invoices that are assigned to their users.

**Vendors** are individuals or organizations that supplies goods or services to a business. In Dynamics 365 Finance, if a vendor provides services or product to multiple legal entities, a vendor account has to be created for each legal entity. Then the business activity can be correctly recored. In Invoice capture, the vendor master data is used to automatically derive the vendor account, which helps increase the touchless rate in invoice processing.


#### Sync legal entities

In the **Manage legal entities** process, users can't manually create legal entities. Instead, you must sync the legal entities by following these steps.

1. Go to **Setup \> System setup \> Manage legal entities**.
2. Select **Sync**.
3. In the confirmation message box, select **OK**.

After synchronization is completed, a message shows the number of new legal entities. The list view is automatically refreshed to show the new legal entities.

#### Sync vendors
 In **Manage vendors**, it provides three options to sync the vendor accounts
 1. Sync all
 It will sync all the vendor accounts and potentially it will cause the performance issue.
 2. Sync by legal entity
 Admin can select one or multiple legal entities and sync all the vendors under select legal entities.
 3. Sync by selection
 Admin can search and select one or mutliple vendor accounts and sync the selected vendor. 
 
An Accounts payable administrator needs manually trigger synchronization. 
>[!NOTE]
>Automatic synchronization is under development that could let the system automatically sync the data in a scheduled time in a recurring way.
