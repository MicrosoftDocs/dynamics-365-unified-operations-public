---
# required metadata

title: Invoice capture received files
description: This article explains how to collect invoice files from different sources in Invoice capture.
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

# Invoice capture received files

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

In Invoice capture, the **Received files** page is a central place where invoice files are received from different sources.

In most cases, the process in **Received files** is handled automatically and doesn't require manual intervention. However, when there are exceptions or errors, the Accounts payable clerk needs to ensure that all invoice files have been executed correctly to avoid omissions that could lead to financial losses to the company. 

In **Manage file** filter, the various filter settings on the received invoice files can be applied. If the invoice files violate the filter rules, it won't be processed. The Accounts payable clerk can decide in **Received files** if invoices can be included again when the invoices are valid. 

## View captured invoices

The **Received file (pending)** page displays incoming files that violate filter rules.
 - If the invoices are invalid, the invoice can be marked as **Voided** by clicking **Void**.
 - If the invoices are valid, the invoice can be included in the invoice process by selecting it and clicking **Retry**.
In the **Received file (voided)** page, all files marked as **Voided** are displayed.
 - If you select an invoice and click **Delete**, it will be permanently deleted from Dataverse and can't be recovered.
In the **Received file (captured)** page, all files that have been successfully recognized and are in Dataverse are displayed. 
 - Select an invoice and click **View captured invoice** to view invoices in a side-by-side view where users can review the invoice status and make corrections. 
 - Click **Download** to download the original invoice file.


## Upload invoice files

To upload invoice images:
1. Go to **Manage Invoices > Received file**, click **Upload file**. 
2. Select the files by clicking **+** frame.
3. Drag and drop the files. The selected files will be displayed in the list.
4. Click **Upload** and the files will start uploading immediately.  
 - Once complete, a successful message will be returned, and the uploaded files will be removed from the list.  
5. Close the pane. The **Received file** list will be automatically refreshed. 


## View history 

Accounts payable clerks can select an invoice and click **View history** to view the processing details with description, message type and processing time. 



