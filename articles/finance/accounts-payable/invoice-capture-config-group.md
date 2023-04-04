---
# required metadata

title: Invoice capture solution configuration groups
description: This article provides general information about configuration groups in the Invoice capture solution.
author: sunfzam
ms.date: 04/4/2023
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

## What is a configuration group

After an invoice is successfully recognized and captured in Dataverse, we need to apply different derivation and mapping logic to determine which vendor the invoice came from and which legal entity it was sent to. Invoices from different vendors have different styles, resolutions, and contexts, and the type of invoice may vary: 
 - A PO invoice associated with purchase orders. 
 - An expense invoice which is unrelated to a purchase order. 

These factors will influence: 
 - Message types in different confidence score thresholds, under what conditions manual intervention is required. 
 - Acceptable types of invoices and fields that need to be displayed based on each type.

## Default configuration group 

After deployment, a **Default configuration** group is created. This **Default configuration** group can't be changed or deleted. 

Administrators can assign different configuration groups on the vendor level, legal entity level and system level. 
After a vendor account and legal entity are determined, the system will check if a configuration group is assigned at the vendor account level. If no configuration group is found, the legal entity will be checked for an assigned configuration group. If there no configuration group assigned at either level, the configuration group specified in **System preference** will be used to display the invoice. 


## Manage configuration groups

To manage configuration groups by using the app, go to **Setup**, and then select **System setup \> Define configuration groups component**.

To create a new configuration group, select the **Copy a configuration group** option. You can create a new configuration group by duplicating an existing group. The new group has the same values as the original group for all the fields except **Group name** and **Group description**. After the configuration group is duplicated, select **OK**.

Configuration groups provides settings for:

### Define confidence score of invoice recognition  

Defines the quality standard for invoice data to be recognized by AI Builder. When the recognition is finished, structured invoice data and the corresponding confidence score for each field on the invoice are sent to AI builder. You can configure the confidence scores to indicate differences in the severity of the detected errors. 

### Define mandatory review needed before invoice creation:  

Determines if a manual review is needed for each recognized invoice based on the severity of the issues (warnings or errors).  

### Supported invoice types 

In Invoice capture, there are different invoice types for incoming invoices. The invoice type determines: 
 - The validation logic to ensure the completeness and correctness of invoices in Invoice capture. 
 - The invoice fields (on Header or lines) to be displayed in the side-by-side viewer. 
 - Together with the setting in Dynamics 365 Finance to decide which data entity API in recipient side will be called (using pending vendor invoice or invoice journal).  
### Supported invoice types
There are three types of invoice types supported in Invoice capture: 
 - PO invoice - invoices that are associated with purchase orders and the purchase order details have to be decided on each invoice line. Both header and lines are required to be reviewed in Invoice capture. 
 - Header-only - invoices are associated with purchase orders. The purchase order is mandatory on the invoice header and has to be correctly assigned. The invoice lines will be automatically created from the purchase order in Dynamics 365 Finance by enabling the **Automatically create invoice lines** feature. After this feature is enable, AP clerks won't need to review the line details in Invoice capture. In addition, the line details won’t be displayed in the side-by-side viewer. 
 - Cost invoice - invoices contain non-stock items which could be either service items or procurement category items. 

If it is clear what the invoice type should be supported for the invoices that are sent from vendors, AP admin can create a configuration group and select the invoice type for the supported invoice type. Then assign the configuration group to the vendor level. This increases the touchless rate of invoice processing in Invoice capture. 

### Define the control of invoice fields 

For each invoice type, admin can define different fields to be displayed by default in the side-by-side view. AP Admin can add or remove the default fields and set a field as mandatory.  

### Security 

AP admin is can access the Manage configuration groups.  

### Manage file filters (optional)

Manage file filters lets users define additional filters for incoming invoice files. Files that don't meet the filter criteria will be received and will appear in the **Received files(Pending)** list. These fields are shown as **Cancelled** and will not be processed by recognitive service unless AP clerks include them manually. 
This behavior differs from the behavior for filters that are defined in the channel. For those filters, files that don't meet the criteria won't be received at all. 

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

#### Supported file names 

AP admin can filter out files that aren't invoices by using file name rules. Different rules can be applied to only accept files when the name contains predefined strings or exclude files that contain the defined strings.
 
#### Security 
AP admin can access the **Manage file filters**.  
