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

Users can manage the invoice fields list and manual review settings for legal entities using **Configuration group**. Users can set up invoice
configurations for different legal entities in groups. Different legal entities in the same configuration group share the same invoice fields and manual review settings. 

## Manage configuration groups 

To manage configuration groups using the app, go to **Setup** and then **System setup > Define configuration groups component**.

On the **Define configuration groups** page: 

The main tab displays the list of the configuration groups that are defined and a default configuration group. 
The following options are available for configuration groups: 

 - Duplicate a configuration group 
Select this option to duplicate an existing confirmation group to create a new configuration group. Once a configuration group is duplicated, select **OK**.
A duplicate configuration group is created with all the fields same as the chosen configuration group except **Group name** and **Group description**. 

 - Delete configuration groups 
You can select a configuration group and select **Delete** to delete a configuration group. The **Default** configuration group can't be deleted. 

 - Edit configuration group ID 
To edit the configuration group ID, click **Group ID** field and update the **Group ID**. The **Group ID** shouldn't contain spaces, special characters and shouldn't 
exceed 20 characters. The **Group ID** field can only be updated once.

 - Edit configuration group description 
To edit the configuration group description, click the **Description** field and update.

 - Change manual review setting 
The user can decide if an invoice needs to be manually reviewed. To change the manual review setting, click **Need manual review** option. 
Select from the following:
**Always manual review**: Select this option if invoices in this configuration group always need manual review. 
**For errors and warnings**: Select this option if invoices that contain an error or warning messages need manual review. 
**For errors**: Select this option to manually review the invoices that contain error messages. 

 - Change confidence score setting 
The **Confidence score** is metadata provided by the Invoice capture solution to report the accuracy of recognized invoice data. The higher the score is, the more accurate the recognized data will potentially be. The configuration lets users define when manual review is needed according to the confidence score. The user can change the confidence score threshold for invoices. To update the confidence score setting, click **Confidence score** field and update.

 - **Warning** alert type: Invoice fields that have confidence scores over the warning threshold are considered correct. The warning threshold must be greater than 
 the error threshold and less than 100. 

 - **Error** alert type: Invoice fields that have confidence scores under the error threshold are considered failed. Error messages will be displayed to 
 inform the user. The error threshold must be greater than zero and less than the warning threshold. The warning messages will be displayed for invoice fields that 
 have confidence scores between the warning threshold and error threshold.

 - Manage invoice fields 
The user can manage the invoice fields list to be displayed in the **Side-by-side Viewer**. Go to the **Invoice field management** tab and click the gear, 
select the invoice fields to be added in the side bar and click **Save** and the selected fields will be added to the list. 
To remove the added invoice field from the list, click **Remove** on the field. 

### Manage file filters (optional) 

Manage file filters allows users to define additional filters to incoming invoice files. Unlike the filters defined in channel where the file won’t be received at all, the filters defined here will display the received files in the **Received files** list, but with file validation errors. Users can review the incoming files and decide if its an invalid invoice and obsolete the file or manually include the file to be recognized and included in captured invoices. 

After the Invoice capture solution installed, a default file filter is defined. The file filter is global wise, if you want to have different filter settings, you can update the default one. 

### Accepted file size 

You may choose the accepted file size. 

>[!NOTE] 
> Files with size over than 20.480KB aren't supported. 

### Accepted file types 

The file types that are currently supported are:  

 - PDF
 - PNG
 - JPG
 - JPEG
 - TIF
 - TIFF 

